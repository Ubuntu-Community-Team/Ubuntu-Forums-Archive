---
title: "No way works for me (VDPAU)"
date: 2010-03-24
forum: Multimedia Software
---

### Post by Laxman_prodigy on 2010-03-24
Hi.

I have tried many ways to enable vdpau support in my machine but for no avail. A member here helped me very much but I couldn't manage to succeed.

My system has Ubuntu 9.10 64-bit, Nvidia 8500GT 512mb, Intel Core 2 duo. I have installed Nvidia driver version 195 currently available from their site.

I tried compiling mplayer with vdpau support from various tutorials thread here around in Ubuntu forums.

None of them worked(I don't know if I couldn't import what they suggested).

Now. Is there anyone in this forum with Ubuntu 9.10 64 bit with the same other system requirements as mine who have successfully managed to make the VDPAU work?

Please do suggest me. It has been a terrible weekend trying to do what I want.:(

---

### Post by tcchris on 2010-03-24
I had a 8500gt working with vdpau . 
I had nvidia team ppa added
195 driver , 185 has vdpau , but did not work as well for me
install libvdpau !!!!!
not sure where to get the proper mplayer , as I was using boxee.

---

### Post by Laxman_prodigy on 2010-03-24
Thanks for the reply. But I have already installed the drivers.

Won't they conflict with other drivers in the said ppa?

Anybody else who has been able to use vdpau capability?

---

### Post by Laxman_prodigy on 2010-03-24
**Members**

Please do reply.

---

### Post by Laxman_prodigy on 2010-03-24
Is anybody here able to enable VDPAU support by compiling Mplayer on 64bit Ubuntu by using Nvidia driver version 195?

If yes, just let me accomplish just that how you did. Please.:oops:

---

### Post by Laxman_prodigy on 2010-03-24
My cores are pumping at Core 1- 100% and Core 2- >=40%.

I have Nvidia 8500GT but don't know how to enable this in the SMplayer.

I have compiled it but it doesn't work in "VDPAU" video output driver.

Please help me somebody!?

---

### Post by Laxman_prodigy on 2010-03-24
[B]Is it that nobody here has vdpau-enabled mplayer in 64bit ubuntu?
[/B]

---

### Post by rvm4000 on 2010-03-24
You can find mplayer packages compiled with vdpau support here:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

### Post by Laxman_prodigy on 2010-03-25
> **rvm4000 said:**
> You can find mplayer packages compiled with vdpau support here:
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")


But nothing is said there about "VDPAU".

---

### Post by Laxman_prodigy on 2010-03-25
> **rvm4000 said:**
> You can find mplayer packages compiled with vdpau support here:
[https://launchpad.net/~rvm/+archive/mplayer]("https://launchpad.net/%7Ervm/+archive/mplayer")


Okay, I have done. Again, only sound and no video when output driver is set at "Vdpau".

---

### Post by WannabeFantasma on 2010-03-25
Do you really want to use that Mplayer?

I got it to work in XBMC.

I'll try it out with Mplayer this weekend (I got nothing to do so :D )

---

### Post by Laxman_prodigy on 2010-03-25
> **WannabeFantasma said:**
> Do you really want to use that Mplayer?

I got it to work in XBMC.

I'll try it out with Mplayer this weekend (I got nothing to do so :D )


I am okay as long as I have "VDPAU" enabled. I don't mind using any player.

How did you do?

---

### Post by WannabeFantasma on 2010-03-25
> **Laxman_prodigy said:**
> I am okay as long as I have "VDPAU" enabled. I don't mind using any player.

How did you do?

I installed drivers (you probably have them already)
Then I installed XBMC (synaptic), start xbmc then: **Settings->Video->Players' and change the Render Method to VDPAU.**

that should do it.

---

### Post by rvm4000 on 2010-03-25
> **Laxman_prodigy said:**
> Okay, I have done. Again, only sound and no video when output driver is set at "Vdpau".

What's the output from mplayer? It will probably provide info about why vdpau didn't work.

---

### Post by Laxman_prodigy on 2010-03-25
> **WannabeFantasma said:**
> I installed drivers (you probably have them already)
Then I installed XBMC (synaptic), start xbmc then: **Settings->Video->Players' and change the Render Method to VDPAU.**

that should do it.


I have installed it. Now it says, I need "Hardware accelerated OpenGL rendering, Install appropriate blah blah"

I have already installed Nvidia drivers from Nvidia site Version 195.

What else do I need?

Will you help me with this please?

---

### Post by Laxman_prodigy on 2010-03-25
> **rvm4000 said:**
> What's the output from mplayer? It will probably provide info about why vdpau didn't work.


Hi.
I cannot even start it. It says, "Error opening initialising the selected video out". and only sound.  Sometimes it says "bad ram/cpu usage blah blah"./

Mplayer has always terrified me with that "Bad cpu/ram usage". The output is set at "VDPAU with X11"..

How do I know if "VDPAU" files or libraries are installed in my computer. Note that I have 64 bit computer.

The output of a command is here if it helps:
```
laxman@Cray-Jaguar:~$ sudo find /usr -iname 'libvdpau_nvidia.so'
[sudo] password for laxman: 
/usr/lib32/libvdpau_nvidia.so
/usr/lib/libvdpau_nvidia.so
laxman@Cray-Jaguar:~$ 
```

**Also, the output of the following is this if it helps too:**


laxman@Cray-Jaguar:~$ mplayer -vo vdpau -vc ffh264vdpau /home/laxman/Videos/Hollywood/Transformers.mp4 
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/laxman/Videos/Hollywood/Transformers.mp4.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [avc1]  1280x528  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
==========================================================================
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
FAAD: compressed input bitrate missing, assuming 128kbit/s!
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [faad] afm: faad (FAAD AAC (MPEG-2/MPEG-4 Audio))
==========================================================================
[pulse] working around probably broken pause functionality,
        see [http://www.pulseaudio.org/ticket/440](http://www.pulseaudio.org/ticket/440)
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video

---

### Post by WannabeFantasma on 2010-03-25
> **Laxman_prodigy said:**
> I have installed it. Now it says, I need "Hardware accelerated OpenGL rendering, Install appropriate blah blah"

I have already installed Nvidia drivers from Nvidia site Version 195.

What else do I need?

Will you help me with this please?

Here it just worked...
Although I installed my drivers at System -> Administration -> Restricted drivers
not from the Nvidia site, not sure if that has something to do with it.

On other forum people with that problem 
Try running

> sudo nvidia-installer --update 

---

### Post by cchhrriiss121212 on 2010-03-26
```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```
This was causing me problems for the last few weeks but I managed to get things working today by googling around. A few things to try:
Install libavcodec-unstripped-52 and libavutil-unstripped-49 which will replace other versions.
Install libfaad2 after downgrading libfaad0 (force 2.61 from menu).
Updating the nvidia ppa, and installing latest versions of mplayer and libvdpau.
I also had a permission problem with /dev/nvidiactl but that may not affect you.
Disable post processing and multi threading.
Add this into smplayer preferences>advanced>options for mplayer>options:
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,

Try using vdpau with xine instead of mplayer as that worked with me first. I have no idea whether any of these are redundant but I'm not going to mess around with something that has taken hours to work. Good luck with it Laxman.

---

### Post by Laxman_prodigy on 2010-03-26
> **cchhrriiss121212 said:**
> ```
[vdpau] Error when calling vdp_device_create_x11: 1
Error opening/initializing the selected video_out (-vo) device.
```This was causing me problems for the last few weeks but I managed to get things working today by googling around. A few things to try:
Install libavcodec-unstripped-52 and libavutil-unstripped-49 which will replace other versions.
Install libfaad2 after downgrading libfaad0 (force 2.61 from menu).
Updating the nvidia ppa, and installing latest versions of mplayer and libvdpau.
I also had a permission problem with /dev/nvidiactl but that may not affect you.
Disable post processing and multi threading.
Add this into smplayer preferences>advanced>options for mplayer>options:
-vc ffmpeg12vdpau,ffh264vdpau,ffwmv3vdpau,ffvc1vdpau,

Try using vdpau with xine instead of mplayer as that worked with me first. I have no idea whether any of these are redundant but I'm not going to mess around with something that has taken hours to work. Good luck with it Laxman.


Thanks chris. I will try it soon I get on my pc.:)

---

### Post by andrew.46 on 2010-03-27
Hi Laxman,

I am sincerely sorry to see you still struggling with this issue, I know I was of little use to you in another thread with the same issue. Perhaps it has come time to cut the Gordian knot and *uninstall* the drivers you have installed from the nVidia site and install the 195 drivers, libvdpau, vdpauinfo, MPlayer and SMPlayer packages from this PPA:

Nvidia Vdpau Team PPA 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

I do not possess an nVidia card myself and I have not experimented with vdpau, as I have mentioned before, but if I was caught in this trouble that you find yourself this is a course of action that I would take myself. There are of course other ways but perhaps this will be the easiest...

Continue to be patient, I am sure a resolution for this issue must exist :).

All the best,

Andrew

---

### Post by Laxman_prodigy on 2010-03-27
> **andrew.46 said:**
> Hi Laxman,

I am sincerely sorry to see you still struggling with this issue, I know I was of little use to you in another thread with the same issue. Perhaps it has come time to cut the Gordian knot and *uninstall* the drivers you have installed from the nVidia site and install the 195 drivers, libvdpau, vdpauinfo, MPlayer and SMPlayer packages from this PPA:

Nvidia Vdpau Team PPA 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")

I do not possess an nVidia card myself and I have not experimented with vdpau, as I have mentioned before, but if I was caught in this trouble that you find yourself this is a course of action that I would take myself. There are of course other ways but perhaps this will be the easiest...

Continue to be patient, I am sure a resolution for this issue must exist :).

