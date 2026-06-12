---
title: "Having problem installing Mint, but it may be a general Linux issue"
date: 2019-07-12
forum: MINT
---

### Post by random9999 on 2019-07-12
I just spent weeks trying to install Linux Mint without success. Not sure if it's an issue specific to Mint. It may be for all Ubuntu or a Linux-wide issue. So I thought I'd ask here. Do I have to post my question in the not very active Mint forum? Yes, I've already gone to Linux Mint forums at forumslinuxmint.com. They haven't been able to help me finish the installation.

---

### Post by deadflowr on 2019-07-12
*Thread moved to **MINT***

Post your machine specs, as that can help figure out if maybe there is a trick or two to get it installed.

---

### Post by random9999 on 2019-07-12
What do you need exactly, because I'll have to write it down on paper, since I can't login to the actual OS. I can open a live session off the DVD. Do you need inxi -Fxz?

---

### Post by deadflowr on 2019-07-12
Machine model, cpu, gpu, and ram are usually a good start.

Also at what point does the installation fail?

---

### Post by random9999 on 2019-07-12
CPU: Dual core Intel Core2 Duo E7400 64 bit
GPU: Nvidia GT200 (GeForce GTX260)
Mobo: EP45-UD3R
RAM: (free -m) Mem = 4033 Used = 208 free = 2975

I can only open a live session in 'recovery mode'. Not even a regular live session.

Got to where the installation is almost finished, and it tells you to restart to complete it. When I booted, I usually got black screen. The rest of the time I'd get the chance to type in my password, but the screen had red pixels all over, and pressing Enter after entering my password, nothing happened. then it goes to black screen. Been trying for days to figure out what's wrong. I think it's driver issues. There's 2 drivers available - Nvidia-340.107 and the 'nouveau' driver. Neither of them work. I downloaded PPA to see if there are more video drivers. Got the Nvidia-304. But when I choose it, I get error messages. Tried removing the other drivers, because I read that you can't have more than one installed at the same time, but I get error messages when I try and remove the others.

---

### Post by oldfred on 2019-07-12
You normally need nomodeset boot parameter both to install & first boot. But then once you install the correct nVidia driver, should not need nomodeset.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    
You should only install the newest driver that supports your nVidia card. Nvidia does freeze older drivers for older cards as newest driver for newest cards has features not supported by older cards.

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="http://www.geforce.com/drivers"]
[/URL]

---

### Post by random9999 on 2019-07-12
I spent 2 days going into the OS with nomodeset, without solving the problem. It still gave me black screen even with nomodeset.

