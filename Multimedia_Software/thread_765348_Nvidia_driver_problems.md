---
title: "Nvidia driver problems"
date: 2008-04-24
forum: Multimedia Software
---

### Post by cky2k6 on 2008-04-24
I haven't ubuntu used for a while now, last release i ran was 7.04. I installed 8.04, but when i go into hardware drivers, i can't get the nvidia driver to work... it was already checked as enabled when i got there, which was odd, but it said it was not in use. i unchecked it, and rechecked it, and it told me to restart. however, the same issue was still there in that its still not using the driver. I tried installing the beta driver from nvidia's site, but its telling me to shut down x server... isn't that the windowing system? why the hell would nvidia ask me to shut that down? i'm a linux noob, so i have no idea what on earth is going on, and what to do...

---

### Post by windreiter on 2008-04-24
you have to shut down the x server (yes, the "windowing thing") for a clean installation of the driver.
Press Alt+Ctrl+F1, log in as root and run "/etc/init.d/gdm stop".

Go to the directory where the driver package is storeed and run "sh ./NVIDIA-and-so-on.run" (enter your correct driver package name.

After installing you can either reboot your machine or run "/etc/init.d/gdm start". It should load itself, or you can go there with pressing Alt+Ctrl+F7.

Good luck

---

### Post by warp99 on 2008-04-24
> **cky2k6 said:**
> I haven't ubuntu used for a while now, last release i ran was 7.04. I installed 8.04, but when i go into hardware drivers, i can't get the nvidia driver to work... it was already checked as enabled when i got there, which was odd, but it said it was not in use. i unchecked it, and rechecked it, and it told me to restart. however, the same issue was still there in that its still not using the driver. I tried installing the beta driver from nvidia's site, but its telling me to shut down x server... isn't that the windowing system? why the hell would nvidia ask me to shut that down? i'm a linux noob, so i have no idea what on earth is going on, and what to do...

Don't install the drivers from nvidia since it's a hassle and not needed. You  most likely do not have the restricted modules for 8.04 only for 7.04, therefore it going to say that you have the restricted drivers but for a different kernel.

To correct the problem open a terminal and first install the correct drivers for your kernel:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
```
issue a 'sudo reboot' to reload the kernel modules then you can enable nvidia in the restricted drivers manager and they should work. If not open a terminal and issue the following:
```
gksudo nvidia-settings
```
if nvidia-settings is not installed then:
```
sudo apt-get install nvidia-settings
```
you may have to enable the universe repositories to install. Now you can use nvidia-settings to make yourself a new xorg.conf that will support you video card by using the "X Server Display Configuration" and saving the file as "/etc/X11/xorg.conf" then reload the desktop (crtl+alt+backspace).

---

### Post by cky2k6 on 2008-04-24
I'm sorry if I was confusing in the first post, but this was a clean install, so I should have the 8.04 driver already installed. What strikes me odd, is that after the initial installation, I get a few weird errors that have some nvidia files and something about a bus. I remember I had errors with 7.10 as well, which was why I waited until 8.04 to install on my new system. At least this boots, 7.10 never even made it to desktop. 

windreiter, I figured out that I actually did have to close x after my post, but thanks for the script to shut down x server. I think the driver isn't ready for hardy though, as it told me it couldn't find a kernel, and it told me libdm was missing when it was certainly not... This sucks though, ever since I got my new pc I haven't been able to get linux working, ironically everything was working perfectly fine back when I had ati...

---

### Post by cor2y on 2008-04-24
Yep in the new kernel the hardware driver is not working  for nvidia.
In the -12 kernel i have restricted driver installed in -16 the diriver is selected but Not In Use according to hardware driver, trying the above method didn't work.

---

### Post by warp99 on 2008-04-24
If you had the restricted drivers running under 7.04 then the drivers are going to run under 8.04. You need to uninstall the nvidia drivers from nvidia and reinstall the restricted modules to get your system back in order. So issue the following:

First uninstall the drivers from nvidia:
```
 sudo ./NVIDIA-Linux-x86-169.12.pkg1.run --uninstall 
```
If that's not the correct nvidia installer version change yours to match, then reinstall the drivers for your running kernel:
```
sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx
```
issue a 'sudo reboot' to reload the correct drivers. Now don't trust the restricted drivers manager to see if the driver is loaded but issue the following:
```
cat /proc/driver/nvidia/version
```
if it returns a value like this:
> NVRM version: NVIDIA UNIX x86 Kernel Module  169.12
then your using the nvidia restricted drivers.

---

### Post by cky2k6 on 2008-04-24
> **cor2y said:**
> Yep in the new kernel the hardware driver is not working  for nvidia.
In the -12 kernel i have restricted driver installed in -16 the diriver is selected but Not In Use according to hardware driver, trying the above method didn't work.

thanks, what card are you using by the way? i'm using 8800gt sli, so maybe the driver doesn't support g92 properly yet? Kind of an interesting issue, hope maybe nvidia or someone from the developers can shed some light on this?

warp, again this is a clean install, nothing I am running has anything to do with 7.04, the driver that is provided with this kernel does not work.

---

### Post by gt_momo on 2008-04-24
I'm having the same problem with my 6600 GT and can't find any NVIDIA drivers in synaptic like I used to be able to in 7.10

---

### Post by gt_momo on 2008-04-24
I just figured it out.

I had to enable the third party software repositories in Synaptic and then install nvidia-glx-new.

Hope that helps.

---

### Post by cor2y on 2008-04-24
> **cky2k6 said:**
> thanks, what card are you using by the way? i'm using 8800gt sli, so maybe the driver doesn't support g92 properly yet? Kind of an interesting issue, hope maybe nvidia or someone from the developers can shed some light on this?

warp, again this is a clean install, nothing I am running has anything to do with 7.04, the driver that is provided with this kernel does not work.

I am using a 8600GTS and it was working in the beta version of hardy heron.
I had the "failed to initialize HAL" for the later kernels so i was keeping to version -12 but that got fixed with the latest slew of updates.

---

### Post by cky2k6 on 2008-04-24
thanks a bunch man, worked perfectly.

---

### Post by jtrink on 2008-04-24
wait a second! I have the exact same problem. I'm a super noob when it comes to linux. Which method actually worked?!?!?!

---

### Post by jtrink on 2008-04-24
bump

---

### Post by DarkYang on 2008-04-24
> **gt_momo said:**
> I just figured it out.

I had to enable the third party software repositories in Synaptic and then install nvidia-glx-new.

Hope that helps.

That worked perfectly for me, thanks. I'm using a Nvidia 7300gt.

---

### Post by Victormd on 2008-04-24
I've been having a really hard time with my 8800GT as well. I recently updated from Gutsy to Hardy. In gutsy, everything worked fine, just used Envy. After the update, I have full screen resolution (1440x900) but no 3D. Tried EnvyNG and several "HOW-TO's" to no success, Hardy would always boot into failsafe mode (low graphics mode). I'm wondering if this is because I upgraded directly from Gutsy to Hardy or if there is some work-around that I haven't tried. My graphics card is a XFX 8800GT 512MB...
I'm downloading the CDs now to try a fresh install to see what happens but really didn't want to install from scratch...

---

### Post by grover66 on 2008-04-24
Looks like to nvidia-glx-new package is not installed by default. Use the following line to install it;

```
sudo apt-get install nvidia-glx-new
```

Restart and you should be good.

Mike :)

---

### Post by locky28 on 2008-04-24
I've done a fresh install of hardy and I'm having the same problems. Reso is fine but no 3D acceleration.

when I run

```
sudo apt-get install nvidia-glx-new
```

I get this

```
locky@locky1:~$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate
locky@locky1:~$ 

```

AFAIK I have universe/multiverse enabled and the two third party sources ticked.

---

### Post by man_bash on 2008-04-24
Hi all, I am also having problems with my 8800 GT video card. When I try to "Enable" the restricted driver, after reboot the screen turns off and the computer has to be manually restarted. At the same time cloned output seems to work OK, with full resolution options, when the restricted 3D driver is not functioning. The same happened when I tried using envyng - monitor turns off at boot, computer stops responding to keyboard. I'd fix the issue by booting into recovery mode and run xfix option, or running >  dpkg-reconfigure xserver-xorg After xfix, if I choose to resume boot normally I see that the Nvidia proprietary driver is "[color="#00FF00"]In use[/COLOR]" but **NOT** "[color="#FF0000"]Enabled[/COLOR]" ](*,). I am totally confused at this moment. The only viable solution to the puzzle is that my power supply is not up to par, but I have a 500W PSU with 25 amps on a 12 volt rail, so that shouldn't really be a problem, given the rest of the system. Here's the system setup
Motherboard: DFI Infinity nF4x
CPU: AMD Turion ML-30
RAM: 2x1GB DDR400, one Kingston Value RAM and one Buffalo Value Select
Video card: EVGA GeForce 8800 GT 512 mb
HDDs: 320 GB WDC SATA (primary) + 250 GB Maxtor PATA
Optical: AOpen DVD burner
Sound: onboard
LAN: USB wireless on ZyDAS chip
PSU: 500W, 3.3V - 28A; 5V - 35A; 12V - 25A, Video card connected with a 6-pin power connector.
Hardy AMD64, fully updated
Kernel: 2.6.24-16-generic
So far I tried Nvidia's 169.12, beta 171.06, beta 171.08. 
If this may be kernel-driver incompatibility, how can install older kernel?

---

### Post by Victormd on 2008-04-24
> **grover66 said:**
> Looks like to nvidia-glx-new package is not installed by default. Use the following line to install it;

```
sudo apt-get install nvidia-glx-new
```

Restart and you should be good.

Mike :)

Mine isn't a fresh install. I think that upgrading from gutsy without removing the previous video driver messed things up. My card didn't even show up in the restricted drivers window.
I've tried installing all versions of the nvidia driver (glx, glx-new, glx-legacy) and none of them worked, not even envyNG or the driver downloaded directly from the Nvidia site. I've reached a point where it's faster to format and do a fresh install...

But you're right, installing the nvidia-glx-new in Hardy (fresh install) should get the 8800gt working with no problems.

[B][COLOR="Red"]UPDATE:[/COLOR]
[COLOR="Blue"]Fresh install of Hardy (image downloaded today - 04/24/08 ) was flawless and detected the 8800GT with no problem.
Tip: before any attempt to install, select all sources in the repositories (system>administration>software sources) then reload (or type sudo apt-get update in the terminal) and reboot. This will "fix" the restricted drivers issue (initially the driver is marked but not in use) and you'll be able to select and install from there with no problem at all!![/COLOR][/B]

---

### Post by man_bash on 2008-04-25
> **Victormd said:**
> lx-new in Hardy (fresh install) should get the 8800gt working with no problems.

[B][COLOR="Red"]UPDATE:[/COLOR]
[COLOR="Blue"]Fresh install of Hardy (image downloaded today - 04/24/08 ) was flawless and detected the 8800GT with no problem.
Tip: before any attempt to install, select all sources in the repositories (system>administration>software sources) then reload (or type sudo apt-get update in the terminal) and reboot. This will "fix" the restricted drivers issue (initially the driver is marked but not in use) and you'll be able to select and install from there with no problem at all!![/COLOR][/B]

Odd. I just fresh-installed Hardy. Enabling the restricted driver downloads the nvidia-glx-new package.

---

### Post by paulstaf on 2008-04-25
I did the second line of what warp99 said:

sudo apt-get install --reinstall linux-restricted-modules-$(uname -r) nvidia-glx

Then mine came up perfect after the reboot.  Only did the one line though.

Thanks!

---

### Post by MatthewAPeters on 2008-05-03
Cross post: [HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron]("http://ubuntuforums.org/showthread.php?t=780777")

Hope this helps someone else.

---

