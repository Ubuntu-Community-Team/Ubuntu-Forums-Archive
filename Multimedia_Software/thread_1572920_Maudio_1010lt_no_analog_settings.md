---
title: "Maudio 1010lt no analog settings?"
date: 2010-09-11
forum: Multimedia Software
---

### Post by mal209 on 2010-09-11
Hi everyone,

ive been making the switch over to ubuntu from Vista and one of the last things in my way is getting my M-audio 1010lt card working in ubuntu (9.10, 64bit).

I set it up so that the maudio card is the primary card and in envy24control the digital mixer shows sound, and i turn up all of the sliders (and unmute) but nothing happens noise wise.

I went into the "sound preferences" gui and was able to disable the internal sound card.  It lists:

ICE1712 [envy24] PCI Multi-Channel I/O Controller
1 output/ 1 input

the top part is fine, but the 1 in/out is wrong.  I should have access to 10in/out.  Additionally, in the "settings for the selected device" drop down menu, there is no choice to select analog stereo to analog outs 1/2.

How can i get the analog output in this drop down menu or find some other way to get sound working??

Thanks in advance for your help,
Michael.

---

### Post by cchhrriiss121212 on 2010-09-12
This is a bug that has been around for several years, but it is possible to get around it by editing a few config files. Some people just decide to switch to a distro without pulse.
Anyway your solution is here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/52](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/52)

This guide will say you need to edit 2 different files. All you need to do to edit a system file is open a terminal and type:
```
sudo gedit "yourfile"
```

So for the first file you will enter this:
```
sudo gedit /lib/udev/rules.d/90-pulseaudio.rules
```

The second file will be this:
```
sudo gedit /usr/share/pulseaudio/alsa-mixer/profile-sets/via-ice1712.conf
```

I should also add that in envy24control, the volume control is under the analogue volume tab. DACs will be outputs and ADCs are your inputs.

---

