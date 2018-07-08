
# Bytes to Int & more Python tips and tricks

### Useful Python 3 Idioms

You can reverse a list by using `[::-1]`:

```python
a = [1, 2, 3, 4, 5]
print(a[::-1]) # [5, 4, 3, 2, 1]
```

Also works on both strings and bytes:

```python
s = 'hello world'
print(s[::-1]) # 'dlrow olleh'
b = b'hello world'
print(b[::-1]) # b'dlrow olleh'
```

Indexing bytes will get you the numerical value:

```python
print(b'&'[0]) # 38 since & charcter #38
```

You can do the reverse by using bytes:

```python
print(bytes([38])) # b'&'
```

### Try it


```python
a = [1, 2, 3, 4, 5]
print(a[::-1]) # [5, 4, 3, 2, 1]

s = 'hello world'
print(s[::-1]) # 'dlrow olleh'
b = b'hello world'
print(b[::-1]) # b'dlrow olleh'

print(b'&'[0]) # 38 since & charcter #38

print(bytes([38])) # b'&'
```

### Python Tricks

Here is how we convert binary to/from hex:


```python
print(b'hello world'.hex())
print(bytes.fromhex('68656c6c6f20776f726c64'))
```

### Try it

Reverse this hex dump: `b010a49c82b4bc84cc1dfd6e09b2b8114d016041efaf591eca88959e327dd29a`

Hint: you'll want to turn this into binary data, reverse and turn it into hex again


```python
h = 'b010a49c82b4bc84cc1dfd6e09b2b8114d016041efaf591eca88959e327dd29a'

# convert to binary (bytes.fromhex)
# reverse ([::-1])
# convert to hex()
```

## Converting from bytes to int and back

Converting from bytes to integer requires learning about Big and Little Endian encoding. Essentially any number greater than 255 can be encoded in two ways, with the "Big End" going first or the "Little End" going first.

Normal human reading is from the "Big End". For example 123 is read as 100 + 20 + 3. Some computer systems encode integers with the "Little End" first.

A number like 500 is encoded this way in Big Endian:

0x01f4 (256 + 244)

But this way in Little Endian:

0xf401 (244 + 256)

In Python we can convert an integer to big or little endian using a built-in method:

```python
n = 1234567890
big_endian = n.to_bytes(4, 'big')  # b'\x49\x96\x02\xd2'
little_endian = n.to_bytes(4, 'little')  # b'\xd2\x02\x96\x49'
```

We can also convert from bytes to an integer this way:

```python
big_endian = b'\x49\x96\x02\xd2'
n = int.from_bytes(big_endian, 'big')  # 1234567890
little_endian = b'\xd2\x02\x96\x49'
n = int.from_bytes(little_endian, 'little')  # 1234567890
```


```python
n = 1234567890
big_endian = n.to_bytes(4, 'big')
little_endian = n.to_bytes(4, 'little')

print(big_endian.hex())
print(little_endian.hex())

print(int.from_bytes(big_endian, 'big'))
print(int.from_bytes(little_endian, 'little'))
```

### Try it

Convert the following:

 * 8675309 to 8 bytes in big endian
 * interpret ```b'\x11\x22\x33\x44\x55'``` as a little endian integer


```python
n = 8675309
# print n in 8 big endian bytes

little_endian = b'\x11\x22\x33\x44\x55'
# print little endian in decimal
```

### Test Driven Exercise

Add `little_endian_to_int()` and `int_to_little_endian()` methods to your library.


```python
def little_endian_to_int(b):
    '''little_endian_to_int takes byte sequence as a little-endian number.
    Returns an integer'''
    # use the from_bytes method of int
    pass

def int_to_little_endian(n, length):
    '''endian_to_little_endian takes an integer and returns the little-endian
    byte sequence of length'''
    # use the to_bytes method of n
    pass
```
