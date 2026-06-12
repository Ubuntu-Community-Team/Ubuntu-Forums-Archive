---
title: "Ubuntu 12.10 64 Bit Soundblaster X-Fi Sound Problems"
date: 2012-11-01
forum: Multimedia Software
---

### Post by UbuNewbie123 on 2012-11-01
Hi everyone,

I just installed a fresh 12.10 after a long break from Ubuntu. I see some great improvements but some old problems still remain.

Anyway, I am experiencing popping/cracking sounds from my speakers. I understand that the SoundBlaster X-Fi drivers are terrible on Linux.

Any idea how to fix this problem?

---

### Post by DemonSpeedster on 2012-11-03
I also am having problem with X-Fi, in my case the X-Fi Surround 5.1 USB. The X-Fi works fine on Win7 and Maverick. The cracking and popping only happens when you switch the hardware profile to more than 2 channels (4.0-5.1)
 
Sometime the cracking can be eliminated by switching the profile from analog stereo to 5.1 several time, but it will return after reboot

---

### Post by UbuNewbie123 on 2012-11-03
Update this post if you find a permanent solution for this bug. It seems like I will continue to use Windows as my main OS until I am 100% sure that my Ubuntu experience can match my Windows experience.

---

### Post by kaspian on 2012-11-05
I can hear annoying noise on my x-fi xtreme gamer edition under ubuntu 12.10.
Works perfect under windows :\

---

### Post by Termo on 2012-11-22
I have the same issue with my creative X-fi Xmod on Ubuntu 12.10 64bit :( As far as I remember it worked fine on earlier Ubuntu distributions, I will test in Virtualbox...

---

### Post by kaspian on 2012-11-22
I solved problem with noise. The reason of this noise is turned by default "microphone to dinamics output, not sure how to call it correct". I just installed some advanced mixer software from software center and turned it off.

---

### Post by DemonSpeedster on 2012-11-26
> **kaspian said:**
> I solved problem with noise. The reason of this noise is turned by default "microphone to dinamics output, not sure how to call it correct". I just installed some advanced mixer software from software center and turned it off.

Can you elaborate more on that? What kind of X-Fi card do you have? Is it PCI or USB? And what kind of mixer app did you use?

---

### Post by DemonSpeedster on 2012-11-26
Actually the last software update apparently solved the clicking sound problem. I can use the 5.1 profile without any glitch in sound output

---

### Post by kaspian on 2012-11-27
> **DemonSpeedster said:**
> Can you elaborate more on that? What kind of X-Fi card do you have? Is it PCI or USB? And what kind of mixer app did you use?


I'm using old PCI card (X-Fi XtremeGamer). I've installed QasMixer from software center.

---

### Post by Another Monkey on 2012-12-03
Could you point me to the documentation for that please?  I'm only showing a "Master" slider for my X-Fi card for some reason.  Not sure why.

---

### Post by The Bright Side on 2013-05-19
> **Another Monkey said:**
> Could you point me to the documentation for that please?  I'm only showing a "Master" slider for my X-Fi card for some reason.  Not sure why.

Same here. Anybody? I'm trying to use my Sound Blaster X-Fi Surround 5.1 Pro's analog in for mic. Ubuntu's own sound settings only show me S/PDIF in. Used to work in 12.04, now I'm on 13.04. 64 bit. :-/

[IMG]http://www.knowingme.org/sound.gif[/IMG]

---

### Post by The Bright Side on 2013-05-21
Solved my mic problem! I needed to install the libasound2-plugins:i386 package, as explained in this article:
[http://www.webupd8.org/2013/05/skype-42-for-linux-released-with-minor.html](http://www.webupd8.org/2013/05/skype-42-for-linux-released-with-minor.html)

---

### Post by jis on 2013-06-06
> Since its release X-Fi has caused several unsolved problems with sound glitches on various motherboards.[http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi]("http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi")
Here is some info about its Linux support: [http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support]("http://en.wikipedia.org/wiki/Sound_Blaster_X-Fi#Linux_support")

Can you tell me about the quality of ALSA drivers in current ubuntu releases? Are all features supported?

---

### Post by libcos on 2013-07-17
Well, im still having this problem, i need to unplug and plug it until it randomly somehow works but only main jack and pulseaudio wont recognize mic so i need manualy add it from alsa. (USB soundblaster X-fi HD), none of the "solutions" here helped me, anyone any idea?

---

### Post by ryan198685 on 2013-07-17
Solved my mic problem! I needed to install the libasound2-plugins:i386 package, as explained in this article:[http://www.badluckbear.info/77](http://www.badluckbear.info/77)

---

### Post by libcos on 2013-07-18
someone posted that before, didnt help at all.

---

### Post by matt9 on 2014-01-06
Guys, giving this a bump since I've been wrestling with this as well.  I'm on 13.10 (but following the forum searches, people have been fighting this since 08!)

I found [this video]("http://www.youtube.com/watch?v=viZBd5hc8_k") from a few months ago from a guy who seems to have solved a similar issue on Windows with a solution similar to that suggested with Qasmixer muting Line and Mic.  Qasmixer however does not give me those options.

Anyone ever get this one solved?

---

### Post by matt9 on 2014-01-20
...apparently not.  

Well for the record (and in case someone far smarter than me comes along and works out how to pull this apart and put it back together again), I had no issues running anything 11.10 or 12.04 based.  This included Ubuntu, Lubuntu, Elementary and now Mint.  In each of these distros, I'd get that buzzing sound for a few seconds, and it would go away promptly.  However anything from 12.10 up, the buzz stays on constantly when I go into anything above stereo mode.

I installed Mint 12.04, added some of the backported repos (as I wanted to get a newer version of Cinnamon), and when I ran those updates (I just set it off without looking), it updated ALSA, and the buzzing sound was back.  

I clean reinstalled it, and have stayed with Mint's 12.04 LTS and not run any updates at all (I'm using it as an HTPC so really everything other than sound and video are superfluous to me anyhow).  

Perhaps someone better versed in such matters will be able to see what happened within ALSA/Pulse world to change the relevant drivers here, or could suggest a way to roll the driver back to the 12.04 version and have some luck with it.

---

### Post by mikel192 on 2014-01-24
This worked for me.
[http://guh.me/solving-creative-sound-blaster-x-fi-titanium-crackling-slash-distortion-on-linux/](http://guh.me/solving-creative-sound-blaster-x-fi-titanium-crackling-slash-distortion-on-linux/)

---

