# great

Another task runner with js

## great vs gulp vs grunt

Great compared to major Task Runners (or Build Systems)

&nbsp; | great | gulp | grunt
:-: | :-: | :-: | :-:
Orienting | Data | File | File
Stream | Yes | Yes | No
Speed | Fast | Fast | Slow
Flow | Clear | Clear | Mess
Easy | Yes | No | No

## great vs nodeunit vs mocha

Great compared to major Test Frameworks

&nbsp; | great | nodeunit | mocha
:-: | :-: | :-: | :-:
Polluting | No | No | Yes
Nested | Good | Bad | Good
Event driven | Yes | No | No
Test only | No | Yes | Yes

## Quick Look

```js
// general configuration
great.on('good', function(){
  log('----- something special -----');
});
great.unit.on('title', function (title) {
  this.title = title;
  log(this.getLevel(), 'titled: ' + title);
});
great.unit.on('end', function () {
  log(this.getLevel(), 'ended: ' + this.title);
});

// run units
great.run(function () {
  this.emit('title', 'main');

  this.add(function () {
    this.emit('title', 'series');

    // series tasks
    this.add(createBody('a-1'));
    this.add(createBody('a-2'));
    this.add(createBody('a-3'));

    great.emit('good');
  });

  this.add(function () {
    this.emit('title', 'mix');

    // parallel tasks
    this.add([
      createAsyncBody('b-1'),
      createAsyncBody('b-2'),
      createAsyncBody('b-3'),
      createAsyncBody('b-4'),
      createAsyncBody('b-5'),
      createAsyncBody('b-6')
    ]);

    this.add(createBody('c-1'));
    this.add(createBody('c-2'));
  });
});
```

See: [example/run.js](example/run.js)
