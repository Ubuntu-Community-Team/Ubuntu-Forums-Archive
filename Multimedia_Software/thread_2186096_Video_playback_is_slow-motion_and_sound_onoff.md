---
title: "Video playback is slow-motion and sound on/off"
date: 2013-11-05
forum: Multimedia Software
---

### Post by NakiMum-NZ on 2013-11-05
[COLOR=#800080][I][B]_UPDATE WITH WORK AROUND 11 NOVEMBER 2013_
I converted the video in WinFF with preset options for DVD PAL Widescreen and video playback is smooth and sound is perfect. 
I know there is a solution somewhere, but for now this work around is the solution for me. A little inconvenient, but I'm not complaining. It takes me all of 5mins from start to finish.[/B][/I][/COLOR]



I've been Google-ing this issue to death. Have crashed my system a few times and had to do re-installs ](*,)

My problem is as follows (I hope it makes sense):
I have a Samsung Galaxy Note 3 and takes heaps of photos and videos on it. Then I have a HP Pavilion dm1 Notebook with Ubuntu 13.10 on. 
The photos taken on the SG work just fine with Ubuntu. It's the video that's driving me insane.
Playback on Google+ and YouTube is just fine. But on the laptop it all goes to bits. I've tried using SMPlayer, VLC, Videos but it just doesn't work properly.
In some the sound works just fine, in others the sound doesn't work. The video in all of them either freeze and sound continues to play or the video playback is in slow motion. 
I'm not too much of a Linux-noob, but am still on a learning curve. I do feel very comfortable with command line.
As would be this issue doesn't exist on Windows, but please, please don't make me use Windows!!! I'm a true-blooded geek and love my Ubuntu-setup too much. \\:D/

---

### Post by olli-sylvanne on 2013-11-07
Had exactly same problems on my ASUS eeePC. Then deleted Rhythmbox music player and all problems vanished. Selected ALSA on SMPlayer. 
I am a beginner, so cannot be sure if this was the real reason. Anyway, all works fine, now even when I connect the headset, sound stops from the loudspeakers, which was not the case before.

---

### Post by NakiMum-NZ on 2013-11-07
> **olli-sylvanne said:**
> Had exactly same problems on my ASUS eeePC. Then deleted Rhythmbox music player and all problems vanished. Selected ALSA on SMPlayer. 
I am a beginner, so cannot be sure if this was the real reason. Anyway, all works fine, now even when I connect the headset, sound stops from the loudspeakers, which was not the case before.

Thanks, I tried that. Now we're down to sound playing but video "paused". In SMPlayer I tried all the video option but it still stayed stuck

---

### Post by papibe on 2013-11-07
Hi Snowflake_NZ.

Could you paste what is says in 'VLC -> Tools -> Codec Information' (while trying to play one of the problematic videos)?

Also, could you open a terminal run these commands and post the results?
```
lsb_release -a

sudo lshw -C cpu | grep product

lspci -nnk | grep -iA3 vga
```
Regards.

---

### Post by NakiMum-NZ on 2013-11-07
> **papibe said:**
> Hi Snowflake_NZ.

Could you paste what is says in 'VLC -> Tools -> Codec Information' (while trying to play one of the problematic videos)?

Also, could you open a terminal run these commands and post the results?
```
lsb_release -a

sudo lshw -C cpu | grep product

lspci -nnk | grep -iA3 vga
```
Regards.

Hi

VLC codec information -> see screenshot 
[IMG]http://ubuntuone.com/35GXF1ct3Y2ep4g0MNR9w0[/IMG]



As for the terminal outputs, here they are 
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.10
Release:	13.10
Codename:	saucy
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ sudo lshw -C cpu | grep product
[sudo] password for nakimum: 
       product: AMD E-450 APU with Radeon(tm) HD Graphics
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ lspci -nnk | grep -iA3 vga
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320] [1002:9806]
	Subsystem: Hewlett-Packard Company Device [103c:3387]
	Kernel driver in use: fglrx_pci
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio [1002:1314]
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$

---

### Post by papibe on 2013-11-07
Thanks.

That's a full HD video. In order to play it smoothly you need to use video hardware acceleration from your video card.

I'm no expert on AMD cards, but it seems your card may support it.

Let's check if you have the necessary libraries. Could you post the results of these commands?
```
apt-cache policy libva1

vainfo
```
Regards.

---

### Post by NakiMum-NZ on 2013-11-07
> **papibe said:**
> Thanks.

That's a full HD video. In order to play it smoothly you need to use video hardware acceleration from your video card.

I'm no expert on AMD cards, but it seems your card may support it.

Let's check if you have the necessary libraries. Could you post the results of these commands?
```
apt-cache policy libva1

vainfo
```
Regards.

I've got little notebook that packs a punch. Now that I've install Ubuntu and completely removed Windows it kick butt :biggrin:

