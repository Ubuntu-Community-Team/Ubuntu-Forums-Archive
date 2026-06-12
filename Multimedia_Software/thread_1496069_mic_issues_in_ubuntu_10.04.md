---
title: "mic issues in ubuntu 10.04"
date: 2010-05-28
forum: Multimedia Software
---

### Post by Nearl86 on 2010-05-28
Hi I'm having issues with my microphone on my asus g60vx. When I turn on my mic in alsamixer it creates feedback in my speakers but programs such as skype dont recieve any sound. I have looked around for some solutions like editing the alsa-base.conf but it just ended up breaking alsamixer completely. Any help would be greatly apreiciated. Thank you.

Oh and i'm somewhat of a noob so step by step instructions would be great to.

---

### Post by Nearl86 on 2010-05-29
Anybody have any ideas?

---

### Post by Samb12345 on 2010-05-29
i've got the same problem. pavilion DV8 :confused:

---

### Post by Nearl86 on 2010-06-08
Bump

---

### Post by flying_174 on 2010-06-09
This is what solved the issue for me.

From Ubuntu Software Center 
Install Default Sound Card and Pulse Audio Volume Control 
Then, open Pulse Audio Volume Control. Select Input Devices. There  should be 2 sliders, and a input tester at the bottom. Speak into the  mic. you will know if it is working. If it is not, slide the slider that  says Front Left, to 0%. Now speak. If the mic works here your good to  go. 

Hope this helps.

---

### Post by lidex on 2010-06-09
The mic is obviously working, it's the routing that's muffed. Read through this thread:
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012]("http://ohioloco.ubuntuforums.org/showthread.php?t=843012")

---

### Post by Nearl86 on 2010-06-09
Thanks i'll try it, this has been driving my OCD insane.

---

### Post by Nearl86 on 2010-06-09
I didn't really find anything pertaining to the issue i'm having. I have thought of upgrading alsa but I don't know if I already have the most up to date version or not.

---

### Post by lidex on 2010-06-09
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=asus-mode3 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use Tab]
Use the left/right arrow keys to select and up/down arrow keys to change levels. M to mute/unmute.

---

### Post by Nearl86 on 2010-06-09
Wow thank you very much that worked! I tried modifying the alsa-base.conf before but I put in asus=g51v I believe and it did nothing. Thanks again!

---

### Post by lidex on 2010-06-09
Great. You're welcome. Please mark the thread as solved using 'Thread Tools' up top and enjoy.

---

