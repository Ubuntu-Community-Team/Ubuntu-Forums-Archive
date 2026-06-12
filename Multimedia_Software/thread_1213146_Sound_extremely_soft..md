---
title: "Sound extremely soft."
date: 2009-07-14
forum: Multimedia Software
---

### Post by Cortux on 2009-07-14
Hi, I have Ubuntu9.04 installed on a Dell E6400, the sound is way too soft. I can hear when I put my ear to the speaker, but the machine had Vista and sound worked great. How could I sort this out. 

BTW. Master volume is maxed.

---

### Post by igorzwx on 2009-07-14
It should be so with PulseAudio

---

### Post by raboofje on 2009-07-14
This is a common problem with HDA Intel sound chips. Check out [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) , does that help?

---

### Post by Cortux on 2009-07-14
Gonna try now, will let you know

---

### Post by renkinjutsu on 2009-07-14
try typing alsamixer into terminal and max out the other volume gauges, some of them are set to the lowest at default and one of them might be responsible for your soft sound

---

### Post by Cortux on 2009-07-14
To be honest, I am a bit lost there. In the terminal I get this message when checking for the sound card model .   Codec: IDT 92HD71B7X

Would you be able to help with this information

---

### Post by Cortux on 2009-07-14
> **renkinjutsu said:**
> try typing alsamixer into terminal and max out the other volume gauges, some of them are set to the lowest at default and one of them might be responsible for your soft sound

let me try that also

---

### Post by Cortux on 2009-07-14
I get this  






&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.18 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: HDA Intel                                                              &#9474;
&#9474; Chip: IDT 92HD71B7X                                                          &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00]                                                  &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;                                 &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                                 &#9474;  &#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;                      Digital    &#9474;  &#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;              &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;OO&#9474;               &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;MM&#9474;              &#9474;MM&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;               &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     100    80<>80   100<>100  80<>80                                  0      &#9474;
&#9474; < Master >Headphon    PCM     Front   Analog L  Analog L Digital  PC Beep    &#9474;
&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

---

### Post by khelben1979 on 2009-07-14
```
sudo apt-get install alsamixergui
```
will install the graphical variant of [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") if you're interested.

---

### Post by Cortux on 2009-07-14
> **khelben1979 said:**
> ```
sudo apt-get install alsamixergui
```will install the graphical variant of [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer") if you're interested.

will do, thanks

---

### Post by Cortux on 2009-07-14
Any more advise?

---

### Post by kmaster228 on 2009-07-14
i dont if this works but on my hp laptop i went into volume control by clicking the button in the panel and i put the volume for front higher and if you dont get that option go to preferences and check front

---

### Post by Cortux on 2009-07-14
will try it, gonna play around then come back tomorrow

---

### Post by raboofje on 2009-07-14
> **Cortux said:**
> To be honest, I am a bit lost there. In the terminal I get this message when checking for the sound card model Codec: IDT 92HD71B7X

OK, so following [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) you  now probably looked at /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz to find out which models are supported for this codec. I *think* this codec would fall under 'STAC92HD71B*', and as such support the models 'ref', 'dell-m4-1' and 'dell-m4-2'. Perhaps try those...

If you find out what works for your model, announce it in the thread at
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by Cortux on 2009-07-15
Ok, now i dont have any sound at all, I did have sound yesterday, and now its gone.

All I did was install a theme for Ubuntu, could it be related.

---

### Post by Cortux on 2009-07-15
Ok


IT WORKS NOW

All I did was log out , into vista, then restarted back into Jaunty and wala. It works great now. I would advise that others with dual boot option also try this if you having similar issues.

---

### Post by raboofje on 2009-07-16
I've heard some cases where the volume in windows determines the maximum volume in linux. 

This is, of course, a bug, but i'm not sure what's going wrong.

---

### Post by Cortux on 2009-07-16
I would love to fully install Linux only, but my problem is that my CBT nuggets dont work on Linux, I did post a thread on this but no luck.
 
Can someone direct me to a thread regarding how to install software that will allow my Webcam to work on my Dell E6400 Latitude. It does not currently work.
 
Also a program to support my skype account. I did install skype on my wifes Netbook (Lenovo S10E) But I cant get that to work with Jaunty Jackalope.

---

### Post by Cortux on 2009-07-17
Can someone direct me to a thread regarding how to install software that will allow my Webcam to work on my Dell E6400 Latitude.

---

### Post by Cortux on 2009-07-20
OK, found this and the sound is absolutely perfectly loud and clear. 



[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

---

