---
title: "X becomes unresponsive when playing flash video in browser"
date: 2010-10-23
forum: Multimedia Software
---

### Post by powerslavez on 2010-10-23
Hi, 

I have an ATI 4650 HD and using flgrx via jockey, on 10.10. 

X becomes unresponsive when I play flash videos inside a browser. The image freezes, and the audio track loops, with a loop length of around 0.5 seconds. The only thing I can is reboot my computer. 

The xorg log file contains no indication that something went wrong. The last entries in it are the monitor display modes.

I cannot switch to the open source ATI driver, as my monitor screen goes blank after booting. 

I have tried a fresh system install, but that hasn't worked either. 

Has anyone had the same problem? Is there a fix? 

Thanks!

---

### Post by powerslavez on 2010-10-24
Bump

---

### Post by powerslavez on 2010-10-25
Bump

---

### Post by powerslavez on 2010-10-26
bump

---

### Post by clickwir on 2010-10-26
Try looking in /var/log/messages

I have been having some trouble with anything using audio. I get pulseaudio putting a ton of junk in my /var/log/messages file.

It might just be that pulseaudio is just busy doing whatever it's doing and writing to the hdd so much that the system becomes unresponsive. I have seen this first hand quite a bit. I don't have a solution, but if you are having the same messages in there, we might be able to push ahead.

---

### Post by powerslavez on 2010-11-02
You're right!

Yes, pulseaudio does make my system freeze. ...A fix would be nice. :)

---

### Post by clickwir on 2010-11-03
I'm doing what I can.

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/669729](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/669729)

---