Nvidia says the 340.107 driver is the correct driver, the one I need. [https://www.nvidia.com/Download/driverResults.aspx/135161/en-us](https://www.nvidia.com/Download/driverResults.aspx/135161/en-us) I already know that. Except that driver doesn't work. I get black screen. What do I do to fix this problem. Should I install the 304 driver instead? The opensource 'nouveau' driver doesn't work either.

> [COLOR=#000000]#What is installed[/COLOR]
[COLOR=#000000]dpkg -l | grep -i nvidia[/COLOR]
[COLOR=#000000]dkms status[/COLOR]
[COLOR=#000000]lsmod | grep nvidia [/COLOR]
[COLOR=#000000]# Shows standard repository versions, which is the same as[/COLOR]
[COLOR=#000000]System Settings, Software & Updates icon, Additional drivers tab, if ppa should then show the 381.[/COLOR]
[COLOR=#000000]ubuntu-drivers devices [/COLOR]

[COLOR=#000000]Remove normally deletes packages, but can save your settings or various hidden configurations.[/COLOR]
[COLOR=#000000]purge deletes packages and related settings[/COLOR]

[COLOR=#000000]You can only have one driver in kernel, see dkms above. So must purge older first.[/COLOR]


[COLOR=#000000]If you have installed any version, you must purge first, old will conflict with new as new install does not overwrite old version.[/COLOR]
[COLOR=#000000]sudo apt-get remove --purge nvidia-*[/COLOR]
[COLOR=#000000]sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms[/COLOR]
[COLOR=#000000]This may not exist, so if error that would be ok[/COLOR]
[COLOR=#000000]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup [/COLOR]
[COLOR=#000000]sudo ubuntu-drivers devices[/COLOR]
[COLOR=#000000]If you just want default version - recommended one[/COLOR]
[COLOR=#000000]sudo ubuntu-drivers autoinstall[/COLOR]
[COLOR=#000000]Or you manually choose any in list.[/COLOR]
[COLOR=#000000]sudo apt-get install nvidia-XXX[/COLOR]

When I type dpkg -l | grep -I nvidia I don't get anything useful. I get 
> ii nvidia-prime applet      1.0.7
all     An applet for NVIDIA Prime

I don't know what bumblebee is or if I have it. How do I purge everything. Purge commands aren't working for me. I don't think they're getting purged, because they're still there when I reboot. I think I need to purge the nvidia drivers and purge the nouveau driver and start over downloading the PPA. Is that correct? What is the EXACT code I need to enter in terminal. Is this it?:


[COLOR=#000000]sudo apt-get remove --purge nvidia-*[/COLOR]
[COLOR=#000000]sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms
[/COLOR]sudo apt-get purge xorg.conf

[COLOR=#000000]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup [/COLOR]
[COLOR=#000000]sudo ubuntu-drivers devices[/COLOR]


[COLOR=#000000]sudo apt-get install nvidia-304
[/COLOR]
Or is it this: 

[COLOR=#000000]sudo apt-get remove --purge nvidia-*[/COLOR]
[COLOR=#000000]sudo apt-get purge nvidia* bumblebee primus bbswitch-dkms[/COLOR]
sudo apt-get purge xorg.conf

[COLOR=#000000]sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup [/COLOR]
[COLOR=#000000]sudo ubuntu-drivers devices[/COLOR]


[COLOR=#000000]sudo apt-get install nvidia-340[/COLOR]

---

### Post by oldfred on 2019-07-12
Do not know about Mint, but 304 is not supported in Ubuntu anymore.
Doubt if you need bumblebee as that is for laptops with switchable graphics.

I have GT620, but use nouveau for most of my installs. Cannot tell difference between that and installing nVidia driver. I did not think I had nVidia in this install, but now Ubuntu autoinstalls it with some of the newest installers if you check install proprietary drivers.
```
fred@bionic-z97:~$ dkms status
nvidia, 390.116, 4.15.0-52-generic, x86_64: installed
nvidia, 390.116, 4.15.0-54-generic, x86_64: installed

```

---

### Post by random9999 on 2019-07-12
This is what I get for dkms status.

> dkms status:
line 170: /usr/bin/nproc: Input/output error

What does that even mean? I'm not a Linux expert. I don't know what's wrong. Most of the time when I enter a command which is supposed to solve a problem, or just tell me what problem I have, I get errors, and I don't know why.

edit: If this isn't specifically a Mint issue, could we move it back to the main forum? This forum is deserted.

---

### Post by oldfred on 2019-07-12
While Mint may be based on Ubuntu it is not Ubuntu.
Main forum is for Ubuntu. 
Do not know differences with Mint vs Ubuntu.

But those that use Mint should be looking in Mint sub-forum or use Mint's own forum.

But your issues seem related to some underlying issue, as I would expect dkms to be the same, but again do not know what changes Mint has done.

---

### Post by random9999 on 2019-07-24
> **oldfred said:**
> While Mint may be based on Ubuntu it is not Ubuntu.
Main forum is for Ubuntu. 
Do not know differences with Mint vs Ubuntu.

But those that use Mint should be looking in Mint sub-forum or use Mint's own forum.

But your issues seem related to some underlying issue, as I would expect dkms to be the same, but again do not know what changes Mint has done.

I don't care if it's Mint or not. I just want to install Linux on the computer. If a different distro has a solution, I'd be happy to know that. This subforum is completely dead. How am I supposed to find out if there's an answer if I'm stuck here.

---

### Post by uRock on 2019-07-24
> **random9999 said:**
> I don't care if it's Mint or not. I just want to install Linux on the computer. If a different distro has a solution, I'd be happy to know that. This subforum is completely dead. How am I supposed to find out if there's an answer if I'm stuck here.

The people who deal with Mint frequently likely skim this sub-forum. You can also try Mint's IRC ##linuxmint or their forums.

Personally, I would either give Ubuntu or Debian a try. Ubuntu installs have worked perfectly with my graphics and Debian's non-free installer also worked flawlessly with my system. That said, I don't have a high end GPU. I'm not a gamer, coin-miner, nor do I use my system's GPU for cracking hashes.

---

### Post by QIII on 2019-07-24
This sub-forum, as all others, is perfectly visible to the entire community.  You are "stuck here" in plain view.

---

### Post by jeremy31 on 2019-07-24
What Mint version?  Did you verify the ISO before writing it to USB/DVD?  I can not find anything like the error you received for dkms status on google for any Linux distro.
If you did not get much help at forums.linuxmint.com open the Welcome Screen in Mint, click support and then chat or click on ircs://irc.spotchat.org/#linuxmint-help and the Hexchat program should open and take you there when you are running Mint.  The ##linuxmint chat on freenode is not an official Mint support channel

---

### Post by rbmorse on 2019-07-24
Given the age of the hardware and that the system won't boot the live session from the installation media even when given the nomodeset option, I'm suspecting a hardware issue...likely the vram controller on the video card, but could be a flaky module.

---

### Post by random9999 on 2019-07-26
> **rbmorse said:**
> Given the age of the hardware and that the system won't boot the live session from the installation media even when given the nomodeset option, I'm suspecting a hardware issue...likely the vram controller on the video card, but could be a flaky module.

It boots a live session from the DVD in 'compatibility mode' with or without nomodeset. That's all it will do. All normal boot attempts result in black screen.

By 'module', do you mean the Linux Mint kernel?

I have Windows Vista installed on that PC as the main partition. It works perfectly. Zero issues.

It's Mint Xfce 19.1

I was unable to completely 'verify' it, there are 2 things you have to do and I managed to verify it with one of them, I can't get the other verification tool to work; but I don't see why there would be an issue downloading it from the Linux Mint site. I didn't get it from a 3rd party torrent or anything.

I guess I'll attempt to install regular Ubuntu and see if it makes a difference. If not... The IRC option seems like it might be a problem, since I'd have to close the chat and boot the PC over and over again while trying to solve this issue.

---

### Post by Dennis N on 2019-07-26
When I looked at Linux Mint a few years ago, the installer wouldn't boot in UEFI mode with Secure Boot on. That may still be true. Check that secure boot is off.
Ubuntu will install with secure boot enabled.

---

### Post by random9999 on 2019-07-26
There's no Secure Boot on that PC. It's not an available feature. It's Legacy BIOS, no UEFI. All the BIOS options have been set to what they need to be.

---

