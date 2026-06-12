---
title: "Sound problem moving from ALSA to OSS"
date: 2011-01-11
forum: Multimedia Software
---

### Post by atomicspin on 2011-01-11
So, I moved over from ALSA to OSS, but I needed Skype so I went back to ALSA.  I'm getting these errors now:

ALSA lib pcm_oss.c:397:(_snd_pcm_oss_open) Cannot open device /dev/dsp

That being said, sound still comes through from music (mplayer) but sometimes sounds are very delayed on things like Pidgin.

Thanks in advance.

Ubuntu 10.10

---

### Post by Yellow Pasque on 2011-01-12
If you set your apps to use OSS output, set them back to pulseaudio (or ALSA).

---

### Post by atomicspin on 2011-01-12
> **Temüjin said:**
> If you set your apps to use OSS output, set them back to pulseaudio (or ALSA).

Is there a command I can do that will do this globally?

---

### Post by Yellow Pasque on 2011-01-12
> **atomicspin said:**
> Is there a command I can do that will do this globally?
No. Every app is configured differently.

---

### Post by atomicspin on 2011-01-12
> **Temüjin said:**
> No. Every app is configured differently.

Okay, but what about apps like F-Spot that don't have an audio configuration option but still use the warning beeps and such?

---

### Post by randolf_ambrose on 2011-01-14
> **atomicspin said:**
> So, I moved over from ALSA to OSS, but I needed Skype so I went back to ALSA.  I'm getting these errors now:

ALSA lib pcm_oss.c:397:(_snd_pcm_oss_open) Cannot open device /dev/dsp

That being said, sound still comes through from music (mplayer) but sometimes sounds are very delayed on things like Pidgin.

Thanks in advance.

Ubuntu 10.10

You said you MOVED to OSS... succesfully i guess!!! could you please tell me what all steps you went through to have OSS succesfully installed and working???

I tried to replace ALSA+pulsaudio with OSS... But by the time installation finishes( from deb or repo ), i get some error relating to compatibility issues with linux kernell and the installation would fail...
After this process, once i restart, there wont be any sound... i had remove all sound drivers and reinstall alsa+pulseaudio to have sound back...

Can you share how you managed to install OSS??? Does OSS installation has anything to do with the linux kernel i'm using???

---

### Post by atomicspin on 2011-01-14
> **randolf_ambrose said:**
> You said you MOVED to OSS... succesfully i guess!!! could you please tell me what all steps you went through to have OSS succesfully installed and working???

I tried to replace ALSA+pulsaudio with OSS... But by the time installation finishes( from deb or repo ), i get some error relating to compatibility issues with linux kernell and the installation would fail...
After this process, once i restart, there wont be any sound... i had remove all sound drivers and reinstall alsa+pulseaudio to have sound back...

Can you share how you managed to install OSS??? Does OSS installation has anything to do with the linux kernel i'm using???

Well, I followed the installation instructions and it didn't work for me either.  It took a few hours on IRC in #oss to get it working.  Even then, when it did, I just found programs I kind of needed (My work uses Skype) that didn't support OSS.  

OSS is really falling apart, I would love to use it and I like the idea of it, but it's just not there.  Hence, why I'm moving back.

---

### Post by randolf_ambrose on 2011-01-14
well... i also managed to get oss working... got sound...

new issues
1. even when i plug in my headset, sound comes from the laptop speakers...
2. i installed the volume control app for oss but i cant find it anywhere!!! the volume is very low as of now...

i'm still looking around!!!

any idea???

---

### Post by Yellow Pasque on 2011-01-14
Did you reverse the changes you made in the instructions?
```
sudo dpkg-reconfigure linux-sound-base
```

---

### Post by Yellow Pasque on 2011-01-14
> **randolf_ambrose said:**
> well... i also managed to get oss working... got sound...

new issues
1. even when i plug in my headset, sound comes from the laptop speakers...
2. i installed the volume control app for oss but i cant find it anywhere!!! the volume is very low as of now...

i'm still looking around!!!

any idea???
You'll have to ask someone to fix jack sensing for you. Maybe Cesium/Yair can do it for you if you post on the OSS forum or hit up IRC. As for volume control, see the suggestions here: [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
My PPA has packages for users not running pulseaudio: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa) . Lucid and Maverick are supported and I might add Natty if people ask me to.

---

### Post by randolf_ambrose on 2011-01-14
yes, sudo dpkg-reconfigure linux-sound-base, OSS is set!!!

so far i followed [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound) to get oss working... used the volume control patch mentiioned here... but... not working...

lemme try the forum...

---

### Post by Yellow Pasque on 2011-01-14
The patch is only necessary for Hardy. Read the instructions more carefully.

---

### Post by atomicspin on 2011-01-14
> **randolf_ambrose said:**
> well... i also managed to get oss working... got sound...

new issues
1. even when i plug in my headset, sound comes from the laptop speakers...
2. i installed the volume control app for oss but i cant find it anywhere!!! the volume is very low as of now...

i'm still looking around!!!

any idea???

1. Jack sensing doesn't work natively.  It *is* possible, but it's experimental and they really encouraged me not to do it.

2.  Just go in to terminal and type ossxmix and it'll pop up.

---

### Post by randolf_ambrose on 2011-01-14
now its working...

got ossxmix and changed some values!!!

tested everything... can play multiple audio files/applications

issues: will have to change values in ossmix every time i switch between headphone and laptop speaker...

still... 

thanks guys!!!

---

### Post by atomicspin on 2011-01-14
> **randolf_ambrose said:**
> now its working...

got ossxmix and changed some values!!!

tested everything... can play multiple audio files/applications

issues: will have to change values in ossmix every time i switch between headphone and laptop speaker...

still... 

thanks guys!!!

Let us know how it works, long term!

---

### Post by randolf_ambrose on 2011-01-16
to set up Multimedia Keys with OSS4
[http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Using_multimedia_keys_with_OSS](http://www.opensound.com/wiki/index.php/Tips_And_Tricks#Using_multimedia_keys_with_OSS)

---

