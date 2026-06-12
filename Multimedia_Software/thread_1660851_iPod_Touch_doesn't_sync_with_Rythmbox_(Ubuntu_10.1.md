---
title: "iPod Touch doesn't sync with Rythmbox (Ubuntu 10.10)"
date: 2011-01-05
forum: Multimedia Software
---

### Post by abelandlinux on 2011-01-05
I am new to Ubuntu (using 10.10) and I just can't get my iPod Touch to sync with my Rythmbox.

When I plug my iPod into the USB port, a message is prompted, which tells me it detected a digital music device and asks me to select a program to access it. Then I select "Rythmbox" and Rythmbox opens.

My iPod's name shows on the left bar, but when I select it, no songs appear, and also I can't drag songs from my library to my iPod.

I aready tried Banshee and Amrok and it didn't work on those either.

I really appreciate your help.

---

### Post by insanekat on 2011-01-08
I am having the same issue. I drag files over to my ipod touch in Rhythmbox, it says that it is transferring and my ipod even says "sync in progress", but the files don't show up.

---

### Post by afogl001 on 2011-01-14
Has this issue been resolved.  I'm postponing upgrading my other computer until I'm sure I can sync my touch, and I have not been able to on my 10.10 machine.  Could have something to do with "upgrading" instead of installing 10.10 fresh?  Thanks!

---

### Post by Vexed Arcanist on 2011-01-15
> **afogl001 said:**
> Has this issue been resolved.  I'm postponing upgrading my other computer until I'm sure I can sync my touch, and I have not been able to on my 10.10 machine.  Could have something to do with "upgrading" instead of installing 10.10 fresh?  Thanks!

I had this issue, had done a fresh install not long after 10.10 released but only recently tried to use my iPod 4g w/4.02 iOS in Ubuntu.  Just did a search and found this web page:

[Get iOS4 Working]("http://www.webupd8.org/2010/12/get-ios4-mountsync-working-in-ubuntu.html")

It worked like a charm, but I can't say how reliable the ppa user is, so always be cautious.  You may find a more official means to correct the issue.

---

### Post by afogl001 on 2011-01-19
Hhhmmm, interesting.  I may just do a fresh install of 10.04 until this is fixed.  I'm a little upset though since being able to freely use iPods out of the box in Ubuntu was a huge selling point to friends.  Hopefully this will be patched :(

---

### Post by WieWeetWat on 2011-03-03
Hi,

I just solved this problem for myself. My Ipod had a reset whith Itunes using a mac. I had the same problems as mentioned.
The mac used ROOT to reset the system.
I installed ITunes on a windows PC and had another reset. The partition table now was a windows version.

Now it works fine for me.

Good luck y'all
Greetings from holland

---

### Post by johntaylor1887 on 2011-03-03
> **afogl001 said:**
> Hhhmmm, interesting.  I may just do a fresh install of 10.04 until this is fixed.  I'm a little upset though since being able to freely use iPods out of the box in Ubuntu was a huge selling point to friends.  **Hopefully this will be patched** :(

Until then, do:
```
$ mkdir /tmp/packages && cd /tmp/packages

$ wget -nc -c http://archive.ubuntu.com/ubuntu/pool/main/{libi/libimobiledevice/libimobiledevice0_0.9.7-1ubuntu1,libm/libmtp/libmtp-dev_1.0.2-1ubuntu1,libm/libmtp/libmtp8_1.0.2-1ubuntu1,libu/libusb/libusb-0.1-4_0.1.12-14ubuntu0.2,libu/libusb/libusb-dev_0.1.12-14ubuntu0.2}_`dpkg --print-architecture`.deb

$ sudo dpkg --install *.deb

$ sudo apt-get hold libmtp8 libmtp-dev libusb-dev libusb-0.1-4
```

You can also use gtkpod to sync your ipod. Works great for me.

---

