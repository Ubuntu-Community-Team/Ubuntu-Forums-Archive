---
title: "My Hauppauge HVR 1600 Analog success story"
date: 2008-07-06
forum: Mythbuntu
---

### Post by heimdal31 on 2008-07-06
Ok, I've spent days playing with this, so I wanted to put it down for posterity.  Please, anyone, chime in with corrections or additions:

System:

Dell Precision 370 mid-Tower
1 GB RAM
EVGA NVIDIA e-GeForce 8500 GT w/512MB RAM (Because the ATI card that came with the system I could not get to work)
Hauppauge HVR-1600
Analog Cable 

MythBuntu 8.04 ISO

I'm doing much of this from memory and scrawled notes, which is why I ask people to chime in with corrections. 

First, install defaults from the CD.  When you get to the MythBuntu set-up, go through the first step, but you can't do any others, since the Hauppauge won't be recognized.

Reboot and get up and running.  Get into the MythBuntu setup (Utilities/Setup -> Setup -> MythBuntu).  

Start Synaptic Package manager and install the kernel-headers package for whatever kernel is currently loaded. (Needed so you can compile cx18 driver).  Also, while there, add ivtv-utils package.

Start update manager and download all updates.

Reboot.

Now we are ready to go with the installation guide at [http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600]("http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1600") with some slight modifications and expansions:

