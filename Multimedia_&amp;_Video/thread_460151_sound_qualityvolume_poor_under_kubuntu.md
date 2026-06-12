---
title: "sound quality/volume poor under kubuntu"
date: 2007-05-31
forum: Multimedia &amp; Video
---

### Post by blake_rateliff on 2007-05-31
I'm using kubuntu and the audio coming from the sound card has much lower volume and seemingly less bass than it did in windows, although this could be due to the lack of an equalizer in most of the media players.
I have the audio from the pc going to a reciever that has a couple of bose 501 speakers hooked to it. They usually sound great under windows using windows media player, but since switching to kubuntu they lack volume and bass response. 

I've remedied the problem for the most part by using an old set of speakers with a headphone jack as a preamp of sorts, bu I'd appreciate it if someone could help me get the audio from the sound card to work right.

---

### Post by blake_rateliff on 2007-06-01
bump...

does anyone know what could be causing this

---

### Post by blake_rateliff on 2007-06-02
bump...

does anyone know what could be causing this

---

### Post by blake_rateliff on 2007-06-05
bump...

---

### Post by blake_rateliff on 2007-06-08
bump... Is anyone out there? :(

---

### Post by blake_rateliff on 2007-06-10
bump... HELLO!?!?!
do I need to post more info?
is there no fix for this?
is there anyone in these forums?
please reply 
](*,)](*,)](*,)](*,)](*,)

---

### Post by videocheez on 2007-06-10
Dude I'm having the same problem and was getting ready to post the same question but thought I would piggy back onto your post but it looks no one has any adivce so far.  I have an integrated 8 channel HD audio CODEC sigmatel 9221 which is on my Intel D975XBX mother board.  I have 5.1 speaker set up and want to know how to set-up 5.1 speakers in ubuntu and why is the sound qualityso  poor too. Good a luck and sorry for getting you excited by responding to your post.

vc

---

### Post by chair on 2007-06-10
Maybe check your mixer settings. Run alsamixer from a console and make sure Master is 100% and PCM is 74%. That way it's full volume without amplification. You could also mute everything else to make sure there's no inputs adding noise.

But yeah, the most important thing is that PCM isn't any more than 74% (0.0 dB gain). If it amplifies is distorts badly.

---

### Post by Chappy7777 on 2007-06-10
What are you playing? MP3s? Streaming audio? One thing I have found in these forums is that your chance of getting replies goes up with the more info you provide. Sound card type, what you are playing, etc. The more you provide, the more the readers have to work with. Obvious, but true.
So, the one program that works I really like is XMMS. It is essentially Winamp for Linux and can use Winamp skins if you can't find a XMMS skin you like. And, to the point, it has an equalizer like Winamp. It will play mp3s and stream audio. You can install it using Synaptic.

---

### Post by blake_rateliff on 2007-06-12
srry about lack of info.
I've tried mp3,wav,and wma files with the same result under a variety of different media players.
(eg. exaile, XMMS)

I'm running Kubuntu 7.04
pc specs are as follows
Athlon64 3200+
1GB RAM
2 HDD's formated with ext3 (finally got rid of the ntfs partition :D)
Gigabyte Motherboard (Nforce 430 chipset)
Using onboard audio (alc880 codec according to the manual)

Audio runs from PC->cheap speaker with headphone output(temporary)->Kenwood reciever->Bose 501 speakers

The audio sounded just fine when I used it in windows with no extra amplification,but under linux it sounds weak,tinny, and seems to lack bass and is distorted.

Also the volume control on my keyboard no longer works. It shows a volume bar across the screen but adjusting it has no effect on the volume.

I assume that since these worked alright before this must be a driver issue in Linux.

Right now I've kind of fixed the problem by using a cheap speaker with a headphone output as a preamp
,but  this causes the speakers to emit a loud pop every so often.

Thanks in advance please ask if you need more information

---

### Post by blake_rateliff on 2007-06-13
when i use alsamixer there is no master but there is front,pc speaker, and pcm.
however when pcm is turned to 100 it is calling that 0db gain same with front

---

### Post by blake_rateliff on 2007-06-13
just found that alsamixer is trying to use 8ch sound rather than 2ch. I'd imagine this is why the speakers sound bad since it is trying to use them as 2 front speakers in an 8ch system rather than as 2 speakers in a stereo system. alsamixer will not let me change from 8ch to 2ch.
if anyone knows how to fix this I'd appreciate the help

---

### Post by blake_rateliff on 2007-06-13
bump...

---

