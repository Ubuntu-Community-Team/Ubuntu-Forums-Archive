---
title: "No center/LF output from onboard 5.1"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Chris Musampa on 2008-04-27
Hi all, I've been trying Ubuntu/Kubuntu on my laptop for a couple of months now and am happy to say windows is rarely fired up.  I've installed Mythbuntu (added kubuntu desktop) on my old desktop box (Gigabyte GA-7VAX motherboard).  The desktop box is connected to my living room speakers with wires plumbed in under floorboards and subwoofer nicely tucked away. All is well apart from the problem in the thread title .

Channel mode: 6ch
Duplicate front: On
All faders up


aplay -l
gives:

**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 3/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Your help would be greatly appreciated.

---

### Post by Chris Musampa on 2008-05-02
Anyone?

---

### Post by kpkeerthi on 2008-05-02
Type **alsamixer** in a terminal and make sure the required channels are not muted and volume levels sufficiently raised. 

MM - Muted - Use 'm' to toggle
OO - Unmuted
Use arrow keys to navigate
Use up/down keys to raise volume
Press 'Esc' to quit

---

### Post by Chris Musampa on 2008-05-02
Thanks for the response.  I've tried that previously but will run through it again tonight after work, any other suggestions in the mean time?

---