Anyway back to the problems at hand, here's the output:
PS I had to install vainfo first, but it installed without errors

nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ apt-cache policy libva1
libva1:
  Installed: 1.1.1-3
  Candidate: 1.1.1-3
  Version table:
 *** 1.1.1-3 0
        500 [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) saucy/main amd64 Packages
        100 /var/lib/dpkg/status
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ vainfo
libva info: VA-API version 0.33.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$

---

### Post by papibe on 2013-11-07
Thanks.

'libva1' is installed, but since 'vainfo' is reporting an error something is missing or mis configured.

The support for libva1 comes from  'xvba-va-driver'. Check if it is installed by running:
```
apt-cache policy xvba-va-driver
```
If it's not, you can install it like this:
```
sudo apt-get install xvba-va-driver
```
If you need to install it, run 'vainfo' again to see if that fixed it.

Let us know how it goes.
Regards.

---

### Post by NakiMum-NZ on 2013-11-07
> **papibe said:**
> Thanks.

'libva1' is installed, but since 'vainfo' is reporting an error something is missing or mis configured.

The support for libva1 comes from  'xvba-va-driver'. Check if it is installed by running:
```
apt-cache policy xvba-va-driver
```
If it's not, you can install it like this:
```
sudo apt-get install xvba-va-driver
```
If you need to install it, run 'vainfo' again to see if that fixed it.

Let us know how it goes.
Regards.

Firstly, thank you for bearing with me.

Here's the output of vainfo. Had to install xvba-va-driver and restart. There is a marked improvement on the video. Very pixelated, but it actually plays abit so we're getting there.

nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$ vainfo
libva info: VA-API version 0.33.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/x86_64-linux-gnu/dri/fglrx_drv_video.so
libva info: Found init function __vaDriverInit_0_32
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.33 (libva 1.1.1)
vainfo: Driver version: Splitted-Desktop Systems XvBA backend for VA-API - 0.7.8
vainfo: Supported profile and entrypoints
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
nakimum@nakimum-HP-Pavilion-dm1-Notebook-PC:~$

---

### Post by papibe on 2013-11-07
Great.

Now make sure you have set the acceleration on VLC. Go to:
```
VLC -> Preferences -> Inputs & Codecs
```
and make sure 'Use GPU accelerated decoding' is checked.

Restart VLC, and let us know how it went.
Regards.

---

### Post by NakiMum-NZ on 2013-11-07
> **papibe said:**
> Great.

Now make sure you have set the acceleration on VLC. Go to:
```
VLC -> Preferences -> Inputs & Codecs
```
and make sure 'Use GPU accelerated decoding' is checked.

Restart VLC, and let us know how it went.
Regards.

Hi, did all that and the video still "jumps". Plays 1 sec then jumps to around 13sec mark etc.

---

### Post by Yellow Pasque on 2013-11-09
If 3D performance is not your primary aim, then I suggest using the open-source driver. Using this PPA will give you vdpau acceleration: [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
You'll also need this for dynamic power management: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by NakiMum-NZ on 2013-11-09
> **Temüjin said:**
> If 3D performance is not your primary aim, then I suggest using the open-source driver. Using this PPA will give you vdpau acceleration: [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
You'll also need this for dynamic power management: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

Hi there
followed the above 2 steps. Restarted the laptop. The results are as follows:
SMPlayer -> sound is fine, video freezes completely
VLC -> sound is fine, video plays for about 2-3 seconds and skips a few then freezes a bit then plays again for 2-3 sec
Video -> video plays fantastically, but sound is on/off

---

### Post by Yellow Pasque on 2013-11-09
But did you remove the proprietary driver?

---

### Post by NakiMum-NZ on 2013-11-09
> **Temüjin said:**
> But did you remove the proprietary driver?

Hi there
I uninstalled proprietary drivers using this guide [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection#Problem:_Need_to_purge_-fglrx) and it's not working. Did a reboot, shutdown.

In Software Sources the following drivers are active and in use
[http://ubuntuone.com/5E9RNM7nIWuvArGW9zr9Au](http://ubuntuone.com/5E9RNM7nIWuvArGW9zr9Au)

Video is jerky, sound is on/off

---

### Post by NakiMum-NZ on 2013-11-10
I have found a work around (I know this isn't the ideal solution, but hey it works).
I've got WinFF installed (none of the other converters work for this well), converted the video to .mpg using the preset option for DVD PAL Widescreen and TADA! I have a smooth video and continuous sounds.

So now I'm thinking that this could be a possible codec issue somewhere between the Samsung Galaxy Note 3 and Ubuntu. I'm not fussed anymore, I got it figured and I don't mind using the work around. 
I still get to brag with my Ubuntu flexibilty and support :P

Thanks to all that have helped so far.

---

