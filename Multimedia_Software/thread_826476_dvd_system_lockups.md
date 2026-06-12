---
title: "dvd system lockups"
date: 2008-06-11
forum: Multimedia Software
---

### Post by aureus on 2008-06-11
Not quite sure if this belongs in multimedia/video, but it is dvd related...

Basically, pretty much any operation involving a dvd will lockup the system and force a cold reboot.  For example, typing 'lsdvd' will return nothing for about 15-20 seconds, then the system will lock up entirely.  Unresponsive to mouse/keystrokes, ssh sessions are unresponsive, cannot open new ssh sesseions.  I've also tried using lsdvd without gdm or a X server running, the same thing happens.

The same behavior also occurs when trying to play a dvd, such as with vlc.

I can't seem to find any log generated from the crash, but I haven't been looking particularly hard, just a quick grep through /var/log. 

Any ideas on how/where to start troubleshooting?

---

### Post by aureus on 2008-06-12
Bump.

Anyone have any ideas at all?

---

### Post by APU on 2008-06-18
I experience something similar and I am also trying to isolate the problem.

Here is what I have collected until now:

Inserting the very first DVD -> a dialog pops up and installs libdvdread3, libdvdnav?? and one or two other libraries (no libdvdcss so far). 

After that: Totem starts whenever a DVD is inserted and hangs after a few seconds. After 30 seconds or so the system hangs completely, mouse dead, keyboard dead, network deat - everything - requiring hard reboot.
 
As a respond I at first removed the Totem autostart function so that my system does not die whenever I put a DVD in. Then I installed VLC and tried to play a DVD with it -> System hangup just like with Totem.

Then I got libdvdcss2 for my architecture (amd64) from the mediabuntu repositories (not sure abouth the correct name). Now I can start up VLC first and from there choose "open disc" - the DVD will play fine. It will however NOT play fine if I instead right-click on the DVD icon on the desktop and choose "play dvd" from there. This will again crash the system.

I looked at the process table and there is an important difference that gives some clue about the problem. Opening VLC and selecting the DVD from within it will open "/dev/scd0". If VLC is started by right-clicking on the DVD icon on the Desktop it tries to read from "/media/cdrom0" which crashes VLC first and the System afterwards. In this case VLC crashes but one single "vlc" process remains in the process table and cannot be killed by any means. I have a feeling that this process is to blame for the following crash.

A further interesting observation: If I play the DVD only once in VLC by opening it from inside the VLC application I can then use right-clicking on the desktop to play the same DVD as long as I do not take it out of the drive. Totem does play it fine, VLC tries to play it but does not decrypt it. Nothing crashes but its just gibberish in VLC's case.

Please confirm if this is the same Problem you encounter so that we can further investigate. I did not find any information about this yet.

Just for comparison:
I use Ubuntu-8.04 Hardy Heron the amd64 edition
Intel Core2 Quad
4 GB RAM
Intel Graphics

---

