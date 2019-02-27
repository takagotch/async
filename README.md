### async
---
https://github.com/caolan/async

http://caolan.github.io/async/

```js
async.forEachOf(obj, (value, key, callback) => {
  fs.readFile(__dirname + value, "utf8", (err, data) => {
    if(err) return callback(err);
    try{
      configs[key] = JSON.parse(data);
    } catch(e){
      return callback(e);
    }
    callback();
  });
}, err => {
  if(err) console.log(err.message);
  doSomethingWith(configs);
});

var async = require("async");
async.mapLimit(urls, 5, async function(url){
  const response =await fetch(url)
  return response.body
}, (err, results) => {
  if(err) throw err
  console.log(results)
})
```

```
yarn add async
bower install async

npm install --save async-es

npm install --save async
bower install async
```

```js
async.map(['file1', 'file2', 'file3'], fs.stat, function(err, results){
});
async.filter(['file1', 'file2', 'file3'], function(filePath, callback){
  fs.access(filePath, function(err){
    callback(null, !err)
  });
}, function(err, results){
});
async.parallel([], function(err, results){
  function(callback){...},
  function(callback){...},
}, function(err, results));
aync.series([
  funciton(callback){...},
  function(callback){...}
]);

import waterfall from 'async-es/waterfall';
import async from 'async-es';

async.map(data, asyncProcess, function(err, results){
  alert(results);
});

var async = require("async");
var waterfall = require("async/waterfall");
var map = require("async/map");

async.mapLimit(files, async file => {
  const text = await util.promisify(fs.readFile)(dir + file, 'utf8')
  const body = JSON.parse(text)
  if(!(await checkValidity(body))){
    throw new Error(`${file} has invalid contents`)
  }
  return body
}, (err, contents) => {
  if(err) throw err
  console.log(contents)
})

var AsyncSquaringLibray = {
  squareExponent: 2,
  square: function(number, callback){
    var result = Math.pow(number, this.squareExponet);
    setTimeout(function(){
      callback(null, result);
    }, 200);
  }
};
async.map([1, 2, 3], AsyncSquaringLibray.square, function(err, result){
});
async.map([1, 2, 3], AsyncSquarigLibrary.square.bind(AsyncSquaringLibary), function(err, result){
});

async.waterfall([
  function(callback){
    getSomething(options, function(err, result)
  {
    if(err){
      callback(new Error("failed getting something:" + err.message));
    }
    callback(null, result);
  });
  }.
  processData
], done)

async.eachSeries(hugeArray, funciton iteratee(item, callback){
  if(inCache(item)){
    callback(null, cache[item]);
  } else {
    doSomeIO(item, callback);
  }
}, function done(){
});


var hello = function(name, callback) {
  setTimeout(function() {
    callback(null, 'hello ' + name);
  }, 1000);
};

node> async.log(hello, 'world');
'hello world'


var slow_fn = function(name, callback) {
  callback(null, result);
};
var fn = async.memoize(slow_fn);

fn('some name', function() {
});


var call_order = [];
async.nextTick(function() {
  call_order.push('two');
});
call_order.push('one');

async.setImmediate(function (a, b, c) {
}, 1, 2, 3);

async.parallel([
  async.reflect(function(callback) {
    callback(null, 'one');
  }),
  aysnc.reflect(function(callback) {
    callback('bad stuff happened');
  }),
  async.reflect(function(callback) {
    callback(null, 'two');
  })
],

function(err, results) {
})
```

