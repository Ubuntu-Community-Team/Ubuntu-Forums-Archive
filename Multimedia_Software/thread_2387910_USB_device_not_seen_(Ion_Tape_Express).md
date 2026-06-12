---
title: "USB device not seen (Ion Tape Express)"
date: 2018-03-25
forum: Multimedia Software
---

### Post by Joe_Linux on 2018-03-25
joe@joe-X555LAB:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 13d3:3423 IMC Networks 
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-X555LAB:~$ sudo lsusb
[sudo] password for joe: 
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 007: ID 13d3:3423 IMC Networks 
Bus 001 Device 002: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
joe@joe-X555LAB:~$ 
I am try to use a Ion Tape Express in Audacity 2.1.2 in Ubuntu 16.04 but the device is not seen at all as you can see above.
Any help would be appreciated.

---

### Post by Autodave on 2018-03-27
Have you tried going into Audacity to see if Audacity sees it? Have you installed *pavucontrol *yet?

I record 18 channels via USB from a digital mixer. The only place I see the mixer is in Audacity. In Audacity:  Edit -> Preferences -> Devices -> Recording.

---

### Post by Joe_Linux on 2018-03-28
Installed Audacity it does not see it. Installed pavucontrol not a choice for usb device. Tried Audacity: Edit -> Preferences -> Devices -> Recording. Under 2.1.2 Audacity it separates the playback and recording devices the choices under recording are pulse and default nothing under usb.

---

### Post by Autodave on 2018-03-28
Another thought: did you have the Ion powered up when you started the PC?  That may help.

I know that you probably don't want to, but you could also attach a cable from the headphones jack to your sound card and do it that way.

---

### Post by Autodave on 2018-03-28
I did some looking on the net. While I found a few problems, I did not find anyone having an issue with having your device not being found by Linux: going clear back to 2010.  Maybe you have a bad unit? Bad cable? Dead batteries?

Have you tried it on another PC?  Maybe at least try it with an audio cable instead of the USB cable.

---

