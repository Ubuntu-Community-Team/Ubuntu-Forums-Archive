---
title: "Need help changing output on amarok 2"
date: 2009-04-30
forum: Multimedia Software
---

### Post by Domas on 2009-04-30
Hi all,

For the last few hours I have been trying to found out how to change audio output on amarok 2. The problem is I am using external usb speakers and they works fine, but not with amarok. It gives sound from internal speakers. 

 cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd0340000 irq 22
 1 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:00:1d.7-3.1, full speed

If I understand correctly, amarok is using Intel, but not Audio. How can I change any configuration file? 

Using older version (1) of amarok everything was fine and even I could change sound engine on it, but not with amarok 2.

Any help would appreciate.

Regards,

Domas

---

### Post by drumfire420 on 2009-05-06
*Bump*

 as I am having a similar issue

---

### Post by drumfire420 on 2009-05-12
I've still been trying to figure this out, and the development version (2.1 Beta 1) added the option to  change the output.
To move to the development version, just add the PPA to your third party sources

[Link to Amarok's guide on adding the PPA]("http://amarok.kde.org/wiki/Download:Kubuntu")

This version seems to be working well, I've been using it for a day or two and haven't noticed any of the buggy-ness of the 2.0.2 version included in the main repos.

---

