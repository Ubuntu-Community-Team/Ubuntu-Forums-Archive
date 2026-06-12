---
title: "Gigaware 25-157 Webcam in 8.04"
date: 2008-06-13
forum: Multimedia Software
---

### Post by chiefchief on 2008-06-13
I just got finished with a fresh install of Ubuntu 8.04, and my webcam does not work.

lsusb returns ```
 046d:c00c Logitech, Inc. Optical Wheel Mouse
```

camorama returns ```
Could not connect to video device (/dev/video0)
```

The camera is connected, and it's green power light is always on.  Also, there is no Video0 in my dev directory.

Any ideas?

---

### Post by herteljt on 2008-06-19
I'm not sure if this will help, but I was looking at compatibility of Gigaware and I stumbled across this entry.  The author describes how to get a gigaware 25-297 to work.


> **goobster71 said:**
> I was able to make mine work with Ubuntu.  I wrote up some instructions here:

[http://lesvanbrunt.blogspot.com/2008/05/making-gigaware-25-297-webcam-work-with.html]("http://lesvanbrunt.blogspot.com/2008/05/making-gigaware-25-297-webcam-work-with.html")

---

### Post by Alfred_McGee on 2009-05-22
The link posted above is for Ubuntu 7.10. It did NOT work for me- it only generated a bunch of error messages when I tried to install the patch provided.

EDIT: Google "gspca" (the driver for the 25-157 webcam) along with "9.04," or whatever your Ubuntu version, and you should get some more up-to-date results than the link above.

For Jaunty users, there is a link that shows how to get this webcam to work by building your own kernel. Doing so can mess up a lot of other things on your system. I'm not gonna do it, but here it is: [http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/](http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/)

---

