---
title: "XMMS doesn't start"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by Jonathan Métillon on 2006-11-27
Package: xmms
Version: 1.2.10+cvs20060429-1ubuntu2

xmms doesn't start up. on the console I get:

```
 $ xmms
Message: device: default
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2489 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2490 error_code 8 request_code 72 minor_code 0
```Notice that it use to work, and in between I deactivated DRI/XGL in xorg.conf. Maybe it has an incidence.

---

### Post by karderio on 2006-11-27
I have a very similar problem. When I try to run xmms, I get 100% load on my first processor, and this :

```
$ xmms
Message: device: hw:0,0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 2454 error_code 8 request_code 72 minor_code 0
```

I have had this problem since I upgraded from Dapper to Edgy. I checked the xmms bugzilla.

I tried removing all plugins for xmms, and re-installing it completely.

This thread suggests using "next generation" players instead (this is not the solution I am looking for :) ) :
[http://www.ubuntuforums.org/showthread.php?t=307118&highlight=xmms](http://www.ubuntuforums.org/showthread.php?t=307118&highlight=xmms)

Love, Karderio.

---

### Post by Jonathan Métillon on 2006-11-28
I do. I would like to use Totem. But... I have an [issue with track info update]("http://ubuntuforums.org/showthread.php?t=307886").

---

