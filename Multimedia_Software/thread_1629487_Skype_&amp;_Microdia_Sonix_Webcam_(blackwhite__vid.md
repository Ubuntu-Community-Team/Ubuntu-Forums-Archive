---
title: "Skype &amp; Microdia Sonix Webcam (black/white  video)"
date: 2010-11-23
forum: Multimedia Software
---

### Post by megadave on 2010-11-23
Hi,

Just installed 64 bit 10.10 on my HP Pavillion laptop and am having trouble with video in skype.  It's grainy, very dark, and in black and white (just like when I didn't have the drivers installed in Windows Vista).

**My built in webcam:** Bus 002 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

**Skype:**  2.1.0.81 (newest I could find on their website)

**guvcview** works fine, shows video in colour.

I tried suggestions from the skype forums
```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
``` and still no love.

Any suggestions?

Thanks.:popcorn:

---

### Post by xc3RnbFO8P on 2010-11-24
Try:
> gedit ~/.profile
add these lines:
> export GTK_MODULES=rgba
export GTK_RGBA_APPS="allbut:skype"
and restart the computer

---

### Post by megadave on 2010-11-27
Hi,

Tried that.  No change.

Error msg 

```

Gtk-Message: Failed to load module "rgba": librgba.so: cannot open shared object file: No such file or directory

```

when I re-edit .profile

---

### Post by Delinquentme on 2011-01-23
how about to add the video to google chat?

---

### Post by Stemp on 2011-01-26
```
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so skype
```

---

### Post by tg3793 on 2011-03-27
I also have a Microdia web cam and the video is quite dark. From the research that I've done I suspect a driver issue but haven't found out if there is a specific driver for the Microdia web cam or if there is a way to alter the video from the generic Linux driver to brighten things up.

Just about half hour into my research so note ready to put the white flag up yet. I'll give it another hour or so of research before I start really begging for expertise from the masters :-)

---

### Post by no2498 on 2011-03-28
try this 


v4l2ucp Version 2.0.2

This application is a port of an original v4l2ucp to Qt4 library,
v4l2ucp is a universal control panel for all V4L2 devices. The
controls come directly from the driver. If they cause problems
with your hardware, please contact the maintainer of the driver.

Copyright (C) 2005 Scott J. Bertin
Copyright (C) 2009-2010 Vasily Khoruzhick

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program; if not, write to the Free Software
Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA

---

### Post by tg3793 on 2011-03-28
Thanks for the tip. Might be useful for me at some later date or might be useful for someone else. I tried another web cam (which works great) and I suspect my Microdia might just be bad ... I'll try the Microdia on a different computer when I get access to one.

Again thanks.

---

