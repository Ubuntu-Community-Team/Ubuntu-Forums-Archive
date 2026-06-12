---
title: "Microphone muted"
date: 2009-02-08
forum: Multimedia Software
---

### Post by wiz_master49 on 2009-02-08
Ok, before I say anything I MUST say that I have been searching google for easily over 2.5-3 hours now for the solution to this problem that appeared out of nowhere. I have read the numerous posts/stickies in this forum. I have tried almost everything I read that pertained to my situation. So here it goes, I was on TeamSpeak earlier today talking with my friend when I decided I wanted to try and get Amarok to work while I was on TeamSpeak so I tried aoss'ing TeamSpeak, didn't work. Got on TeamSpeak and mic and headphones were muted. So I tried getting on TeamSpeak again just regularly and now my mic and headphones are STILL muted. After a bunch of tinkering around in settings I got my headphones unmuted so I can listen to music and stuff but my mic stays muted. I have checked in the volume control panel and whenever I enable microphone capture and make sure the slider is up and the mic is not muted, as soon as I close the dialogue it resets back to mute. Couple of screenies to show what I am talking about:

Mic capture on:
[IMG]http://i42.tinypic.com/2potg20.jpg[/IMG]

I unmute my mic:
[IMG]http://i40.tinypic.com/2iifj1v.png[/IMG]

Close dialogue and open back up, mic muted:
[IMG]http://i40.tinypic.com/2vtps0p.png[/IMG]

If you want any info from me just post, I'll be glad to give it to you. Any help is appreciated. I really can't remember all I have tried or I would list them, but some things I have tried are stopping and restarting alsa service (I think that was it?), playing with different settings in volume control panel, and many others I can't remember. If you post something I already tried I will tell you. My sound card is not an integrated one but I can't remember which I have so if anyone could tell me how to get that info I will post that. By the way I am using Ubuntu 8.10

---

### Post by Zapadlo on 2009-02-08
Bump, same problem here.

---

### Post by wiz_master49 on 2009-02-08
So anyone have any suggestions? I really like using ubuntu rather than windows but I want to be able to use my mic, and in windows I have no problems using it.

---

### Post by nstorrs on 2009-03-13
I'm running into the same problem. If I unmute my microphone and then close Volume Control and re-open it it is muted again. I don't know if somewhere they are set that way by default and can be adjusted there (?).  If anyone has any ideas I love to hear them.  


p.s. Dell XPS m1530 with a built in Intel STAC92 sound chip. on Ubuntu 8.10

---

### Post by Jubward on 2009-03-16
Same exact problem :(

---

### Post by danhm on 2009-03-16
I've also got the same exact problem, on a Dell Studio 15n with 8.10. 

# lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)

I'd really like to not have to turn on my Windows desktop in order to use Skype.

---

### Post by nstorrs on 2009-04-26
Same thing; Dell XPS m1530 I had the problem in 8.10 and still do now in 9.04

$ lspci |grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by mkr55 on 2009-07-08
bump - me too

---

### Post by gradinaruvasile on 2009-07-08
Use alsamixer from a terminal. The gui sometimes fails to apply changes or is reporting wrong some stuff. So, open a terminal and type

```
alsamixer
```

---

### Post by Xlost on 2009-07-08
> **gradinaruvasile said:**
> Use alsamixer from a terminal. The gui sometimes fails to apply changes or is reporting wrong some stuff. So, open a terminal and type

```
alsamixer
```

I am having the same issue. Even after running alsamixer, and using the sudo alsactl store command in terminal same issue happens.

---

