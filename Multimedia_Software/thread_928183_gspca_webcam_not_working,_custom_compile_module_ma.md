---
title: "gspca webcam not working, custom compile module made it worse (howto revert?)"
date: 2008-09-23
forum: Multimedia Software
---

### Post by LTSmash on 2008-09-23
Hi,

I just setup and AMD64 ubuntu system, and I have a pixart webcam which is actually supported by this kernel module, however, when I tried to access it, it wouldn't work, since it always threw an input/output error.

```

ferreteria@ferreteria-desktop:~$ spcagui 
SpcaGui version: 0.3.5 date: 18 September 2005
video device /dev/video0
ERROR opening V4L interface 
: No such file or directory
ferreteria@ferreteria-desktop:~$

```

No program detected the cam, just flash player (this is curious, because as it's running on a AMD64 system and obviously flash is a 32 bit app, it was something unespected).

So I decided to install this module manually: [http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20071224.tar.gz)

I followed the instructions and it compiled succesfully, but now not even flash will recognize the webcam (it did show it up before this as a Pixart Webcam)... the module is currently running, so I don't have any ideas on what might be wrong... oh, and I have to say it, the cam did work on flash, it showed realtime video...

What should i do to fix this? Is there any way to go back to the stock Ubuntu kernel?

Thanks in advance.

---

