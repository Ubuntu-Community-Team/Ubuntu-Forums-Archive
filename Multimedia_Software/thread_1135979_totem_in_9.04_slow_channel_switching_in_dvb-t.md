---
title: "totem in 9.04: slow channel switching in dvb-t"
date: 2009-04-24
forum: Multimedia Software
---

### Post by nab on 2009-04-24
Hi all,

I'm using totem-gstreamer to connect to my dvb-t usb stick.
Everything is working fine. 
Just the channel switching takes very long (about 20 sec) compared with kaffeine in 8.04 (about 3sec)

Starting totem in a console I get following output:
> totem
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
** Message: don't know how to handle private/teletext

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
** Message: don't know how to handle private/teletext

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()
** Message: don't know how to handle private/teletext

(totem:10783): Pango-WARNING **: Invalid UTF-8 string passed to pango_layout_set_text()



Any suggestions are appreciated!
Nikolaus

---

### Post by nab on 2009-04-25
Doing some search I found about the deprecation warning with python:

[https://bugs.launchpad.net/ubuntu/+source/python-gdata/+bug/336706]("https://bugs.launchpad.net/ubuntu/+source/python-gdata/+bug/336706")

So unlikely to be the cause of the slow switching.

---

### Post by nab on 2009-04-25
The pango-warning I eliminated with removing all special characters out of channels.conf and channels.ps

(I followed [http://wiki.ubuntuusers.de/Totem]("http://wiki.ubuntuusers.de/Totem") to set totem up, but I had to use the ugly codecs to get sound working)

Now I only see:
** Message: don't know how to handle private/teletext

---

