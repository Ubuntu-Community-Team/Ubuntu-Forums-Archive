---
title: "No audio in Kubuntu Dapper after upgrade"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by anirban.sam on 2006-07-21
[B]After the latest upgrade to kernal 2.6.15-26-686 the sound is gone from my Kubuntu Dapper desktop. Thanks in advance for any suggestions.
[/B]
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Intel Corporation: Unknown device e002
        Flags: bus master, medium devsel, latency 0, IRQ 209
        Memory at f7900400 (32-bit, non-prefetchable) [size=512]
        Memory at f7900800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

---

### Post by Fatmaxlim on 2006-07-21
I have the same problem with the same sound card on my Ubuntu Dapper desktop.
 Any ideas how to solve it?

---

### Post by jrjr on 2006-07-21
Check permissions in system/administration/Users and Groups/your log in name/properties/user privileges tab

---

### Post by Robertjm on 2006-07-21
Is this a global setting, or can it be a setting for different sound devices? Reason I ask is my speakers are fine, however, I have no sound coming through my headphones.

I have a Creative Labs Platinum 5.1 w/LiveDrive. When I first installed Dapper Drake the headset was working, though it was rather annoying that the main speakers didn't go silent when I plugged the headphones in, and the Line2 (front microphone jack) wouldn't work for the life of me.

Anyone have any suggestions?

Robert

---

