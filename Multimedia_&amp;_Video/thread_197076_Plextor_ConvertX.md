---
title: "Plextor ConvertX"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by mikeymckay on 2006-06-15
I have a fresh install of Dapper and a new Plextor ConvertX USB video capture device. I want to use it with MythTV.

So I downloaded the Linux driver from here and tried to build it:
[http://oss.wischip.com/](http://oss.wischip.com/)

I had to install:
fxload
linux-headers-386
libncurses5-dev
(and probably some other stuff that I am forgetting)

Then make succeeded, so I did make install. This failed due to various hotplug directories (/etc/hotplug/usb) not existing. So I created them. Make install then worked, but the magic hardware device driver linkage didn't: I tried the gorecord sample application and it said:
Unable to read /sys/bus/usb/drivers/go7007: No such file or directory
Is the go7007-usb kernel module loaded?

After some more googling I determined that Dapper doesn't use hotplug, but something called udev. One Ubuntu forum post said the answer to my problem was [here]("https://lists.ubuntu.com/archives/ubuntu-devel-announce/2005-December/000028.html").

Which says I need to rewrite the hotplug scripts or something, which is outside of my comfort zone. So I am stuck there.

Any suggestions?

Mike

---

### Post by mikeymckay on 2006-06-16
Aha - solved it!

There appears to be a bug in the driver install code. It is supposed to detect udev, but it doesn't. Explicitly specifying it on the command line fixes it:

sudo make install USE_UDEV=y

Thanks to Byron Polland. See this thread for more info: 
Byron Poland has just replied to a thread you have subscribed to entitled - hotplug changes in Dapper? - in the Ubuntu Users Mailing List Thread forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=183412&goto=newpost](http://ubuntuforums.org/showthread.php?t=183412&goto=newpost)

---

### Post by ceros on 2006-08-21
What ConvertX device are you using?

---

### Post by tomdkat on 2006-09-27
I'm interested in knowing which device you're using as well since I'm researching a [ConvertX PX-M402U](http://www.plextor.com/english/products/M402U.htm) but I want to make sure it will work.  Also, are you running a 32-bit or 64-bit Ubuntu installation?

Peace...

---

