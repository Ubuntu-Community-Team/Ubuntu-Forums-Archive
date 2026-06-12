---
title: "HDMI Audio Devices Missing"
date: 2011-08-31
forum: Multimedia Software
---

### Post by lucasjung on 2011-08-31
I'm setting up an HTPC and I'm not getting any audio out through the HDMI connection.  I get video through the HDMI, and I get audio if I plug headsets into the front panel, just not audio through HDMI.

I found several sets of directions posted on these forums and elsewhere, but they all assume that the HDMI audio device shows up when you run commands like aplay, but in my case they don't.

Ubuntu Version:  Ubuntu 10.04.3 LTS
Kernel Version:  2.6.32-33-generic x86_64
CPU: Intel Core i3-2100T
Motherboard: Intel DH67GD

lspci | grep Audio
```

00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 05)
```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
Based on what I've seen in other places, the above list should have one or two more cards, one of which would be HDMI.

aplay -L
```

pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, HDA Generic
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
```
Likewise, there should be additional entries for Intel HDMI.

EDIT: Almost forgot to mention: HDMI audio is enabled in BIOS.

---

### Post by BicyclerBoy on 2011-08-31
You need user-space alsa drivers 1.0.24 or later.
speaker-test reports the user-space alsa version.

With 10.04 you have to add a 3rd party ppa.
iQuik audio launchpad ppa
[https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)

With Sandybridge CPU/GPU & chipset you may need to update the kernel to the 11.04 natty kernel.

---

### Post by lucasjung on 2011-08-31
Thank you very much for helping me!

Speaker-test reports that my alsa drivers are version 1.0.22, so I'll try that PPA when I get home from work this evening.

How would you recommend that I upgrade to the 11.04 kernel if it comes to that?  Is it wise to pull packages from the repository of a different version?  Would it be smarter to just upgrade to 11.04?  I went with 10.04 because of the LTS: I don't want to have to upgrade this box very often, since upgrades tend to break lots of things and that would leave my family without TV until I could fix it, but I'll move to 11.04 if it's the best way to fix this problem.

---

### Post by BicyclerBoy on 2011-08-31
I'm using 10.04 lts for HTPC for the same reasons.
I would not recommend 11.04 natty for HTPC setup.
10.10 is basically same as 10.04.3.

Kernel updates are possible from launchpad ppa, this could/would break any analogue tuners & LIRC IR remotes.

I would just buy a nVidia GT430 or GT220/240/520. The required driver is easy to get & the h/w works very well. (GT520 is just adequate)
With the video driver ppa & alsa 1.0.24 it will all just work.

My guess is the intel sandybridge solution will work out of the box in 12.04 LTS.

---

### Post by lucasjung on 2011-08-31
> **BicyclerBoy said:**
> Kernel updates are possible from launchpad ppa, this could/would break any analogue tuners & LIRC IR remotes.
I don't have an analog tuner, but I do have an internal IR receiver that I plan on configuring with LIRC. Is it something inherent to the particular kernel version that would break LIRC, or would it break because the kernel is out of phase with the rest of the system? In other words: would LIRC break if I were to install 11.04 in its entirety, or would it only break if I kept 10.04 and upgraded the kernel via ppa?
 
Although I would prefer the stability of LTS, I'm currently leaning towards switching to 11.04 because there are now three things I would need to upgrade via ppa: alsa and the kernel to get HDMI working, plus firefox in order to be able to use [adblock video]("http://adblockvideo.com/"). However, if 11.04 would break LIRC, then I would have to stick with 10.04.
 
> **BicyclerBoy said:**
> I would just buy a nVidia GT430 or GT220/240/520. The required driver is easy to get & the h/w works very well. (GT520 is just adequate)
With the video driver ppa & alsa 1.0.24 it will all just work.
That's not really an option for me, unfortunately. I'm already slightly over-budget for this thing, and even if I could afford a video card it would create crowding issues in my case (I have a slot for it, but it would cause serious cable-management problems).
 
