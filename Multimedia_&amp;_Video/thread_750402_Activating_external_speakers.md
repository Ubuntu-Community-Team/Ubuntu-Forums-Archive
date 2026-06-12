---
title: "Activating external speakers"
date: 2008-04-09
forum: Multimedia &amp; Video
---

### Post by Ba|der on 2008-04-09
I have an Acer TravelMate 4320, and I have not found out how to get  external speakers to work. It's only sound in the internal speaker. If I plug in a sound jack plug the sound for the internal speakers is still on, and not off as in Windows.

---

### Post by Metaljaz on 2008-04-11
Try opening the terminal and typing this command:
alsamixer

scroll until you get to external. Make sure it is on or unmuted. Press "M" to mute or unmute.

May be the solution.

---

### Post by Ba|der on 2008-04-12
I have no "external" item in the  list.
AlsaMixer v1.0.14
Card: HDA Intel
Chip: Realtek ID 268
View: Playback: Capture All
Item 1: Master[db gain=-12,-13]
Item 2: PCM [db gain=0.00,0.00]
Item 3: Caller ID (May be turned on/off by pressing M. It then changes from MM to 00]
Item 4: Off-hook (May be turned on/offby pressing M. It then changes from MM to 00]

Append: This in on Ubuntu 7.10, that I have on my second desknote.

---

### Post by Metaljaz on 2008-04-13
If you have a pci based audio card type this command in the terminal to identify it:

lspci

Look for multimedia controller. If you have an Intel based audio controller read here:
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

You can also read this thread which has been solved:
[http://ubuntuforums.org/showthread.php?p=4701195#post4701195](http://ubuntuforums.org/showthread.php?p=4701195#post4701195)

---

