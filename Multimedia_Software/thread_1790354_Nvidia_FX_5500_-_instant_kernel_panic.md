---
title: "Nvidia FX 5500 - instant kernel panic"
date: 2011-06-24
forum: Multimedia Software
---

### Post by mystmaiden on 2011-06-24
I had this card installed before with the legacy drivers in synaptic and it didn't actually freak out and cause kernel panics until I installed virtualbox. In complete frustration after multiple attempts to fix it I gave up. Now I'm doing a clean install of 10.04 LTS and I'd like to try one more time to get it working.

I installed the card in the box, and booted up. Now the kernel panic is instant and I can't see the screen well enough to do anything. I had read in several places that the issue was the newer Nvidia drivers. I have the old drivers from Nvidia (NVIDIA-Linux-x86-169.07-pkg1.run), but how can I install them?

thanks,

mystmaiden

---

### Post by BicyclerBoy on 2011-06-24
Looks like you have to do this the hard nVidia way..

The nVidia driver contains very good docs & the nVidia driver downloads has a driver readme of about 40 pages.

You need:
1. build-essential tools
2. linux kernel **headers** package that matches your kernel version (uname -r)

if you are running 64 bit & want 32bit compatible GL libs for Wine etc there is a 32 bit build library for 64 bit boxes (ia32-libs)
3. ia32-libs

Next:
console login or switch to console 1 & stop gdm
<Ctrl>+<Alt>+<F1>
login
[sudo] service gdm stop
cd to path of nvidia driver.run file..
cd ~/Downloads
[sudo] sh ./NVIDIA---blah--.run
(use the <tab> key auto complete your cmd)

Follow the prompts & look for error messages..

[sudo] service gdm start

The [] just indicate you need the sudo permissions.

---

### Post by mystmaiden on 2011-06-25
> **BicyclerBoy said:**
> Looks like you have to do this the hard nVidia way..

The nVidia driver contains very good docs & the nVidia driver downloads has a driver readme of about 40 pages.

You need:
1. build-essential tools
2. linux kernel **headers** package that matches your kernel version (uname-r)

if you are running 64 bit & want 32bit compatible GL libs for Wine etc there is a 32 bit build library for 64 bit boxes (ia32-libs)
3. ia32-libs

Thank you, BicyclerBoy for the reply! This is just a straight 32 bit system.  When I searched synaptic for build-essential tools 'devscripts' came up. Is that correct? And is uname-r supposed to be entered in the commandline to show me what kernel I have? If so, I'm getting 'command not found'.

thanks again,
mystmaiden

---

### Post by BicyclerBoy on 2011-06-25
Whoops my mistakes..

uname -r
has a space in there...-r is an option

The build-essentials tools package is "build-essential".
I think this package just creates available tools list..you may still have to install other stuff.

If you are stuck at the console login & need some tool xyz
sudo apt-get install xyz

---

