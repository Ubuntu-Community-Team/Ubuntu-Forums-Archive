---
title: "Sound Problem"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by nokia.2003 on 2006-08-11
First of all before answering any questions keep in mind i am a total newbie in linux and have started using it from 1-2 days.
I have installed ubuntu 5.1 on Virtual PC 2004 and it is working but the problem is that there is no sound it is not detecting sound card when i run ubuntu through Virtual PC 2004. The sound was working when i tried the live cd version not on virtual PC 2004 but seperately while booting but it dosen't seem to work in Virtual PC 2004 after i have installed ubuntu on it can anyone help me?
I have a Realrak 97 audio as my soundcard.

---

### Post by wieman01 on 2006-08-11
Some users reported that the sound it muted/turned off by default. Same happened to me the first time I installed Ubuntu.

Try to enable sound using this terminal command:
> alsamixer

---

### Post by nokia.2003 on 2006-08-11
I apologize but i don't know from where to run alsamixer is it installed in ubuntu 5.1 by default if yes how can i run it ?Do i have t download it? As i have already said i don't know anything about ubuntu

---

### Post by rck_hitokiri on 2006-08-11
aplications > Accesories > terminal. or wherever you can find your terminal cauz im using 6.06. you gota research your problems to. i had the same problem having no sound and i know its frustrating. well read this to fully understand sounds in ubutu. Just post here so i can follow you up with any advices i can give you. cheers.

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) (here you can view how to configure your sounds, its by lord raiden, this will surely help you.

---

### Post by nokia.2003 on 2006-08-13
When i try to access alsamixer from terminal it gives me this error:
"alsamixer: function snd_ctl_open failed for default: No such device"
I don't know what to do.I have even upgraded my ubuntu to 6.06 but still same problem.

---

### Post by LordRaiden on 2006-08-13
Your error indicates that your soundcard is not installed or not loading. 

Do this in a terminal/console ```
dmesg | grep snd
``` and paste back the results here.
Following my guide will help you. Post back to this thread if you get stuck somewhere.

---

### Post by nokia.2003 on 2006-08-13
I used the command you told me in terminal there was no output.
I used dmesg only and it showed lots of stats but doing | grep snd does nothing which i guess is due to the fact that there is no sound card detected by ubuntu 6.1.

---

### Post by nokia.2003 on 2006-08-13
I went to Realtek's site and looked for drivers for AC97 audio card and there was linux drivers but it didn't had ubuntu in the list instead it had these versions of linux:
Redhat Fedora core 4
Redhat Fedora core 5
RHEL4
Linux(kernal version 2.2.14 or above)

Can any one these above versions be useful to me should i try to download any of these drivers for ubuntu 6.1 for my Realtek AC97 audio card?

---

### Post by Mithrilhall on 2006-09-09
Odd...the other day alasmixer would work from the command line but now I get the > alsamixer: function snd_ctl_open failed for default: No such device error message.

What's even more strange is I'm listening to mp3s while I'm typing this even though I do a "dmesg | grep snd" and get back no output.



](*,)

---

### Post by nokia.2003 on 2006-09-09
My problem is gone because my problem was related to virtual PC i was getting bored of running ubuntu slow on VPC so i installed ubuntu on hard disk and sound is working now.

---

### Post by Mithrilhall on 2006-09-09
That's the odd thing. I have sound but alsamixer doesn't work.

---

