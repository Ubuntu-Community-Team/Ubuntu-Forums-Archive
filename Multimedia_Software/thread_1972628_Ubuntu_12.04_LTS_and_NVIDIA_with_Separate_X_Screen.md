---
title: "Ubuntu 12.04 LTS and NVIDIA with Separate X Screens"
date: 2012-05-03
forum: Multimedia Software
---

### Post by Einder on 2012-05-03
I've been running 12.04 LTS for a few days now with no issues. I have a secondary Monitor and wanted to run a separate x screen for watching videos and other miscellaneous stuff. The problem I'm having, isn't so much that it's not working, because I do get the secondary screen using the NVIDIA-Settings. However, my mouse is an X instead of the pointer and I can't do anything on the second screen. It also breaks compiz and I would prefer to have it working as I use the cube, which breaks on both screens. Twinview unfortunately isn't able to do what I would like, is there anyway to get the separate x screens fully working?

---

### Post by papibe on 2012-05-03
Hi Einder.

It look like you have conflicts between Unity and Compiz.

Take a look at this [tutorial]("https://help.ubuntu.com/community/CompositeManager"). Although I don't see a section for 12.04, all 11.10 tips should work.

If you have any problem with the tutorial, post a question in this support [thread]("http://ubuntuforums.org/showthread.php?t=1892851").

Regards.

---

### Post by Einder on 2012-05-04
> **papibe said:**
> Hi Einder.

It look like you have conflicts between Unity and Compiz.

Take a look at this [tutorial]("https://help.ubuntu.com/community/CompositeManager"). Although I don't see a section for 12.04, all 11.10 tips should work.

If you have any problem with the tutorial, post a question in this support [thread]("http://ubuntuforums.org/showthread.php?t=1892851").

Regards.

The problem isn't compiz itself. That I know how to use. The problem I'm having is with setting up the separate x screens. I use nvidia-settings and get two screens like I want, however I can't do anything at all on the second screen. All I get is the default background on both screens and one working screen.

---

### Post by papibe on 2012-05-04
I see.

Could you post the content of these 2 files?
```
/var/log/Xorg.0.log

/etc/X11/xorg.conf
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by Einder on 2012-05-04
> **papibe said:**
> I see.

Could you post the content of these 2 files?
```
/var/log/Xorg.0.log

/etc/X11/xorg.conf
```Please paste them separately here: [http://paste.ubuntu.com/](http://paste.ubuntu.com/), and then post back the links here.

Regards.

[http://paste.ubuntu.com/966850/](http://paste.ubuntu.com/966850/)
[http://paste.ubuntu.com/966854/](http://paste.ubuntu.com/966854/)

The first one is the log, the second one is the .conf, though it's not currently set up for dual screens because I couldn't get it working.

---

### Post by papibe on 2012-05-04
Thanks.

Everything look OK, since it's just one monitor.

Are you able to set up separate screens with no Xinerama? (that's the way I use it, btw). I would start by taking Xinerama out of the equation.

To do that, first backup your conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then run 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```
Set up the other monitor as a separate X screen, and then press 'Save to X Configuration File'.

Restart.

BTW, maybe you are looking for Xinerama and Twinview (if so take a look at [this]("https://help.ubuntu.com/community/XineramaHowTo"))

Regards.

---

