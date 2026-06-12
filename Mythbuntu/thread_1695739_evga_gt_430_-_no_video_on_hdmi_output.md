---
title: "evga gt 430 - no video on hdmi output"
date: 2011-02-26
forum: Mythbuntu
---

### Post by slaterson on 2011-02-26
i just installed an evga gt 430 in my mythbuntu box.  i have video output to my tv on the dvi output of the card, but no video output on the hdmi output.

the previous card was a 8600gt with only dvi output.  can't seem to find anything to allow me to select which video output on the card to use and the card isn't figuring it out on it's own.

any help/advice?

---

### Post by gordintoronto on 2011-02-26
Did you install a proprietary video driver? Do you have a Preferences/Monitors program? When you boot the computer, is the TV connected and turned on?

---

### Post by slaterson on 2011-02-26
i'm using nvidia's drivers (was using the same driver with the 8600 gt).

tv is turned on and even have the right input selected.

i've been using nvidia-settings to check the card status and change settings, there is nothing present on hdmi output or any setting for selecting dvi, hdmi or vga output.

do i need to have mythbuntu reconfigure xorg?  the only thing i can think of is xorg.conf isn't setup to be aware of my new card and its all powerful hdmi output. :)

---

### Post by gordintoronto on 2011-02-26
I have no experience with mythbuntu. I have a laptop with hdmi output, and it is always available for video. (I have to change a setting to get sound on the hdmi.)

Faint hope suggestion: remove the current driver and run Preferences/Available Drivers to get a new one. Actually, if I were changing video cards, I would always remove the proprietary driver before removing the old card.

---

### Post by LowSky on 2011-02-26
in a terminal type

```
sudo nvidia-xconfig
```

it will update to the new card

---

### Post by slaterson on 2011-02-26
ok, so now i'm in more trouble with this...

x won't start.

here's what i did:
1) uninstalled the nvidia proprietary drivers
2) rebooted
3) realized i don't even get a post screen on the tv when using hdmi, but i do when using dvi
4) check the hdmi connection on the card and found that the cable was being blocked by some sheet metal of the case.  it wasn't actually plugged in all the way and of course wouldn't work.  fixed that.
5) rebooted, now i get video via hdmi (post screen) BUT i can't get x to start.  i re-installed the nvidia drivers from the command line (sudo apt-get install nvidia-current), made sure the modules are loaded (they are).

rebooting just takes me to the command line, startx reports no screens can be found.  editing xorg.conf and specifying nvidia-current (or just nvidia) doesn't help.

can i reconfigure x automagically from the command line?  i'm not a daily ubuntu user, i just use it for my mythtv box.  i run gentoo on a couple other boxes, familiar with maunal configuration more than all this automatic stuff. :)

---

### Post by slaterson on 2011-02-26
> **LowSky said:**
> in a terminal type

```
sudo nvidia-xconfig
```

it will update to the new card

nvidia-xconfig is not on my system :(

---

### Post by slaterson on 2011-02-26
got it working.  had to revert to the vesa driver to get into x.  once in x i had to use the additional drivers gui tool to set the nvidia drivers.  is there no command line tool to set the nvidia binary drivers?

---

### Post by heyho on 2011-02-27
Are you sending audio over HDMI? If not, you may as well use the DVI, as it will be the same as HDMI.

---

