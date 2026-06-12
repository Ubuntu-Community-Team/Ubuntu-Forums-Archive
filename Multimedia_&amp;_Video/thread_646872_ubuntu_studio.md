---
title: "ubuntu studio"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by brandon333 on 2007-12-21
Is there a way to get ubuntu studio without burning to dvd? my dvd burner is not working.

---

### Post by Saahib on 2007-12-21
Do you mean.. want to install without DVD ? or directly from hdd ?

---

### Post by brandon333 on 2007-12-21
yes on the site it says you must burn the iso to dvd. its a tad to big for cd

---

### Post by brandon333 on 2007-12-21
anyone? is there a way to divide this, i only have a cd burner. or is there a way to open a iso file without a dvd?


if not can anyone tell me a decent video editor besides kini (wont detect my firewire)

---

### Post by corevette on 2007-12-21
burn a fresh copy of ubuntu gutsy onto a cd. install ubuntu, then once it's installed you can go to synaptic and install ubuntu studio from there or just do
```
sudo apt-get install ubuntustudio-desktop
```
in the terminal

---

### Post by brandon333 on 2007-12-21
I did and it started to install and then stopped here:

Setting up ubuntustudio-desktop (0.11) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
mini@mini-desktop:~$ 

what am I suppose to type


oh lol I guess its done.....well where is it dont see it?

---

### Post by brandon333 on 2007-12-21
this isnt what I am looking for it is only a dv editor kino and volume control I mean ubuntustudio.org tools, it is not in add and remove programs, I guess what I am trying to find out is:

In linux is it possible to open a iso file meaning launch it from not a dvd, or cd since it is like 30 mbs to big for a cd.

---

### Post by Drunky on 2007-12-23
Preface:  I understand that you want to install Ubuntu Studio but only have a CD burner.

Well, no problem.   And you don't need to worry about running an ISO.  The only caveat is that you have an internet connection (preferably not dial-up).

Burn yourself a copy of Ubuntu 7.10 Gusty on CD.  Not Studio, just Ubuntu.

Install this on your friend's machine.  Once installed also install any/all updates until it is current.

Now we upgrade this installation to Ubuntu Studio using [UbuntuStudio/UpgradingFromGutsy Wiki help page]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy") by opening a terminal and cut/paste:
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

This will give you a complete Ubuntu Studio installation including the real-time kernel.

This worked for me and I hope you find it useful.

---