1. Grab the latest v4l-dvb drivers from [http://www.linuxtv.org/hg/v4l-dvb](http://www.linuxtv.org/hg/v4l-dvb").  You can do this by:
[INDENT]a. Start a terminal window
b. **mkdir cx18; cd cx18**
c. start FireFox
d. open [http://www.linuxtv.org/hg/v4l-dvb](http://www.linuxtv.org/hg/v4l-dvb) in FireFox
e. right-click -> copy on the "gz" link at the top of the page
f. in terminal window issue: **wget <pasted gz link>**[/INDENT]

This should give you a file called tip.tar.gz in your cx18 directory.  (NOTE:  If you get to the end and this doesn't work, I specifically used revision 8172 which should be available at [http://www.linuxtv.org/hg/v4l-dvb/archive/682760d4b111.tar.gz]("http://www.linuxtv.org/hg/v4l-dvb/archive/682760d4b111.tar.gz") )

2.  Untar it by issuing in your terminal window: **tar -xzvf tip.tar.gz**

3.  Now we get the Hauppauge firmware by issuing: **wget [http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz](http://dl.ivtvdriver.org/ivtv/firmware/cx18-firmware.tar.gz) **

4. **tar -xzvf cx18-firmware.tar.gz **

5.  Copy firmware to the correct directory.  It's going to be the /lib/firmware/... directory that relates to the currently running kernel.  Every time a kernel is updated, you will also have to repeat these steps. (The cx18 compilation and the firmware in the appropriate directory)

6.  cd into the cx18 created by untarring in step 2.

7. **make**

8. If there are no errors **sudo make install**

9. **sudo make unload**

10. **sudo modprobe cx18 **

If all goes well, your card is working.  Test by doing:

1.  Start a terminal window

2. ** /bin/cat /dev/video0 > test.mpg **

3.  Wait a few seconds and hit ctrl-c

4.  **mplayer test.mpg**

If you see video and hear sound, you are in good shape.  If like me, you don't, you have more work to do.

I restarted, and found that X wouldn't load.  Mythbuntu would start up with the VESA drivers complaining that it had problems and I would be unable to get it working with the proprietary nvidia drivers.  Eventually, I stumbled on pointers to [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/appendix-l.html]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9629/README/appendix-l.html"), which explains in the section titled "Kernel virtual address space exhaustion on the X86 platform" that you need to pass some additional parameters to the kernel when it boots.  I used vmalloc=256MB and did not need to use the uppermem param.

If you have the same low graphics problem I did, then you need to edit your /boot/grub/menu.lst  file to include the additional parameter(s).  Any time you update your kernel, you will likely need to edit it again.

Now, you can finally run the backend setup for MythBuntu, which should allow you to actually do steps 2 - 4, but I ran into some oddities in setting up the analog side of the card.  If I chose the v4l card type, then the Hauppauge HVR 1600 was listed.  Unfortunately that did not work.  If I chose the Hauppauge PVR card type, then the card was not listed.  I found I had to chose the v4l card, save it, re-open it to edit and change it to a Hauppauge PVR card.  I'm assuming this is because of the particular driver I compiled and may not happen to all.

Finally, things were almost working.  I could see video, but I had no sound.  I struggled with this for quite some time, but finally stumbled across [http://www.mail-archive.com/ivtv-devel@ivtvdriver.org/msg05506.html]("http://www.mail-archive.com/ivtv-devel@ivtvdriver.org/msg05506.html") where I found that you need to change the audio section of your live TV profiles (Utilities/Setup -> TV Setting -> Recording Profiles -> MPEG-2 Encoders (PVR-x50, PVR-500)) to change them all to 48kHz with a bitrate of 224kb/s.

Once I did that, all was working.

There are other (and better) places with information on getting the Hauppauge 1600 to work, but I didn't find many that pointed to the nVidia vmalloc solution and found even fewer that pointed to the analog audio answer.

I don't have access to a HDTV source, so I can't comment on the HD side of the Hauppauge 1600.

---

### Post by OffAxis on 2008-07-07
Thanks for documenting the steps you took.

I just wanted to chime in on step number 2 (the second #2)
>  /bin/cat /dev/video0 > test.mpg 

you can stream the video straight to mplayer without saving to a file.
```
mplayer /dev/video0
```

---

### Post by azmanam on 2008-07-08
Thank you for posting this.  I, too, am trying to get a Hauppauge 1600 card to work.  I'm following your instructions with no problem until I get to step 9: sudo make unload.

make and make install work fine, but sudo make unload gives the following error for most of the entries:
  ERROR: Module *(module name)* is in use by cx18 (or something else, but usually cx18)

Any ideas where to go from here?

Thanks!

---

### Post by Nishtya on 2008-07-15
I too want to thank you!  I have had a HVR 1600 gathering dust for ages that I got for a media pc build.  Finally broke down and bought XP for the media PC before I wouldn't be able to get it anymore. But now, hey, trying linux on it.

Everything went beautifully up to the test (mplayer /dev/video0)

I can see mplayer start to load, the screen scrambles a bit and then my monitor goes blank with an "unsupported mode" message.

So I went to another console and as root brought the vmalloc up to 192, rebooted, tried the test again, same thing.  Kicked vmalloc up to 256MB.  Rebooted.  Same thing.  

Perhaps more an mplayer problem then the video drivers? I can boot fine.  No problems I until I crank up the mplayer for video0 Not sure.  Any ideas?

---

### Post by Buckwheat469 on 2008-08-17
Thank you for the step regarding configuring the card as a V4L in the backend setup, then setting it to PVR after saving it. This was the key that I needed. I couldn't figure out how I got it working before, but I guess the driver must have changed, or I skipped a step.

Well Done!

Now I just have to get the sound set up on the right card.

---

### Post by sbhargav21 on 2008-09-08
I have till Step 9 working.
When I try to cat on /dev/video0 it is not detected.

Any help is appreciated.
Thanks

---

### Post by jesusdemontreal on 2008-09-27
No pretending to solve any issues but rather a comment on my personnal story.

I have two HVR 1600 cards in the same pc along with a NVidia 6200, sound card and network. I had some issues with one of my card being badly or not at all recognized. After a while, I came to understand that the card was sharing IRQ with the NVidia card, which for some reason resulted in my broken card.

A rather barbaric fix for this was to turn off the computer, remove the HVR cards, network and sound and installing them in this order

PCI-1 HVR 1600
PCI-2 HVR 1600
PCI-3 Empty
PCI-4 Network
PCI-5 Sound

On my motherboard, the PCI slots are actually marked down, but on most motherboard, if not indicated, the first PCI slot is the closest one to the CPU. 

Doing so and telling my BIOS to clear the ESCD data (in the PnP options from the BIOS) changed my IRQ's so now my soundcard shares IRQ with the HVR 1600. This seemed to solve all my issues with lags, freezes and system malfunction.

---

### Post by dagar on 2008-10-06
> **sbhargav21 said:**
> I have till Step 9 working.
When I try to cat on /dev/video0 it is not detected.

Any help is appreciated.
Thanks
I had this problem at 1st.  Try a 'sudo make remove' and then reboot.
When it comes back up, do the make clean, make, make install, make unload, modprobe cx18.

Now has anyone gotten the remote to work and how?

---

### Post by geowtx on 2008-10-07
I don't have an answer but while browsing around I found this related thread. [http://www.gossamer-threads.com/lists/ivtv/users/39009](http://www.gossamer-threads.com/lists/ivtv/users/39009)

Hope this helps..

---

### Post by Despotic on 2008-11-19
Hey folks,
I've just replaced my ATI AIW9600xt with a nVidia 6200 and a Hauppauge HVR-1600. It didn't work out of the box like I had hoped, but I've come across this thread now.
I followed all of your steps above and when I got to 10 I think, I failed.
I tried both methods, shortcut first
```
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ mplayer /dev/video0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm)  (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
File not found: '/dev/video0'
Failed to open /dev/video0.


Exiting... (End of file)
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ /bin/cat /dev/video0 > test.mpg
/bin/cat: /dev/video0: No such file or directory
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ 

```

any assistance is very welcome. I've been damn determined to get tv on my box, but if this isn't working before I can return the card, I'm gonna take a break from trying again.

Thanks in advance.

---

### Post by saedelaere on 2008-11-21
> **Despotic said:**
> Hey folks,
I've just replaced my ATI AIW9600xt with a nVidia 6200 and a Hauppauge HVR-1600. It didn't work out of the box like I had hoped, but I've come across this thread now.
I followed all of your steps above and when I got to 10 I think, I failed.
I tried both methods, shortcut first
```
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ mplayer /dev/video0
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm)  (Family: 6, Model: 10, Stepping: 0)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /dev/video0.
File not found: '/dev/video0'
Failed to open /dev/video0.


Exiting... (End of file)
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ /bin/cat /dev/video0 > test.mpg
/bin/cat: /dev/video0: No such file or directory
jesse@despotica:~/cx18/v4l-dvb-5dc4a6b381f6$ 

```

any assistance is very welcome. I've been damn determined to get tv on my box, but if this isn't working before I can return the card, I'm gonna take a break from trying again.

Thanks in advance.

Please post 

```
dmesg | grep cx18
```

---

### Post by MTDrifter on 2008-11-21
All was going well with my HVR-1600 on a Mythbuntu 8.10 build. Everything worked great! Then I decided to add another HVR-1600 card (I decided to use my XP box for something else and didn't want the tv card in it anymore). Everything but the audio worked on the 2nd card. It would do everything...without audio on the "new" 2nd card. 

I followed all the steps 1 thru 10 and steps 1 - 4 (revised). Audio and video worked from both cards. 

Rebooted the machine just to make sure it was on a fresh start and loaded MythTV (/dev/video0)... worked fine. 

Switched to input from /dev/video1 and it wouldn't lock on a channel.
 
Exited and ran mythfilldatabase then tested again. Everything is working great again. We can watch and record TV from both cards at the same time (I'm also running MythTV Frontend from another box in another room).

Thank you for posting your steps. I was almost ready to remove the 2nd card.

Next step...install some oddball USB wireless device... that'll be a whole other story.

---

