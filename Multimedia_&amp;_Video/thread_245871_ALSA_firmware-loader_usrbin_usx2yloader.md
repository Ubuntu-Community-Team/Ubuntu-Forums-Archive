---
title: "ALSA firmware-loader usr/bin usx2yloader"
date: 2006-08-28
forum: Multimedia &amp; Video
---

### Post by thestuckup on 2006-08-28
I recently applied the 2.6.16-rt29 realtime patch for low latency and my os is up and running fine.  I need to load to get the 'usx2yloader' working (it is a loader for some tascame usb soundcards, in my case, a us-122).  In reading different threads and how-to's for doing this I notice that they are all downloading earlier versions of the alsa firmware loaders than I have already installed according to my synaptic package manager (All the posts are applying 1.09.[whatevers].  I have 1.0.10.  Ok, no big deal. I move on in the threads and download this loader and unzip it which is a hex file

wget [http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2](http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2)

From looking at the readme file and the thread at

[http://www.ubuntuforums.org/showthread.php?t=194490](http://www.ubuntuforums.org/showthread.php?t=194490)

the ld2-ezusb.hex file will replace the tascam_loader.ihx

The thread has me replacing it under the /usr/share/alsa/firmware folder - which I do not have... and I used the search of my hard drive to find that the only one of either of these files I have was the one I downloaded.

however...

under the /usr/bin directory, there is a usx2yloader executable but I assume it is only something that initiates a process not unloads a bunch of files I need?

---

### Post by floogy on 2006-08-29
Maybe you should do something like this??:

```
sudo mkdir -p /usr/share/alsa/firmware
cd /usr/share/alsa/firmware
wget http://langerland.de/linux/usx2y/usx2y-fw-0.1b.tar.bz2
```

But I'm not sure. Maybe you'll have to configure and compile your kernel, to get that directory, and the necessary alsa stuff for firmware dependand usb-audio cards??

If you get it working, please tell me, because these soundcards are looking very interesting. Does anybody know how they would work on low latencies?

---

