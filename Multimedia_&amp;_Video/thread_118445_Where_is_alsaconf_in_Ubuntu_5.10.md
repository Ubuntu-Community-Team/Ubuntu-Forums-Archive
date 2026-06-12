---
title: "Where is alsaconf in Ubuntu 5.10?"
date: 2006-01-17
forum: Multimedia &amp; Video
---

### Post by Brian Kendig on 2006-01-17
Ubuntu 5.10 doesn't recognize the built-in sound on my laptop. I can't find the 'alsaconf' utility to configure it. Where is alsaconf installed? Or, why wasn't it installed, and where can I get a package to install it?

---

### Post by Sef on 2006-01-17
1) >  Where is alsaconf installed?

To check if something is installed:  aptitude search (program name)

Did not find alsaconf installed.

2)> ...where can I get a package to install it?

System -----> Preferences ------> MultiMedia Systems Selector ----> Audio ---->Input ----> Click on the arrows and highlight ALSA -----> Test ----> Close

---

### Post by Brian Kendig on 2006-01-17
[QUOTE=Sef]To check if something is installed:  aptitude search (program name)[/QUOTE]

"aptitude search alsaconf" doesn't find alsaconf, and nothing else I've tried finds it either, but it's supposed to be a part of 'alsa-utils' which is installed. Did Ubuntu remove the alsaconf binary from its distribution?

> System -----> Preferences ------> MultiMedia Systems Selector ----> Audio ---->Input ----> Click on the arrows and highlight ALSA -----> Test ----> Close

I tried that, but Alsa fails when I test it, and it doesn't install alsaconf. Where can I find a package which installs alsaconf on Ubuntu?

---

### Post by newuser111 on 2006-01-17
the alsautils in ubuntu breezy don't come with alsaconf! why is a question to ask the ubuntu devs

the best solution I have found is to download and compile the latest alsa from the alsa website,

use this guide [https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto) but keep in mind its intended for intel HDA (my audio chipset) but you can use it on any alsa compatible card

---

### Post by Brian Kendig on 2006-01-18
I downloaded alsa-utils from the alsa web site, but I'm not able to get alsaconf to compile.

Does anyone know why alsaconf was removed from Ubuntu 5.10? Or any package which will install alsaconf on Ubuntu 5.10 for me?

---

### Post by newuser111 on 2006-01-18
which error message does it give you when compiling?  I remember I had to install a whole bunch of packages to compile stuff for ubuntu

---

### Post by FarEast on 2006-01-18
Hi;) ,

'alsaconf' itself is not a binary but a script.  We can obtain it by compiling
alsa-utils from its source.  The package 'libasound2-dev' is needed.

```
tar xjvf alsa-utils-1.0.9[COLOR="Red"]a[/COLOR].tar.bz2
cd alsa-utils-1.0.9[COLOR="Red"]a[/COLOR]
./configure
make
cd alsaconf
cp alsaconf ~
cd ~
chmod 755 alsaconf
sudo ./alsaconf
```

---

### Post by Brian Kendig on 2006-01-19
That didn't work for me last night for some reason, but this time it did the trick! Thank you very much!

What can I do to help make sure alsaconf isn't left out of the next release of Ubuntu? Is there somewhere I can file a bug on this?

---

### Post by FarEast on 2006-01-19
> What can I do to help make sure alsaconf isn't left
> out of the next release of Ubuntu?

I think that 'alsaconf' is left out intentionally by the packager.
For we do not neet it so long as we have PCI/USB sound cards.
It makes users who have ISA sound cards unfortunate.
What shall we do:???: ?

---

