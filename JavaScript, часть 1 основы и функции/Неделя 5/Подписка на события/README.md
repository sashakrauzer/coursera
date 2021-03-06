В этом задании необходимо реализовать библиотеку, позволяющую подписываться на события и получать по ним уведомления.

В библиотеке нужно реализовать три метода:

-   **on** _—_  подписка на событие;
-   **off** _—_  отписка от события;
-   **emit** _—_  оповещение всех подписчиков.

        var emitter = require('./index.js');

        var notifications = {
            counter: 0,
            count: function() {
            this.counter++;
            }
        }

        emitter.on('new_notification', notifications, notifications.count);

        emitter.emit('new_notification');

        console.log(notifications.counter);

## Условия

-   Все функции будут вызываться корректно, дополнительных проверок не требуется.
-   Все функции должны возвращать объект, от которого вызваны (emitter), чтобы их можно было вызывать в цепочке (chaining):

	emitter
	  .on(...)
	  .off(...)
	  .emit(...)
	  .on(...);

### Метод 'on'

Подписывает на событие. На любое событие подписчик может подписаться неограниченное количество раз.

	emitter.on(eventName, subscriber, handler);

-   eventName  _—_  название события, на которое подписываемся.
-   subscriber  _—_  объект-подписчик.
-   handler  _—_  функция-обработчик.

### Метод 'off'

Отписывает от события подписчика. После отписки, при возникновении данного события, никаких обработчиков, связанных с этим подписчиком, не должно быть вызвано. Есть возможность повторно подписаться и снова получать события.

	emitter.off(eventName, subscriber);

-   eventName  _—_  название события, от которого отписываемся.
-   subscriber  _—_  объект-подписчик.

### Метод 'emit'

Оповещение всех подписчиков (не отписавшихся). Вызывает все функции-обработчики в порядке подписки.

	emitter.emit(eventName);

-   eventName  _—_  название события, о котором оповещаем подписчиков.