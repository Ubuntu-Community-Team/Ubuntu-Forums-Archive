---
title: "Skype &amp; Eyetoy Video"
date: 2010-05-15
forum: Multimedia Software
---

### Post by h1123 on 2010-05-15
Hello,

I have been trying to get my Eyetoy Silver camera to work with my desktop, running ubuntu, but cant seem to understand how to do it. At the momement i have tried everything in the other threads, none of which seem to work, and the links to drivers all seem to be dead. When I do run it with skype all the other person see's is a white box. However the camera does work, so the issue should not be with it. When plugged in both the red and blue light are on..

---

### Post by owners4life5 on 2010-07-20
i unfortunately have the same problem

---

### Post by digitalcitizenx on 2010-07-20
You need to look here:

[http://ubuntuforums.org/showthread.php?t=272328](http://ubuntuforums.org/showthread.php?t=272328)

found with a very simply search of the ubuntu forums

---

### Post by towheedm on 2010-07-20
> **h1123 said:**
> Hello,

I have been trying to get my Eyetoy Silver camera to work with my desktop, running ubuntu, but cant seem to understand how to do it. At the momement i have tried everything in the other threads, none of which seem to work, and the links to drivers all seem to be dead. When I do run it with skype all the other person see's is a white box. However the camera does work, so the issue should not be with it. When plugged in both the red and blue light are on..

If your Eyetoy is working with Cheese then try this:

Rename the skype binary file:

```
sudo mv /usr/bin/skype /usr/bin/skype.real
```Create a new file named skype:

```
gksudo gedit /usr/bin/skype
```Paste the following two lines into it:

```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so XLIB_SKIP_ARGB_VISUALS=1 skype.real 
```Save the file and close gedit.  Now make it executable:

```
sudo chmod +x /usr/bin/skype
```I had the same problem with the cam working with cheese etc, but no video in the skype test.  The above worked for me.

Don't worry about the whole ov519 drivers...it does not compile in Karmic or Lucid.

Hope it helps you to.

---