I am a little confused about the need for ppas at all, though. I've seen at least two posts by people who had problems with HDMI, but not the problem I'm having:
[http://ubuntuforums.org/showthread.php?t=1470812](http://ubuntuforums.org/showthread.php?t=1470812)
[http://www.linuxjunkie.com/2010/10/18/ubuntu-10-04-lucid-5-1-hdmi-audio-intel-g45-boxee-5-1-hdmi-audio/](http://www.linuxjunkie.com/2010/10/18/ubuntu-10-04-lucid-5-1-hdmi-audio-intel-g45-boxee-5-1-hdmi-audio/)
They're both using sandybridge, and as you can see from their aplay outputs, they both have the HDMI device, which I do not. As far as I can tell, they were this way with 10.04 out of the box. Certainly, neither of them said anything about updating alsa or the kernel in order to get the HDMI device to appear. I even saw one post (can't find a link right now) where the guy basically said that if aplay doesn't list an HDMI device, he doesn't know how to fix it, and he was also using 10.04. That's why I'm so confused: what is the difference between their systems and mine, that their HDMI device shows up and mine doesn't?  If I can just get my HDMI device to show up like theirs, then I can follow the rest of their steps and get HDMI working.

---

### Post by BicyclerBoy on 2011-08-31
I don't have your system to expt with.
You can try the live DVD version of 11.04..

I would not contemplate building a HTPC with intel GPU solution because:
intel GPU support (SB & IB) is developing.
intel HDMI/DP seems to be broken more than it works.
VA-API is 2-3 yrs behind VDPAU.
nVidia supports their products.

The GT520 is 1/3-1/4 the cost of the Intel CPU/GPU. 1/2 price of 2TB HDD, <2x price of DVD drive. (1/2 tank of petrol/gasoline)

Many LIRC drivers have been rewritten &  gone into the kernel...your remote may not need Lirc, it could just work or it may never.

The kernel updates/upgrades idea was directed at maximising the SB graphics performance.

The alsa 1.0.24 user-space is generally considered a good starting point.

Your listed audio HDA audio device most likely is your HDMI audio device but alsa is not enumerating more than one device.

The first link: the OP never identifies the mobo chipset/CPU (AFAICT)
The 2nd link: is using a Asus p5 P45/G45 chipset so core2duo LGA775 CPU & you do not need to remove pulse-audio.

---

### Post by lucasjung on 2011-09-01
> **BicyclerBoy said:**
> 
I would not contemplate building a HTPC with intel GPU solution because...
I'm really wishing I had talked to you before starting this project, because everything I found while searching online back then was either "works out of the box" or "works if you follow these simple steps."

> **BicyclerBoy said:**
> The GT520 is 1/3-1/4 the cost of the Intel CPU/GPU. 1/2 price of 2TB HDD, <2x price of DVD drive. (1/2 tank of petrol/gasoline)
That's all true (except the gas part--gas must be REALLY expensive where you live, because I have a big tank and filling it up once costs about the same as one of those cards).  The problem isn't that those cards are expensive (they're certainly not), it's that I've no money left for one right now.  If I had planned for one from the beginning, I could have gone with a slightly less expensive SSD and maybe started out with less RAM, but I've already spent that money.  Normally I'd only have to wait a few weeks and I'd be able to go out and buy one, but with a slew of birthdays coming up, followed by Christmas, I have to start saving for gifts, and that means I won't be able to buy one until January at the very earliest.  At that point, 12.04 will be just around the corner and I'd be inclined to just wait and see if it fixes everything.

> **BicyclerBoy said:**
> Many LIRC drivers have been rewritten &  gone into the kernel...your remote may not need Lirc, it could just work or it may never.
I've got a Logitech Harmony One, and I've heard mostly good things about it.  Do you happen to have a Logitech remote?  Or is it the receiver that matters when it comes to drivers?

> **BicyclerBoy said:**
>  The kernel updates/upgrades idea was directed at maximising the SB graphics performance.
Ah...in that case, I won't bother with it unless I experience significant graphics problems.  So far it's been fine.


> **BicyclerBoy said:**
>  The alsa 1.0.24 user-space is generally considered a good starting point.
I just upgraded alsa to 1.0.24 using the PPA you linked to.  Thanks!
The outputs from aplayer -l and aplayer -L did not change at all.  However, the GUI mixer now has more than one option.  It used to just list "HDA Intel PCH (alsa mixer)," but now it lists all of the following:
[LIST]
[*]HDA Intel PCH (alsa mixer)
[*]Intel ID 2805 (OSS mixer)
[*]Playback: Internal Audio Analog Stereo (PulseAudio mixer)
[*]Capture: Monitor of Internal Audio Analog Stereo (PulseAudio mixer)
[*]Capture: Internal Audio Analog Stereo (PulseAudio mixer)
[/LIST]

Selecting different sound cards from the pull-down doesn't seem to affect output at all: the headphone jack continues to work, HDMI audio and S/PDIF never work.  I don't think that any of the other stuff I linked to is going to help me, since my aplayer outputs don't match up with their methods.  Do you have any suggestions?  Worst case scenario, I'll rig something up using the analog outputs on the back and hope that HDMI audio gets fixed in 12.04.  If it doesn't, by then I'll have plenty of money to go out and buy a decent video card.

Thank you for putting in so much time to help me out with this.

---

### Post by BicyclerBoy on 2011-09-01
US$1.90/L 95RON 4c less for 91 octane.

I've long given up on IR remotes..the HID keyboard is so much better with MythTV..

dmesg | grep HDMI

ls -al /proc/asound/

Have a play with
pavucontrol
But you should have similar to (4) audio devices analog digital & 2 HDMI..

Doing some more reading; does seem that a lot of sandy-bridge hdmi audio stuff went into kernel 2.6.39.
There is a launchpad ppa with oneiric-backport 3.0.0-8.11 kernel for lucid 10.04.
This was a natty-backport but that is history..

---

### Post by lucasjung on 2011-09-02
> **BicyclerBoy said:**
> US$1.90/L 95RON 4c less for 91 octane.
Good grief.  That's almost twice what it costs here.  That does explain why you would compare that video card to a half-tank while I thought it was closer to a full tank.

> **BicyclerBoy said:**
> I've long given up on IR remotes..the HID keyboard is so much better with MythTV..
I've got a Logitech diNovo Edge, and it's working beautifully for me so far, so if I can't get the IR to work it's not the end of the world.  It would sure be nice to have, though.  The xbmc interface is really optimized for remote, not mouse & keyboard.

> **BicyclerBoy said:**
> dmesg | grep HDMI
This doesn't return anything.


> **BicyclerBoy said:**
>  ls -al /proc/asound/
```
total 0
dr-xr-xr-x   5 root root 0 2011-09-02 00:23 .
dr-xr-xr-x 200 root root 0 2011-09-02 00:19 ..
dr-xr-xr-x   4 root root 0 2011-09-02 00:23 card0
-r--r--r--   1 root root 0 2011-09-02 00:23 cards
-r--r--r--   1 root root 0 2011-09-02 00:23 devices
-r--r--r--   1 root root 0 2011-09-02 00:23 hwdep
-r--r--r--   1 root root 0 2011-09-02 00:23 modules
dr-xr-xr-x   2 root root 0 2011-09-02 00:23 oss
lrwxrwxrwx   1 root root 5 2011-09-02 00:23 PCH -> card0
-r--r--r--   1 root root 0 2011-09-02 00:23 pcm
dr-xr-xr-x   2 root root 0 2011-09-02 00:23 seq
-r--r--r--   1 root root 0 2011-09-02 00:23 timers
-r--r--r--   1 root root 0 2011-09-02 00:23 version
```> **BicyclerBoy said:**
> Have a play with
pavucontrol
But you should have similar to (4) audio devices analog digital & 2 HDMI..
The only device that shows up under the Output Devices tab is "Internal Audio Analog Stereo."  The same device shows up under the Input Devices tab.  Under the Configuration tab, there are four options available from the pulldown:
[LIST]
[*]Analog Stereo Duplex
[*]Analog Stereo Output
[*]Analog Stereo Input
[*]Off
[/LIST]


> **BicyclerBoy said:**
> Doing some more reading; does seem that a lot of sandy-bridge hdmi audio stuff went into kernel 2.6.39.
There is a launchpad ppa with oneiric-backport 3.0.0-8.11 kernel for lucid 10.04.
This was a natty-backport but that is history..
Thanks, that's good to hear.  The 3.0 kernel also brings my wireless drivers out of staging and into mainstream, which might solve some of my other issues.  If I can't get things working under 10.04, I will probably try 11.04 and maybe even a kernel backport PPA.

---

### Post by lucasjung on 2011-09-03
I got it working!  I had some spare time today so I did a clean install of 11.04.  After that, aplay -l and aplay -L showed all of my devices properly.  Then I just followed the method described in this post:

[http://ubuntuforums.org/showthread.php?p=7328686#post7328686](http://ubuntuforums.org/showthread.php?p=7328686#post7328686)

In my case, I had two HDMI devices showing and only one of them produced sound from my speakers, and unlike the guy who posted the directions above, I had to use device 7 instead of 3.  Also, the only package I had to install was pavucontrol.  Point being, the directions work fine as long as you tailor them to your specific setup.

Bicyclerboy: Thank you very much for all of your help!  If it hadn't been for the info you provided about the kernel versions, I might never have tried 11.04 and would have been stuck using some cobbled-together setup tapping the analog outputs, at least until 12.04.

---

### Post by BicyclerBoy on 2011-09-03
That's a much cleaner solution than hacking/patching everything. Chances are there would have been a gotcha with some dependency..

Note that AFAIK there should only be one of these entries in /etc/pulse/default.pa
load-module module-alsa-sink device=hw:m,n
Pulse already enumerates the first device exposed by alsa & pulse only allows 2 in total.

---

### Post by lucasjung on 2011-09-03
I initially put in two, but realized that the second one wasn't doing anything for me and removed it in order to clean up the selection pull-down in the mixer GUI.

---

