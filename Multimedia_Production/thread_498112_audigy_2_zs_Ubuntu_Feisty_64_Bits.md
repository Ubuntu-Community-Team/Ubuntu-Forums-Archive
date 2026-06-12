---
title: "audigy 2 zs Ubuntu Feisty 64 Bits"
date: 2007-07-10
forum: Multimedia Production
---

### Post by rolodoom on 2007-07-10
Doen anybody know how to setup jack server on ubuntu feisty 64?? I ca not get signal from the microphone.  Can isten music, etc but not record. Besides does anybody knows about any recording setup using this sound card??

Note: I haven't use ubuntu studio 'cause  there is no 64 bits. I'm running a plain feisty 64 installation.

---

### Post by linuxwizard on 2007-07-11
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

---

### Post by rolodoom on 2007-07-11
I have already been there, but after following the steps on that page, the jack server doesn't  start. 

I've been working with mac and win for audio recording, know I'm only running ubuntu feisty 64 but don't really understand how does the audio stuff work under this os. I've been looking for documentation about jack but it only gets darker and darker.... It's so frustrating...

---

### Post by linuxwizard on 2007-07-11
Do you have all the codecs installed that you need ?
I don't know if this will help on your microphone
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

---

### Post by fredj on 2007-07-11
I have an audigy 2 zs running under ubuntu so your problems can be fixed. First thing is why are you running
64bit Ubuntu. Do you have 4Gb or more of memory? If not then you can make your life easier by installing the
32bit version. Its difficult for me to give you any advice since I don't know how many of your problems are
caused by mixing a 64bit kernel with (possibly 32 bit drivers).

---

### Post by rolodoom on 2007-08-01
> **fredj said:**
> I have an audigy 2 zs running under ubuntu so your problems can be fixed. First thing is why are you running
64bit Ubuntu. Do you have 4Gb or more of memory? If not then you can make your life easier by installing the
32bit version. Its difficult for me to give you any advice since I don't know how many of your problems are
caused by mixing a 64bit kernel with (possibly 32 bit drivers).

It's on a Intel Core Duo 2,  3GB RAM (and planning on getting more) . Using Ubuntu feisty 64 bits. As said before, I also have been using a lot of time mac and intel, now since switching to ubuntu, I can make everything (design, webmaster, have fun) but not the audio stuff. I followed the steps on that ubuntu forum link about audigy and jack, but there's only one thing, don't know how to make it work. Any help would be appreciated.

---

### Post by fredj on 2007-08-03
Ok I will try to help. The first thing is, is your soundcard working through Alsa.
Can you playback wav files mp3s etc.
Install jack and qjackctl. Use qjackctl from the Applications->Sound and Video 
menu to setup jack. Start qjackctl and open the status window then go into
setup and make sure that jack has 2 inputs and 2 outputs and that alsa is being
used as the driver. Then exit from setup and start jack. Post any error messages
you get here.

---

