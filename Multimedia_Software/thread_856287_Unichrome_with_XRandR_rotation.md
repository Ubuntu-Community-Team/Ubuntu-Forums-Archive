---
title: "Unichrome with XRandR rotation"
date: 2008-07-11
forum: Multimedia Software
---

### Post by foxten on 2008-07-11
Hi there,

I have a Via Unichrome Pro and want to use XRandR to rotate my screen (my monitor can rotate too), but it can't do the rotation.
Is there a support from Unichrome drivers to XRandR rotation?

Actually i'm using Feisty.

Another way to rotate my screen is adding option "Rotate" to xorg.conf, as my driver supports it, but then I need to restart X everytime I want to rotate again.
If my drivers doesn't have support for XRandR rotation, there is a way to change this "Rotate" option for X without restarting it?

Thanks.

---

### Post by Jack the R on 2008-07-15
foxten, I've been going through a [wacom](http://sourceforge.net/tracker/index.php?func=detail&aid=1593330&group_id=69596&atid=525127) driver patch thread on Sourceforge, to support usb tablet pc's, and there was some discussion about how to handle screen rotation.

Since it's a long thread I pulled all the comments out and saved them in a seperate document - 

[Link](http://www.extinctionlevelevent.com/misc/linux/rotate tablet PC screen.odt)

I will look at it closer tomorrow but I could use a little help myself.  Especially since I want to flip the screen 180 not rotate 90.

---

