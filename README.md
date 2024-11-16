domevents-util
==============

Usage
-----

Register event listeners.

```html
<input type="text" data-oninput="foo">
<button data-onclick="bar"> Do something </button>
```

```js
let eventsMap = {
    onclick: {
        'foo': () => foo(),
    },
    oninput: {
        'bar': () => bar(),
    },
};

DOMEvents.Listen(eventsMap);
```

Refer to these common event types. For custom events, see customization.

```
const commonEventTypes = {
    onclick: 'click',
    ondblclick: 'dblclick',
    onmousedown: 'mousedown',
    onmouseup: 'mouseup',
    onmousemove: 'mousemove',
    onmouseover: 'mouseover',
    onmouseout: 'mouseout',   
    ontouchstart: 'touchstart',
  
    onkeypress: 'keypress',
    onkeydown: 'keydown',
    onkeyup: 'keyup',
    onfocus: 'focus',
    onblur: 'blur',
    
    oninput: 'input',
    onchange: 'change',
    onsubmit: 'submit',
    onreset: 'reset'
};
```

Customization
-------------

### Within Specific Container

```js
DOMEvents.Listen(eventsMap, containerElement);
```

### Event Group

```html
<button data-uiSearch-onclick="foo"> Do something </button> 
```

```js
let eventsMap = {
    key: 'uiSearch',
    onclick: {
        'foo': () => uiSearch.foo(),
    },
};

DOMEvents.Listen(eventsMap);
```

### Custom Event

```html
<div class="_container" data-onmyevent="foo"> A container </div> 
```

```js
let $ = document.querySelector.bind(document);
let eventsMap = {
    onmyevent: {
        eventType: 'MyEvent',
        'foo': () => foo(),
    },
};

DOMEvents.Listen(eventsMap);
$('._container').dispatchEvent(new Event('MyEvent'));
```