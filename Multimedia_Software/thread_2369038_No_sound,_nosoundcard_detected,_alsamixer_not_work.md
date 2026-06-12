---
title: "No sound, nosoundcard detected, alsamixer not working"
date: 2017-08-17
forum: Multimedia Software
---

### Post by mortiba on 2017-08-17
Hello, I will provide you as much information as I can so you can help me with this. Many thanks in advance.
 I have Ubuntu 16.04.3 lts (gnome) in my Asus. The main problem is that my  computer is not detecting any sound card.  I was using an external  speaker (which was perfectly working) and after I disconnected it,  the  internal speakers of my computer where not detected anymore (before,  they were). I tried to solve this playing with alsamixer and some  answers in forums but everything turned worse...at the begining my  computer was able to detect the sound card (Intel). Now...not even that.
 I have tried all this:
 [https://askubuntu.com/questions/457028/sound-suddently-stopped-working-for-internal-speakers-headphones-still-work](https://askubuntu.com/questions/457028/sound-suddently-stopped-working-for-internal-speakers-headphones-still-work)
[https://bbs.archlinux.org/viewtopic.php?id=123447](https://bbs.archlinux.org/viewtopic.php?id=123447)
[https://ubuntuforums.org/showthread.php?t=1316634](https://ubuntuforums.org/showthread.php?t=1316634)
[https://askubuntu.com/questions/719548/unable-to-get-sound-working-ubuntu-server-14-04-3](https://askubuntu.com/questions/719548/unable-to-get-sound-working-ubuntu-server-14-04-3)
 and now I am following this guide, [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
so I will post the information you may need in order to be able to help me.
 I execute 

bash alsa-info.sh --stdout

and I get:

[https://paste.ubuntu.com/25336510/](https://paste.ubuntu.com/25336510/)


One thing here is that there is nothing writen in  Driver Version for Alsa.


 Then I executed step 4 from the guide I mentioned and I got:


[https://paste.ubuntu.com/25336524/](https://paste.ubuntu.com/25336524/)

And this is all I did for the moment. Thank you for your comments

María

---

### Post by ajgreeny on 2017-08-18
See if opening **pulseaudio volume control** from the volume icon in your panel ->Sound Settings shows the output as muted or set too low in the "Output Devices" tab

---

