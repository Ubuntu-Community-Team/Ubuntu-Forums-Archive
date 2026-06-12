---
title: "NVidia 8400M - full frame?"
date: 2013-12-17
forum: Multimedia Software
---

### Post by bugbear6502 on 2013-12-17
I have searched the web prior to posting, and I can find several posts (in various *nix versions) about the NVidia
8400M having trouble with full frame flash, which means (notably) Youtube, back in 2010-2012.

In my searching I didn't find a definitive cure (just a load of "try this" style posts).

Symptoms/report:

When watching youtube, if I go "fullscreen" it's very flickery to start with, then locks solid. Power sequence
is only way out.

Video card is essentially "good" (and quite fast); e.g. Stellarium runs at 59 f/s, fullscreen,

Machine;
```

lshw -c video
       description: VGA compatible controller
       product: G86M [GeForce 8400M GS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fd000000-fdffffff memory:f4000000-f7ffffff memory:fa000000-fbffffff ioport:ef00(size=128) memory:fea00000-fea1ffff


dpkg -l | grep nvidia

nvidia-319-updates                            319.60-0ubuntu1                            amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-settings-319-updates                   319.60-0ubuntu1                            amd64        Tool for configuring the NVIDIA graphics driver
```

So - is this (old) problem still unsolved?

  BugBear

---

### Post by bugbear6502 on 2013-12-17
I note that Geforce have a newer driver available;

[http://www.geforce.com/drivers/results/69372](http://www.geforce.com/drivers/results/69372)

331.20 vs my 319.60

 BugBear

---

### Post by SeijiSensei on 2013-12-17
First, make sure that the VDPAU software is installed; check to see if there is a file called /usr/lib/vdpau/libvdpau_nvidia.so.1 on your system.  It should have been installed along with the NVIDIA driver.  This software provides support for hardware acceleration of certain types of video files, particularly ones distributed in the H.264 format.

Next, open a YouTube video in full-screen, right-click on the image and pick Settings.  Is the "Enable Hardware Acceleration" box checked?  If not, check it, then close and reopen the browser.  Try the video again and see if it runs more smoothly.

---

### Post by bugbear6502 on 2013-12-17
> **SeijiSensei said:**
> First, make sure that the VDPAU software is installed; check to see if there is a file called /usr/lib/vdpau/libvdpau_nvidia.so.1 on your system.  It should have been installed along with the NVIDIA driver.  This software provides support for hardware acceleration of certain types of video files, particularly ones distributed in the H.264 format.

Next, open a YouTube video in full-screen, right-click on the image and pick Settings.  Is the "Enable Hardware Acceleration" box checked?  If not, check it, then close and reopen the browser.  Try the video again and see if it runs more smoothly.


VDPAU:

```


ll  /usr/lib/vdpau/libvdpau_nvidia.so.1
lrwxrwxrwx 1 root root 55 Nov 14 16:46 /usr/lib/vdpau/libvdpau_nvidia.so.1 -> /etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1
ll /etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1
lrwxrwxrwx 1 root root 54 Nov 14 16:46 /etc/alternatives/x86_64-linux-gnu_libvdpau_nvidia.so.1 -> /usr/lib/nvidia-319-updates/vdpau/libvdpau_nvidia.so.1
ll /usr/lib/nvidia-319-updates/vdpau/libvdpau_nvidia.so.1
lrwxrwxrwx 1 root root 25 Oct  2 16:18 /usr/lib/nvidia-319-updates/vdpau/libvdpau_nvidia.so.1 -> libvdpau_nvidia.so.319.60
ll /usr/lib/nvidia-319-updates/vdpau/libvdpau_nvidia.so.319.60
-rw-r--r-- 1 root root 1813416 Oct  2 16:19 /usr/lib/nvidia-319-updates/vdpau/libvdpau_nvidia.so.319.60

```

Settings were fine. And, for a 30 second test, full screen TouTube was fine. :confused: I'll leave a longer test running.

Thanks for your help so far.

 BugBear

---

### Post by bugbear6502 on 2013-12-17
Damn. Ran the video again just after posting the above.

Flickered immediately, sound OK, for around 2 seconds
Then blank screen, sound OK.
Then the sound stopped.

Machine then immune to anything I tried except power button.

 BugBear

---

### Post by mc4man on 2013-12-17
Maybe there is some other factor(s)??
I've still got an 8400m laptop here, while old it can play youtube vids @ fs, with or without full hw acceleration
( vdpau support in 8400m is remedial at best, though can help a bit  with yt vids

As far as hwaccel with flash using Firefox - maybe ck. that you're actually getting both rendering & decoding
Open a yt vid (non fullscreen so it plays), right click in vid window > stats for nerds
It should show ' accelerated  video decoding', see screen for example

If not & you wish to see if it helps - in terminal
```
sudo mkdir -p /etc/adobe
```
```
echo "EnableLinuxHWVideoDecode=1" | sudo tee /etc/adobe/mms.cfg
```
Then start up firefox & see

---

### Post by bugbear6502 on 2013-12-18
> **mc4man said:**
> Maybe there is some other factor(s)??
I've still got an 8400m laptop here, while old it can play youtube vids @ fs, with or without full hw acceleration
( vdpau support in 8400m is remedial at best, though can help a bit  with yt vids

As far as hwaccel with flash using Firefox - maybe ck. that you're actually getting both rendering & decoding
Open a yt vid (non fullscreen so it plays), right click in vid window > stats for nerds
It should show ' accelerated  video decoding', see screen for example

If not & you wish to see if it helps - in terminal
```
sudo mkdir -p /etc/adobe
```
```
echo "EnableLinuxHWVideoDecode=1" | sudo tee /etc/adobe/mms.cfg
```
Then start up firefox & see

Thanks - I shall try this when I get home (I'm posting from work, in the UK).

It's good to hear "*I've still got an 8400m laptop here, while old it can play youtube vids @ fs, with or without full hw acceleration*"

What Linux/Driver versions do you have?

 BugBear

---

### Post by bugbear6502 on 2013-12-18
Interesting - I tried and failed to take a screenshot with both Gimp and Shutter; in both cases the part of the screenshot that was the video was just a window onto the live, still playing firefox!!

So I'll just have to key it:

10 stage fps, 24 video fps, 63 dropped, 0kbps,
accelerated video rendering, software video decoding,
NaN db, 1 audio factor.

I should point out that I'm using 4 desktops under LXDE/Openbox, which may be relevant.

But the failure is quite variable - now I'm trying to TEST it, I can sometimes (but not always...) run full screen for a coupla' minutes. I suspect amount of interaction may be a factor.

 BugBear

---

### Post by bugbear6502 on 2014-02-25
I've found a site that REALLY breaks my Flash;

[http://www.historic-maps.norfolk.gov.uk/mapexplorer/](http://www.historic-maps.norfolk.gov.uk/mapexplorer/)

Consistent and horrible full screen flashing.

 BugBear

---

