---
title: "Ubuntu 10.04 does not sync iPod Touch"
date: 2010-10-09
forum: Multimedia Software
---

### Post by insanekat on 2010-10-09
I just got a 4th generation iPod Touch today. I plug it in to my laptop (Ubuntu 10.04), it recognizes it as a photo storage but it will not recognize it in Rhythmbox or Banshee. Therefore I cannot get any files on to it. Although when I plug it in and open Rhythmbox it makes a little noise.

I have tried installing libimobiledevice, ifuse and tried with gtkpod (basically I've read a lot of stuff about getting it to work) all to no avail. I also plugged it into Windows Vista to get it started as well as transferred a song from iTunes 10 to it, and it still doesn't do much when on my laptop.

It seems to not be mounted in the proper place for gtkpod and no fixes seemed to work. For using ifuse it does not seem to recognize that it is plugged in. I have updated all the libimobiledevice packages and still nothing.

I hope someone can help me out! I can try and answer other questions you guys may have. Thanks.

---

### Post by insanekat on 2010-10-10
Still no luck with this...

I should also mentioned that when I run

ifuse /mnt/ipod/

it comes up with the "No device found. Is it connected?" dialogue, same when I run ideviceinfo in the terminal.

---

### Post by Predatorian on 2010-12-09
I am having a problem with my desktop mounting my ipod touch 64gig. i was able to get my ipod touch working with my netbook while i was in afghanistan, but now i cant, and ive upgraded from 9.04 to 10.04. ive read a lot of documentation, and ifuse didnt work, i cant find the libmobiledevice in synaptic or apt. ive downloaded gtkpod and libgpod a billion times, and usbmuxd. still no change, doesnt even recognize it as a plugged in device, yet it'll charge. I am running the 64bit system, and it will not recognize my ipod. im..very..frusterated. please help me.

---

### Post by Dante311 on 2011-04-26
I'm having similar problems.  When I input ideviceinfo I receive the following error:


GNUTLS ERROR: A TLS packet with unexpected length was received.

I have ifuse installed and lib1 libraries.

It's frustrating that I can't use my Ipod...

---

### Post by hydrox24 on 2011-09-22
I am having this issue. HOwever it is the case that when I try to mount my iPod touch 2G with ifuse (using the device UUID) it spits out the following error:
```

GNUTLS ERROR: A TLS packet with unexpected length was received.
```

I have tried reinstalling iFuse but to no avail. Please help as this is causing me great difficulty

---

### Post by technosysind on 2011-09-22
Has anyone of you tried using WINE + PLAYONLINUX??
Try it!! It will work for sure with itunes

---

### Post by hydrox24 on 2011-09-22
Just been doing some research, looks like I might be able to retrieve a solution from a combination of these websites:

[http://askubuntu.com/questions/27141/nothing-happens-when-i-connect-my-iphone-3g-to-my-laptop](http://askubuntu.com/questions/27141/nothing-happens-when-i-connect-my-iphone-3g-to-my-laptop)

[http://www.streamreader.org/askubuntu/questions/27141/nothing-happens-when-i-connect-my-iphone-3g-to-my-laptop](http://www.streamreader.org/askubuntu/questions/27141/nothing-happens-when-i-connect-my-iphone-3g-to-my-laptop)

[http://ubuntuforums.org/showthread.php?t=1628529&page=4](http://ubuntuforums.org/showthread.php?t=1628529&page=4)

So wish me luck, I will edit this post with the results tomorrow.

---

### Post by hydrox24 on 2011-09-29
Sorry that it took me so long to post back, but the solution for me was to install the latest version of libimobile device and follow the directions of this thread for installation:
[http://ubuntuforums.org/showthread.php?t=1471018](http://ubuntuforums.org/showthread.php?t=1471018)
After installing a newer version of libimobile device I used the
```

idevicepair unpair

```
command twice and then quickly running the 
```

iFuse /mnt/iPod/

```
code because if you wait too long it seems to repair. This worked well for me and I will keep an eye on this thread incase my method has issues to it.

---

