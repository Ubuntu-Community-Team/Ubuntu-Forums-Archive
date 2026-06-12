---
title: "Y04G0033 remotes with Leadtek DTV1000T and DTV2000H"
date: 2008-01-22
forum: Mythbuntu
---

### Post by ozybushwalker on 2008-01-22
I started with a DTV1000T and got it working receiving diital TV to my satisfaction. After quite a bit more tweaking I got a program guide working in a satisfactory way. I was almost ready to unleash the system on the family - just needed to have a working remote.

Well, the remote support for the DTV1000T is broken in 7.10 (claimed to be fixed in 8.04 which isn't out yet) but I also had a DTV2000H which came with a remote with the same code: Y04G0033. I pulled out the DTV1000T (the motherboard has only one PCI slot) and replaced it with the DTV2000H and tried to get that working. I hadn't been able to find any lircd.conf files for this remote so expected I would have to generate one.  In my research I had come across the articles at [https://help.ubuntu.com/community/InstallLirc/Gutsy]("https://help.ubuntu.com/community/InstallLirc/Gutsy")
and [https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative]("https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative")
which were generally helpful but I couldn't get irrecord to work: over a number of attempts it always reported: 

[FONT="Courier New"]Hold down an arbitrary button.
irrecord: gap not found, can't continue
irrecord: closing '/dev/input/event4'[/FONT]

Then I made another attempt with irrecord but this time instead of holding down tan arbitrary button I repeatedly pressed a button until irrecord got past that first step. Then I was able to generate a lircd.conf file. Subsequent testing with irw showed that most of the buttons on this remote DON'T repeat but CH+/CH- and VOL+/VOL- do  Hence irrecord's request to hold down an arbitrary button is misleading.

My initial lircd.conf had only a few keys to get me started. I found a Y0400033.conf which pretty well matched my remote so I'll tweak that file once I've got the basic stuff working.

I've also had some trouble getting MythTV to recognise and act on key presses on the remote, only enter seems to work. I seem to be missing something in the association between the lircd.conf file and the lircrc file but I'll have a further look at that tonight.

Due to the problem getting the DTV1000T remote working I had bought a remote  described as a "Digitech Windows Media Centre Remote Control" which came with a USB dongle. I couldn't get to work either but once I get the Y04G0003 remote working I'll take another look at the Digitech.

---

### Post by e00 on 2008-01-23
I'm using a DTV1000T and it works well. Didn't bother with the included remote once I found out I would have to patch various sources to get the thing working, instead bought a MCE remote from Altronics. Some head-bashing later I found out the MCE remote actually registers as a USB keyboard and sends Windows MCE compatible keystrokes! Fiddle with the key bindings of Myth and Mplayer and now they all work fine.

The moral is: watch out for those MCE remotes, they may actually be keyboards!

Sometimes my media box doesn't act on the keypresses, I don't know if it's the receiver hardware being flaky or Myth being a bit slow, but anyway...

---

### Post by badwolf on 2008-06-15
Thanks for the link [https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative]("https://blueprints.launchpad.net/mythbuntu/+spec/lirc-gpio-alternative").

using irw I was then able to check the remote was working.

Once I found a lircd.conf for my remote on the net, running mythbuntu lircrc autoconfigure program generated a the proper key bindings in ~/.mythtv so that my remote worked (sortof).

Still need to recompile kernel to get the remote capturing more quickly but im too lasy.

Good news for anyone starting out with this card, the recent Hardy kernel patches mean that the ir receiver generates events in /dev/input/eventX, so you dont need to re-compile the kernel for that as some guides recommend.

---

