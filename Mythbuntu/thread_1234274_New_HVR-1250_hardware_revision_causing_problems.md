---
title: "New HVR-1250 hardware revision causing problems"
date: 2009-08-07
forum: Mythbuntu
---

### Post by NTolerance on 2009-08-07
So I recently purhcased a retail boxed Hauppauge HVR-1250.  I bought this card because it's digital tuner has had kernel support for quite some time.  The analog side isn't supported but I don't care about that.  

I installed the card and the drivers were loaded, but they couldn't detect the card and a dvb entry under /dev was not created.  In the end, I stumbled across a [post](http://ubuntuforums.org/showthread.php?t=1014551) here at Ubuntuforums that linked me to [this tutorial](http://www.linwik.com/wiki/installing+the+latest+v4l+tv+tuner+drivers+for+ubuntu+8.10) which I used to grab the latest v4l drivers with mercurial and install them.  This got my card working.  

I can confirm that my card is also the new and undetected revision 4:
```
$lspci | grep Conexant
03:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 **(rev 04)**
```

My concern is with kernel upgrades.  Will I have to recompile and reinstall the drivers every time a kernel update is presented with Update Manager?

---

### Post by silverdulcet on 2009-08-07
Until the version of v4l-dvb with support for your card is included in the next Mythbuntu release you will have to recompile it when you get kernel updates. After you've installed the updated kernel make sure to run
```
make distclean
```
inside your v4l-dvb source directory before you run the make/make install commands. That way it doesn't just use the config and build files for the older version of the kernel.

If you want to update the v4l-dvb source to the latest (perhaps they have fixed a bug or added features for your card. Prior to compiling, run this command in your v4l-dvb directory to update it. 
```
hg fetch
```

---

### Post by NTolerance on 2009-08-08
Thanks a ton for the heads up on that.  I really don't want to ruin my newly formed Mythbox.  Here's what I think I'm gonna do when the next kernel upgrade comes down the pipe:

1.  Install upgrade and reboot.  Check to see if HVR-1250 is broken.  If not, kernel now supports my card and I can stop here.  If so, proceed to step 2.

2.  ```
sudo apt-get install linux-headers-`uname -r`
```

3.  ```
cd /usr/src/v4l-dvb
```

4.  ```
sudo make distclean
```

5.  ```
sudo make
```

6.  ```
sudo make install
```

7.  ```
sudo reboot
```

I probably won't upgrade to the latest v4l-dvb source because an upgrade to both that and the kernel at the same time is pretty scary.

---

### Post by silverdulcet on 2009-08-09
> 1. Install upgrade and reboot. Check to see if HVR-1250 is broken. If not, kernel now supports my card and I can stop here. If so, proceed to step 2.

Thats exactly what I do. 

Just a note however, you don't need to to apt-get the kernel headers each time. Just like any other package, if you have the previous version installed, when an upgrade is available Ubuntu will update it along with the kernel.

---

### Post by NTolerance on 2009-08-20
Just wanted to say that your method works great.  Kernel update came through yesterday.  I updated and rebooted; /dev/dvb didn't exist so the update broke my tuner.  Followed the steps above and now my tuner works fine.  No need to install new kernel headers as previously stated.

---

### Post by epi 1:10,000 on 2009-08-21
Does the new revision work as well as the old?  How good is it at tuning compared to X tuner?

---

### Post by NTolerance on 2009-11-02
If anyone finds this thread via search, be advised that the 2.6.31-14-generic kernel included in Ubuntu 9.10 properly detects this card revision.  Compiling and installing the drivers as described in this thread is no longer necessary.

---

### Post by Daibhi on 2011-10-14
I am worse than a noob, I'm practically a Linux/Ubuntu virgin when it comes to command line entry so I'm learn, please bear with me. 

I've got the v4l data in my Downloads folder so am I to understand that it needs to get to /usr/src? Can someone steer clueless here in how to get there. 

Sorry to be such a PITA.

Thanks

---

### Post by NTolerance on 2011-10-14
> **Daibhi said:**
> I am worse than a noob, I'm practically a Linux/Ubuntu virgin when it comes to command line entry so I'm learn, please bear with me. 

I've got the v4l data in my Downloads folder so am I to understand that it needs to get to /usr/src? Can someone steer clueless here in how to get there. 

Sorry to be such a PITA.

Thanks

If you have a HVR-1250 and a recent version of Ubuntu, you shouldn't need to do anything described in this thread.  Ubuntu has supported this card out of the box since version 9.10.

---