### Post by *M* on 2012-05-04
If that doesn't work try following this thread:
[http://ubuntuforums.org/showthread.php?t=1967980](http://ubuntuforums.org/showthread.php?t=1967980)

---

### Post by Einder on 2012-05-05
> **papibe said:**
> Thanks.

Everything look OK, since it's just one monitor.

Are you able to set up separate screens with no Xinerama? (that's the way I use it, btw). I would start by taking Xinerama out of the equation.

To do that, first backup your conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Then run 'Nvidia X Server Settings' as root:
```
gksudo nvidia-settings
```Set up the other monitor as a separate X screen, and then press 'Save to X Configuration File'.

Restart.

BTW, maybe you are looking for Xinerama and Twinview (if so take a look at [this]("https://help.ubuntu.com/community/XineramaHowTo"))

Regards.

That unfortunately, didn't work. Instead I'm still receiving the problem I had before where I get a screen with the default background that is unusable.

---

### Post by Einder on 2012-05-05
> ***M* said:**
> If that doesn't work try following this thread:
[http://ubuntuforums.org/showthread.php?t=1967980](http://ubuntuforums.org/showthread.php?t=1967980)

I tried these steps and though I could use terminal to force things onto the other screen, I can't grab an appropriate resolution and I don't have the top panel or anything. I'm wondering know if it's just a bug that I have to wait on.

---

### Post by carranty on 2012-05-16
Hi Einder,

I was just wondering if you managed to resolve this issue?  I'm also unable to use two x screens in 12.04 (i could in 10.04), I'm having the exact same issue as you.  I gave up trying to fix it a week or two ago and am using twinview, but I prefer seperate x screens.

---

### Post by Einder on 2012-05-16
> **carranty said:**
> Hi Einder,

I was just wondering if you managed to resolve this issue?  I'm also unable to use two x screens in 12.04 (i could in 10.04), I'm having the exact same issue as you.  I gave up trying to fix it a week or two ago and am using twinview, but I prefer seperate x screens.

Unfortunately no. I'm stuck but I figured give it a little while and see if anyone comes up with a solution.

---

### Post by papibe on 2012-05-16
Einder,

Could you post the result of these commands?
```
sudo lshw -C display

lspci -nn | grep -i vga

apt-cache policy nvidia-current

dpkg -l | grep -i nvidia
```
Regards.

---

### Post by Einder on 2012-05-16
> **papibe said:**
> Einder,

Could you post the result of these commands?
```
sudo lshw -C display

lspci -nn | grep -i vga

apt-cache policy nvidia-current

dpkg -l | grep -i nvidia
```Regards.

sure thing

sudo lshw -C display
```
  *-display               
       description: VGA compatible controller
       product: G86 [Quadro NVS 140M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)

```

lspci -nn | grep -i vga
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86 [Quadro NVS 140M] [10de:0429] (rev a1)
```

apt-cache policy nvidia-current
```
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
        100 /var/lib/dpkg/status

```

dpkg -l | grep -i nvidia
```
ii  nvidia-common                          1:0.2.44                                Find obsolete NVIDIA drivers
ii  nvidia-current                         295.40-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        295.33-0ubuntu1                         Tool of configuring the NVIDIA graphics driver

```

This is all of course without the second monitor hooked up atm. If you need me to hook that up and try to have it running the way I want it to as well, then let me know.

---

### Post by waperboy on 2012-05-28
I've also battled with this issue forever. In 10.04, I got it to work if I reluctantly turned off Compiz - which I ended up living with for good.

In 12.04, I get the same behavior as I did with Compiz enabled in 10.04. I tried switching to unity2d and turn off OpenGL in Compiz-settings-manager, but no go.

I have never come across a solution for the combination Nvidia proprietary drivers, Ubuntu with desktop effects, dual head separate X screens. And I don't believe it's possible anymore.

---

### Post by hansaplast on 2012-06-07
I'm having exactly the same issue (and drivers) except I'm using product: G92 [GeForce 8800 GTS 512]

So if you've found a sollution...

---

### Post by hansaplast on 2012-06-07
Ubuntu 12.04 now uses lightdm window manager as it previously used the gnome display manager (gdm).

My guess is that the "Separate X Screens" option in nvidia-settings works for gdm and isn't available (or not yet implemented) in lightdm. There is a bug in [launchpad]("https://bugs.launchpad.net/bugs/1002641") describing (almost) our issue. [Vote]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1002641/+affectsmetoo") for it to give it higher priority.

---

### Post by benny232391212 on 2012-06-30
Me too... I have the exactly same problem so makes me to see if I can stay on ubuntu or go to other linux packages...

Most worst situation.... back to Microsoft XP :(

---

### Post by chrisdew on 2012-07-19
Me too!  I've gone back to twin view for now.

---

### Post by VietCanada on 2012-07-26
My solution was to install Linux Mint Mate 13. I now have separate x-screens again. Mate appears to be Ubuntu 12 with gnome instead of unity. So I've lost nothing with the switch just got separate x-screens back again.

---

