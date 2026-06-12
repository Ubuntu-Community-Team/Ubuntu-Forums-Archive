---
title: "hidraw vs bluetooth"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by Beeblebrx on 2012-04-19
I have just succesfully connected an "A4 Tech" 7100N keyboard-mouse set to Ubuntu on my workstation.  The wireless receiver device for this set is model "[COLOR=DarkGreen]RN-10B[/COLOR]", which connects through USB. Ubuntu recognizes keyboard + mouse as [COLOR=DarkGreen]hidraw0[/COLOR] + [COLOR=DarkGreen]hidraw1[/COLOR].

My Question: Can Bluetooth enabled devices connect to the workstation through such wireless device? Not asking about pairing, asking how BT (and HCI mode) relates to HID devices in raw mode and whether they can (they should be able to) communicate?

If yes, how? Create psudo-device in /dev for HCI and link it to hidraw?

---

