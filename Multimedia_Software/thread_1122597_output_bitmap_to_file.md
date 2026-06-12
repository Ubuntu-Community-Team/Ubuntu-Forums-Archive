---
title: "output bitmap to file"
date: 2009-04-11
forum: Multimedia Software
---

### Post by djbushido on 2009-04-11
I was coding python and was using the PIL (Python Image Library) and had some problems. I created a bitmap using wx.BitmapFromBuffer, but Image.open failed with this error: ```
Traceback (most recent call last):
  File "renderDialog.pyw", line 88, in beginRender
    img = Image.open(wx.BitmapFromBuffer(320,240,rendering.render('snowflake.flam3', [320,240], 200)))
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 1893, in open
    prefix = fp.read(16)
AttributeError: 'Bitmap' object has no attribute 'read'

```
I also tried ```
image = wx.BitmapFromBuffer(<stuff>)
f.write(image)
f.close()
```
But that didn't work either. ```
Traceback (most recent call last):
  File "renderDialog.pyw", line 90, in beginRender
    f.write(image)
TypeError: argument 1 must be string or read-only buffer, not Bitmap

```
Any ideas?

---

### Post by djbushido on 2009-04-11
Found a hack in another book:
```
f.write('%s' % image)
``` if that helps anyone.
NOTE: there is no Header, but this will output the bitmap.

---

