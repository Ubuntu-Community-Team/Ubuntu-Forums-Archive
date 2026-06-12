---
title: "Sound card problems."
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by Ch3rry on 2005-12-06
I just installed 10.5, and I'm having some sound card trouble. I previously tried the live CD before actually doing an hard drive install. And, when I was running the live disk, the sound was fine. But, since I've done the hard drive install it has not worked. There are times when I hear a slight crackle coming out of my speakers, where there would have normally been a sound.. But, most of the time there is nothing. If anyone could please give me some advice it'd be greatly appreciated. Thank you, in advance.

-Jen

---

### Post by jaredwhitehead on 2005-12-06
10.5? or 5.10.

If you heard sound during a Live session than there is hope for you. However, take a look around this forum for sound issues; almost everyone has them. I have pretty much given up on hearing anything come out of my laptop. Post your sound card info and the output from:

lsmod

---

### Post by Ch3rry on 2005-12-06
[QUOTE=jaredwhitehead]10.5? or 5.10.

If you heard sound during a Live session than there is hope for you. However, take a look around this forum for sound issues; almost everyone has them. I have pretty much given up on hearing anything come out of my laptop. Post your sound card info and the output from:

lsmod[/QUOTE]
Thank you for responding to my thread. ^^ Actually, when I started my computer today, the sound was working much better. It's very weird. But, I'll take your advice and read the other threads. I hope I wasn't repeating what someone else had already asked.. If so, I do apologize. I was trying to find my documentation that came with my motherboard so that I could claify and say exactly what sound card I have.. But, so far I haven't been able to do so. And, I'm not really too sure of how to find that information in Ubuntu. But yeah, thanks for the reply.

-Jen

---

### Post by Lucas32 on 2005-12-06
To find the brand/model of your soundcard, you could try going to system menu->administration-> device manager and see if there is anything that might indicate what type of soundcard you have. if you're not sure than try to post a screenshot of device manager.
another thing, you could try the Live cd again and once you're running it go into the graphical sound mixer.  it should say what soundcard you have on the mixer's title bar (at least it says that on mine).

finally, when you open your graphical sound mixer under file menu and change device, see if there is another device listed.  my mixer lists the device that's detected by the alsa drivers and the same device that's detected by the OSS drivers.  they're both the same device but named differently.  anyway, try adjusting the volume on one of the other devices.

---

### Post by Ch3rry on 2005-12-07
[QUOTE=Lucas32]To find the brand/model of your soundcard, you could try going to system menu->administration-> device manager and see if there is anything that might indicate what type of soundcard you have. if you're not sure than try to post a screenshot of device manager.
another thing, you could try the Live cd again and once you're running it go into the graphical sound mixer.  it should say what soundcard you have on the mixer's title bar (at least it says that on mine).

finally, when you open your graphical sound mixer under file menu and change device, see if there is another device listed.  my mixer lists the device that's detected by the alsa drivers and the same device that's detected by the OSS drivers.  they're both the same device but named differently.  anyway, try adjusting the volume on one of the other devices.[/QUOTE]
Oh... I haven't tried any of those ideas before. Thank you for the suggestion.. Much appreciated! ^_^

---

### Post by Ch3rry on 2005-12-07
I found this... I hope this works.. I posted it as an attachment.. But, just in case it dosen't, I'll include direct links to the screen captures...

[http://img241.imageshack.us/img241/6163/snapshot26ca.png](http://img241.imageshack.us/img241/6163/snapshot26ca.png)
[http://img236.imageshack.us/img236/5079/snapshot17yn.png](http://img236.imageshack.us/img236/5079/snapshot17yn.png)

---

