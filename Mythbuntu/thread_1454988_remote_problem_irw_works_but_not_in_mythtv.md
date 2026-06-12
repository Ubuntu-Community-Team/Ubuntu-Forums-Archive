---
title: "remote problem: irw works but not in mythtv"
date: 2010-04-15
forum: Mythbuntu
---

### Post by dragoster on 2010-04-15
I have a very strange problem with the remote to my mythbuntu system. The remote came with the case of my HTPC and it has "ione" written on it. The remote is being recognized as 3 separate devices, i.e. different keys on the remote are mapped to different devices in /dev/input/by-id:

```
usb-HOLTEK_USB_Keyboard-event-kbd
usb-HOLTEK_USB_Keyboard-event-mouse
usb-HOLTEK_USB_Keyboard-mouse
```

The first device corresponds to the arrows on the keyboard and the OK button, so that always works in the system as it is seen like a keypress on the keyboard. The second device is the one that I was using lirc to read from.

After a system update the remote stopped working although I made sure all my config files are in the same state as before. I can test with irw and get the correct output when I press the remote keys:

```
00000000000100a3 00 NEXTSONG ione
00000000000100a5 00 PREVIOUSSONG ione
00000000000100a8 00 REWIND ione
00000000000100d0 00 FASTFORWARD ione
0000000000010072 00 VOLUMEDOWN ione
0000000000010073 00 VOLUMEUP ione
00000000000100a7 00 RECORD ione
0000000000010193 00 CHANNELDOWN ione
0000000000010192 00 CHANNELUP ione

```

Strangely enough when I do

```
sudo cat /dev/input/by-id/usb-HOLTEK_USB_Keyboard-event-mouse
```

I get no output when I press remote keys. This used to work before so something has happened since the update. The fact that irw shows output when keys are pressed is also very strange. I tried to listen to all input devices and I get no output when remote keys are pressed, but I get output when I press the keys on my keyboard or move the mouse. 

Any ideas anyone? Not having a remote for Mythtv is quite annoying.

---

### Post by dragoster on 2010-04-15
After a couple of restarts the remote started working again. I didn't make any changes in the config files, so I have no clue what is actually going on...

---

### Post by dragoster on 2010-04-15
Nevermind, after a restart, the remote stopped working again. Any ideas what is causing this erratic behavior?

---