All the best,

Andrew



Thank you Andrew. 

I installed Ubuntu in my brother's pc with 9600GT and installed everything from the said ppa.

It works flawless on his system with CPU usage of 2-4%.

Now, I thought I may have messed up my system so I reinstalled Ubuntu and did the same thing. But, again no video and only sound and sometimes the mplayer terrifies me with those "Bad cpu usage" etc.

My card is Geforce 8500GT. I have 195 version of Nvidia installed from their ppa as I can clearly see it under "System - Administration-Nvidia X-server settings".

But,  now again the same thing.

On terminal the output of the following command is :
```
laxman@Cray-Jaguar:~$ vdpauinfo
display: :0.0   screen: 0
Error creating VDPAU device: 1
laxman@Cray-Jaguar:~$ 
```

Any help from any member would be greatly appreciated at this moment.

---

### Post by andrew.46 on 2010-03-27
Hi Laxman,

Good to hear that at least it all installed and ran well on your brother's computer. As regards your own computer I am afraid that I am totally out of ideas, my apologies...

Have you thought of approaching the [nVidia Forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14")? I should mention that these forums are in no way as friendly as the Ubuntu Forums :(.

Andrew

---

### Post by Laxman_prodigy on 2010-03-27
> **andrew.46 said:**
> Hi Laxman,

Good to hear that at least it all installed and ran well on your brother's computer. As regards your own computer I am afraid that I am totally out of ideas, my apologies...

Have you thought of approaching the [nVidia Forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14")? I should mention that these forums are in no way as friendly as the Ubuntu Forums :(.

Andrew

Hi Andrew.

I think my card has some problem. When I used my brother's card, it runs.

I need to get it checked.

---

### Post by AdrianVeidt on 2010-03-27
> display: :0.0   screen: 0
Error creating VDPAU device: 1

If you installed the Nvidia driver, vdpauinfo, libvdpau and you rebooted afterwards (and you are actually using the nvidia driver) and you get that message, your hardware is broken. Time for a GT 220/230/240.

---

