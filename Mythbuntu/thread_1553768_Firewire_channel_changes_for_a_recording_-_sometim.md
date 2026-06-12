---
title: "Firewire channel changes for a recording - sometimes successful"
date: 2010-08-15
forum: Mythbuntu
---

### Post by ozite on 2010-08-15
I have a Comcast cable, Motorola DCH-3200 box, connected via FireWire as a FireWire cable box. The issue occurred on both 0.23-fixes and 0.24 trunk.

I have a problem with MythTV, sometimes, setting or changing the channel for a recording. Connection type is point to point, 100 Mbps, signal timeout = 2000, tuning timeout = 9000.

The problem usually lies with trying to record HD channels with three digits (e.g. 403, 420, 450, etc).  Maybe 2/3 the time the change is successful, but for the other 1/3 of the time only the first two digits are successfully changed and channel 40, 42, 45, etc. is recorded.

Any suggestions?

---

### Post by LowSky on 2010-08-16
Are you recording over firewire or just changing the channel?

I'm not completely sure of your setup, but I've been using mythchanger to just change the channel and it works great

[http://ubuntuforums.org/showthread.php?t=977820](http://ubuntuforums.org/showthread.php?t=977820)

---

### Post by ozite on 2010-08-16
I'm recording, and changing the channel, over Firewire.  In most cases, it flawlessly records whatever channel it records.

The Motorola cable box is 'slow' to register the channel change. Even with the normal Comcast remote, if I quickly press '4-5-0', it may or may not respond to all three digits and only catch two of the digits. If I press '4--5--0' with a larger delay between buttons, it always changes to the correct channel (450).

Ideally, there would be an option to put in and adjust a delay between digits given the channel changer.  

If there is no simple change, can someone point me in the right direction to suggest the feature for a future version of MythTV?

---

