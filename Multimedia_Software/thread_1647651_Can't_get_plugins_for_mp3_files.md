---
title: "Can't get plugins for mp3 files"
date: 2010-12-17
forum: Multimedia Software
---

### Post by plamend91 on 2010-12-17
Hello everyone, I am relatively new to ubuntu and have all sorts of problems. 

First of all, none of my depositories work, but I'm fine with this. I think it is due to my uni wireless connection, as I haven't been able to update any linux distro here. That's the reason why I couldn't fetch the MPEG 1 Layer 3 (MP3) plugin that Rhythmbox offers me to download. So I looked for alternatives. 

I installed some restricted extras package from the official ubuntu databases, but it was only 6 KB (should it be that tiny?) and when I tried again, it still wasn't working. 

So what should I do to fix this? 
Thanks.

---

### Post by BicyclerBoy on 2010-12-17
There is a section in Ubuntu help that explains adding non-free codecs etc.

Search for keywords like restricted-extras, dvd playback, non-free,
 libavcodec etc.

If rhythmbox could not download the plugin it could be that you have restricted web access (like http only).

Note that other devices (like wifi, TV-tuner cards) need non-free firmware & sometimes non-free drivers.

For a novice user:
If your package manager can not update its database from selected repositories then you need to fix this first.
If you have been changing settings in synaptic you should try to undo/reverse your changes.

Did synaptic/update manager ever work ?
How did you install the OS ?

---

### Post by plamend91 on 2010-12-17
Although this is a little off-topic (and I am sorry),  I used a different Ubuntu-based distro for one month and noticed that only the browser and skype worked. Repositories and updates were useless. The university Internet providers are quite strict. 

So far I have tried 3 debian-based distributions and I wasn't able to access a depository from none of them. Updates don't work as well. 

No, Synaptic never worked.
I installed Ubuntu (Maverick, by the way) with a usb flash pen.

---

### Post by BicyclerBoy on 2010-12-17
I think you have your answer...

The internet protocol allows many type of services.
Any or all of them can be controlled by server or ISP.
Could be that all websites are blocked except selected few.
Could be blocked due to content or keywords..

Take your PC to an real ISP connection & try again.

---

### Post by plamend91 on 2010-12-17
Well, I already installed the missing libraries for skype manually and fixed some other minor things as well. I downloaded and installed ubuntu-restricted-extras but it doesn't work! It still can't play .mp3 files. 

What I am going for is a stable system that has everything I need. Once I achieve that, it's going to be just studying and browsing the Internet. But the .mp3 thing is killing me :) .

So what's wrong with it? 
I saw some web sites offering a 'Free MPEG1 Layer 3 MP3 codec' but I am not sure if they are trustworthy. 
Is there a different version of restricted-extras, perhaps? I downloaded the one for Maverick from the ubuntu.packages website.

---

### Post by Yellow Pasque on 2010-12-17
The restricted-extras package is just a small meta-package that depends on a bunch of other packages. Since you don't have those packages available locally and no net connection, the restricted-extras package is useless by itself. What you really want for playing mp3's on RB is this (and any dependencies you don't have): [http://packages.ubuntu.com/maverick/gstreamer0.10-fluendo-mp3](http://packages.ubuntu.com/maverick/gstreamer0.10-fluendo-mp3)

---

### Post by plamend91 on 2010-12-18
Thank you very much. This solved my problem in less than a minute.

---

