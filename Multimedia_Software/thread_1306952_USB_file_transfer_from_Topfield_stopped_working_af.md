---
title: "USB file transfer from Topfield stopped working after 9.04 --&gt; 9.10"
date: 2009-10-30
forum: Multimedia Software
---

### Post by PeteP-1970 on 2009-10-30
Hi all,
I have been using my old Amilo Li2727 laptop and Puppy with my Topfield 5100. It did not work out-from-the-box with 9.04, first I got these errors:

ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading

but editing the **/etc/init.d/mountdevsubfs.sh** and adding these lines at the end of the file did the trick in 9.04:

```
#
     # Magic to make /proc/bus/usb work
     #
     mkdir -p /dev/bus/usb/.usbfs
     domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
     ln -s .usbfs/devices /dev/bus/usb/devices
     mount --rbind /dev/bus/usb /proc/bus/usb
```After upgrading to 9.10 I am back to square one, and again getting the same errors I got with 9.04 before editing the mentioned file. 

I did not take very long from me to notice that **mountdevsubfs.sh** is gone, instead there is now file called:
[B]
mountdevsubfs.sh.dpkg-old[/B], so I guess it is not used anymore and all the stuff have been moved to another place/file?

So now what? What I need to do/edit to get my Ubuntu to work again with my Topfield? Also the WLAN stopped working, so nice going ... [-X

---

### Post by rickbeton on 2010-02-06
...stunned silence. No advice has come.

There is another thread with the same dead end [here]("http://ubuntuforums.org/showthread.php?t=307216&page=7").

I get

```
> puppy -c dir
ERROR: Can not perform autodetection.
ERROR: /proc/bus/usb/devices can not be open for reading.
ERROR: No such file or directory

```

I wonder whether the problem is that Puppy is three years out of date and needs recompiling against the current APIs.  Or is it simply that it is trying to access /proc/bus/usb/devices and that's an obsolete location long since removed - I don't know this I'm merely guessing.

Rick

---

### Post by rickbeton on 2010-02-06
I found some more information by googling: it seems that the procfs used in Linux 2.4 was changed to the sysfs in Linux 2.6, at which point the device scanning done by puppy would have stopped working.

It needs a bit of re-writing. I could attempt this if someone would tell me how it's supposed to be done.

Rick

---

### Post by rickbeton on 2010-02-14
OK, I found the answer to this one spread across several of the Net's nooks and crannies.

Here's my [solution]("http://www.bigbeeconsultants.co.uk/puppy-for-ubuntu") (based on other people's work).

---

### Post by griamdu on 2010-11-06
Don't know if this could help someone... But as I was searching a solution to get recorded files from my Topfield since I use Ubuntu 10.10 instead of Windows (by the Altair application), I found this thread and I plug the PVR to see. I saw that Ubuntu mounts a device with the gphoto2 system file. I get the gphoto2 package and used the gphoto2 command line. I was then very surprised when I managed to get files with the --get-file=RANGE option : this worked the first time I tried !!


More comments

gphoto2 only works to download files from the PVR

And, as it was just said over...
To upload files to the PVR, I made the change in puppy 1.14 to support the new way to catch usb devices with sysfs support (path is like /dev/bus/usb/BUS_NB/DEVICE_NB). The info is from the puppy author site here :   [http://peteru.blogspot.com/](http://peteru.blogspot.com/)         See "A third party patch to add sysfs support to puppy is available ..." to have differences between the old puppy.c file and the new one.

---

