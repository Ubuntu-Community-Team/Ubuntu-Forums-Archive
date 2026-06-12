---
title: "Sound problems with 10.4 netbook remix and ASUS 1001pxd  (Realtek ALC259)"
date: 2011-02-10
forum: Multimedia Software
---

### Post by walkkenn1 on 2011-02-10
The internal microphone is not recognized.  When I plug in a mike and headset I have no sound at all.  When I run the alsamixer there is no mute box below the PCM, Mike Boost and Capture fields.  They are only on the first two fields (master and speaker). I used the sound guide that was posted on the website, but, honestly I'm afraid that I am just making the problem worse.  I have looked through the different threads and nothing seems to be working for me.  I pulled up this info as a starter:

walkkenn@walkkennHAL3:~$ uname -a
Linux walkkennHAL3 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
walkkenn@walkkennHAL3:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
walkkenn@walkkennHAL3:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
rc  libsdl1.2debian-alsa                           1.2.14-4ubuntu1.1                               Simple DirectMedia Layer (with X11 and ALSA 
ii  linux-backports-modules-alsa-2.6.32-28-generic 2.6.32-28.27                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.28.32                                    Backported drivers for alsa-driver snapshot.
walkkenn@walkkennHAL3:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC259


I have posted the configuration at  [http://www.alsa-project.org/db/?f=5b6bed00ad7e6bcabac561bff6c185c5a4785c29](http://www.alsa-project.org/db/?f=5b6bed00ad7e6bcabac561bff6c185c5a4785c29)
Thanks for the help!:)

---

### Post by walkkenn1 on 2011-02-11
[http://paste.ubuntu.com/565882/](http://paste.ubuntu.com/565882/)

 [http://www.alsa-project.org/db/?f=d88af7e00befc9b4e7d5cc6555420e5bdee223d4](http://www.alsa-project.org/db/?f=d88af7e00befc9b4e7d5cc6555420e5bdee223d4)

The last one seems to indicate that there are no input devices listed, but I don't have the expertise to fix the problem.

---

### Post by harlandski on 2011-02-22
I am in the process of installing Ubuntu Netbook Remix 10.10 on my ASUS 1001pxd, and it seems like I'm going to have the same problem. I'm running Ubuntu from my pendrive at the moment, but it also seems like the internal mic isn't working. I'm afraid I don't have any solutions at the moment. I'll post any success I have here.

---

### Post by walkkenn1 on 2011-02-23
I have since determined that a microphone works if connected through the microphone jack.  You have to play with the recording sound in sound preferences.  I still can't get the internal mic to work in any configuration.

One of the things I tried was to change my version of ALSA to 1.0.23 and that didn't work any better, so now I am back to 1.0.22

I also tried what I could of the solutions on the Sound Guide troubleshooting manuel that was posted online.

Like I said, I can now use the sound recorder with an internal mic, but I have not been able to get the internal mic to work or any mic to work with SKYPE.

---

### Post by walkkenn1 on 2011-02-23
My problem is now solved.  It seems that I was simply overmodulating the input.  Go to sound preferences and go to input.  I had the mic input set at 100% when it should actually be set at unamplified at the input level.  When the input level is set somewhat above that (unamplified), it just doesn't work.  

I also don't know if this is the fix for the problem, or I have done something else and inadvertently fixed it some other way.

---

### Post by walkkenn1 on 2011-03-09
This problem is continuing.  After a new update the microphones failed again.  I seem to be going in circles here.  In an attempt to fix them I have updated to ALSA 1.0.23, but I have the same problem.  Can't seem to get this to work on the ASUS for any great length of time.:confused:

---

### Post by walkkenn1 on 2011-03-09
Info on configuration can be found here:






 [http://www.alsa-project.org/db/?f=577edb050fb70e16a38a0d7f3e6749df69dd9053](http://www.alsa-project.org/db/?f=577edb050fb70e16a38a0d7f3e6749df69dd9053)



Thanks for any help

---

### Post by walkkenn1 on 2011-03-12
I tried to get a mic working by connecting a USB headset to the  computer.  Any program I opened to try to test the device (skype or sound recorder) would freeze up.   When I leave the headset connected to  the computer during restart, the computer would not boot up.  I have  not seen any problems with any other USB devices (memory stick, hard  drive, etc.) which I used daily.

---

### Post by walkkenn1 on 2011-03-17
OK, I got it fixed again.  My solution may not be as elegant as some, but, here goes ...

I opened System>Administration>Synaptic Package Manager and used the search tool using ALSA.  Then I studied all of the installed packages.  I found my ALSA driver package and used the Package Manager to "mark for complete removal".  Then I removed it.

Then I restarted my computer.  Then I used these commands to reinstall it:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)

Then reboot.

Hey, it worked! :D

The only problem I seem to have now is getting the sound alert for new mail to work.  I have checked in sound preferences and I've checked evolution to see if it's turned on.  

But if this is the only problem, I'll survive.

---

