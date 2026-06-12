---
title: "Rosegarden in Edgy EFT and some music utilities"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by RagE_es on 2006-11-15
Hi,

I'm new in this forum and please forgive me if i make a new threat that is already posted by someone.

I'm starting in Ubuntu and Edgy Eft. I usually composed some music in Windows, but i'm really interested to do the same in Linux.

I tried to install Rosegarden but it starts with a low latency problems. I have read that i need to compile the kernel. I think that Jackd and alsa are alright connected but i can't hear any midi.

I compose midi with an USB Keyboard and i usually load soundfonts in Windows. Is there any possibility to play soundfonts loading them via software in Linux? I have an Audigy 4. 

I'd like you'd tell me the best programms i should use like Cubase or Sonar in Windows o refer me to any guide.

Thx.

---

### Post by dolson on 2006-11-15
Yes, you can play via soundfonts in Linux. I recommend that you use a software for it, instead of using the onboard synth built into the audigy. To do it, install qjackctl and then run it. Once you have it configured and running, then you can install and run qsynth. In qsynth, load up your soundfont. Then go into qjackctl and connect the audio output of qsynth to the sound card output, and connect the MIDI output of your keyboard into the MIDI input of qsynth. Then you will be able to play the soundfont with your keyboard.

For a more detailed explanation of how to do this type of stuff, please read the wiki: [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by Esben Kramer on 2006-11-15
There is actually a distro made specifically for music-production! 

[http://www.musix.org.ar/en/](http://www.musix.org.ar/en/)

I haven't tried it, because I need my Cubase, but you could give it a go. Hope it helps.

---

### Post by dolson on 2006-11-15
> **Esben Kramer said:**
> There is actually a distro made specifically for music-production! 

[http://www.musix.org.ar/en/](http://www.musix.org.ar/en/)

I haven't tried it, because I need my Cubase, but you could give it a go. Hope it helps.

Just for your information, Ubuntu Studio will be released when Fiesty Fawn is released.

---

### Post by RagE_es on 2006-11-20
Hi, I'm back again in this forum. I've tested musix. There i improved my knowledge about MIDI. Now I want to try it in Ubuntu. Thx anyway for your explanation. Right now i'm downloading ubuntustudio-audio from repositories. I'm waiting next release!

---

### Post by fritzm on 2006-11-20
dolson said :
> Yes, you can play via soundfonts in Linux. I recommend that you use a software for it, instead of using the onboard synth built into the audigy.

For my enlightenment, could you tell me why you recommend that ? I have an audigy card and it seems to work fine using asfxload to load soundfonts into it. Is there a flaw to this that I haven't run into yet (I'm only starting out with Linux audio)?

Fritz

---

### Post by RagE_es on 2006-11-21
I can't load my 150MB soundfont in Audigy either Windows or Linux. So I need to use some programs to load them via software :)

---

### Post by dolson on 2006-11-21
> **fritzm said:**
> dolson said :


For my enlightenment, could you tell me why you recommend that ? I have an audigy card and it seems to work fine using asfxload to load soundfonts into it. Is there a flaw to this that I haven't run into yet (I'm only starting out with Linux audio)?

Fritz

The reasons I recommend this are that it is much easier [for a newbie] to load soundfonts using a GUI app rather than asfxload, and to record the sound output into an audio track (using Ardour or somesuch) to create compositions.

If all you want to do is play music and not record it, and you don't mind using a command line utility, then asfxload might work fine for you. But for recording, JACK routing is a must, and I think that qsynth+fluidsynth work well for that.

---

### Post by fritzm on 2006-11-21
OK, so you are saying that one cannot route the Audigy audio output through JACK to a recorder - am I understanding correctly ? I thought that all system audio went through alsa, so it would be accessible to JACK but I can't seem to get the Audigy synth output (which I am hearing in my headphones) to go through JACK to Ardour, no matter how I play with alsamixer record source settings. Do you know of a good explanation of how the hardware, alsa and jack work together, because I'd like to understand how this all works? 

Fritz

---

### Post by zettberlin on 2006-11-23
> **RagE_es said:**
> x.

I tried to install Rosegarden but it starts with a low latency problems. I have read that i need to compile the kernel.

Just to start with lower latency in ubuntu you dont need to compile a kernel. There is a french project, that provides a properly configured kernel for Ubuntu Dapper Drake, that works very well in Edgy eft too:

[http://www.ubuntuforums.org/showthread.php?t=261821](http://www.ubuntuforums.org/showthread.php?t=261821)

after you followed the easy repository-setup HOWTO you can install the kernel (get the one for "testing", version 2.6.17.6-rt7-ubuntumusique) using synaptic.
RG, Muse, Ardour etc. are working very good with that kernel, set qjackct to start jackd realtime, I run it with 128 Frames/Period if I use Desktopstuff (Open Office, Firefox etc) at the same time as the Soundapps. You can go as low as 32 Frames/Period (that is about 1.5 ms latency...).

To make RG and Muse perfectly happy you`ll need to set the timer-resolution as well. You can do it like this:

1.) open a terminalwindow (called konsole in KDE)
2.) enter the following:

# sudo bash
# echo 1024 > /proc/sys/dev/rtc/max-user-freq


To make the latter permanent, I put the following lines at the end of the file  /etc/init.d/bootmisc.sh:

        #       set rtc for serious audioapps

echo 1024 > /proc/sys/dev/rtc/max-user-freq

There are better ways to do this, yet this works OK for me.

> **RagE_es said:**
> 
 I think that Jackd and alsa are alright connected but i can't hear any midi.

As noted before: midi just sends notes, there must be a audioapp running, that understands these notes and can generate sounds. I also recommend a Soundfont-Software like qsynth or swami, that can load soundfonts and play them. You can also use softsynths and samplers like ZynaddsubFX, ams or specimen. All these can be connected to a MIDI-Track in RG (rightklick on the trackhead choose a midi-software-device).

good luck ;-)

---

