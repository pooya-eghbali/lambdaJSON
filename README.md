===========
lambdaJSON
===========
Serialize python standard types (tuple, complex, bytes, dict with number keys, byte keys or tuple keys, and etc) with json.
lambdaJSON lets you serialize python standard library objects with json.
Typical usage::

    #!/usr/bin/env python

    >>> import lambdaJSON
    >>> myComplexData = {True: (3-5j), (3+5j): b'json', (1, 2, 3): {b'lambda': [1, 2, 3, (3, 4, 5)]}}
    >>> mySerializedData = lambdaJSON.serialize(myComplexData)
    >>> myComplexData  == lambdaJSON.deserialize(mySerializedData)
    True

    >>> 

To pass args and kwargs to the encoder/decoder simply pass them to the serialize/deserialize function, example for json::

    >>> mySerializedData = lambdaJSON.serialize(myComplexData, sort_keys = True)
    >>> myComplexData  == lambdaJSON.deserialize(mySerializedData, object_hook = my_hook)

It can be done for ujson too. You can also serialize python functions::

    >>> import lambdaJSON
    >>> def f(): print('lambdaJSON Rocks!')
    
    >>> mySerializedFunction = lambdaJSON.serialize(f)
    >>> myNewFunction  = lambdaJSON.deserialize(mySerializedFunction)
    >>> myNewFunction()
    'lambdaJSON Rocks!'
    >>>

Added in version 0.2.2, you can pass the list of globals for function deserialization, see the example below::

    >>> import lambdaJSON
    >>> y = 10
    >>> def f(x): return x*y
    
    >>> mySerializedFunction = lambdaJSON.serialize(f)
    >>> myNewFunction  = lambdaJSON.deserialize(mySerializedFunction, globs = {'y':11})
    >>> myNewFunction(5)
    55
    >>>

I'm working on a way to pass real references to the global variables, not just a static value, any suggestions are welcome.

Currently Supported Types
=========================

This types are covered in this version:

1. Functions
2. Bytes
3. Tuples
4. Complex
5. Dicts (With Number, Tuple, String, Bool and Byte keys)
6. other json supported types

Changes from previous
=====================

Ability to pass globals to deserialized Functions.

Download
========

Download package from here: https://pypi.python.org/pypi/lambdaJSON

Project Info
============

Github project page: https://github.com/pooya-eghbali/lambdaJSON
PyPi: https://pypi.python.org/pypi/lambdaJSON
Mail me at: persian.writer [at] Gmail.com


[![Bitdeli Badge](https://d2weczhvl823v0.cloudfront.net/pooya-eghbali/lambdajson/trend.png)](https://bitdeli.com/free "Bitdeli Badge")

