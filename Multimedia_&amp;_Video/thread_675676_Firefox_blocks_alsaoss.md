---
title: "Firefox blocks alsa/oss"
date: 2008-01-22
forum: Multimedia &amp; Video
---

### Post by akwatve on 2008-01-22
it looks like firefox blocks alsa/oss sound systems thus making it impossible for other applications (amarok, xmms, audacity etc.) to access sound card. Every time I start firefox, I face this problem. It disappears after I quit firefox. This is quite frustrating as there are many occasions when I would want to run amarok and firefox together. I see that there are others who are facing the same problem. Does anyone know how to fix this ?
I have 64 bit system and 32 bit firefox (thats the only way i can use flash plugins). I do not think that this is responsible for the problem but I dont know. May be the wiser folks will shade some light on this.

---

### Post by Yellow Pasque on 2008-01-22
Try OSS4 (see my sig). It uses a virtual mixer so that you can get multiple sounds streams playing. BTW, if you're running a 32-bit browser just for Flash, you really should try getting it working with nspluginwrapper so that you can run a 64-bit browser. There are lots of threads on this in the 64-bit forum.

My Ubuntu64 system has OSS4, Swiftweasel(optimized Firefox) 64-bit, and Flash plugin r115 w/nspluginwrapper. Everything works great and I can play music through foobar2000/WINE and hear sound from Flash videos at the same time.

---

### Post by akwatve on 2008-01-23
Thanks for the reply... I will try OSS4 today.

About the plugin issue, I did try nspluginwrapper but it didn't work. From what I read on the forums and nspluginwrapper wiki, it looked like I first had to install the 32 bit plugin and then run nspluginwrapper -i <plugin> ... I always got an error saying "the plugin is not NPAPI" (Netscape Plugin API). As the 32-bit firefox installation went smooth and sweet, I did not break my head any more on nspluginwrapper.

---

### Post by akwatve on 2008-01-23
Temüjin,

I tried to install oss4 as per ur HOWTO. I used failsafe terminal to install OSS4 deb but it seems that even in failsafe terminal, some sound driver related stuff was still loaded. Because I got an error messages saying "some sound modules cannot be installed as they are being used".  The installation failed with error code 2. When I tried to uninstall/reinstall it kept searching for some directories and some files which I dont have. So now my system is in inconsistent state which is really ugly (OSS4 is neither properly installed nor can it be removed). May be we need to used the totally NO-GUI terminal (one obtained using ctrl-alt-f1). Even the OSS installation guide suggests the same ....
DO you have any suggestions on how to remove existing OSS4 because I cannot do anything with it as of now.

---

### Post by Yellow Pasque on 2008-01-23
[http://www.4front-tech.com/forum/viewtopic.php?t=2054](http://www.4front-tech.com/forum/viewtopic.php?t=2054)

---

### Post by akwatve on 2008-01-23
Ahhh 
I just did as suggested in [http://ubuntuforums.org/showthread.php?p=4189555](http://ubuntuforums.org/showthread.php?p=4189555)
and luckily it worked... (Its actually a nasty thing to overwrite files in /usr/lib/)

Anyways Thanks again for this...

I did manage to install OSS4. when I run osstest it said all the tests were successful but I did not hear anything. I tried " ossmix front.mute OFF rear.mute OFF side.mute OFF center/lfe.mute OFF" But I got following error message :
"Bad mixer control name(1) 'front.mute' "

WHen I run Amarok, the mixer indicators show that its playing something. vmix0.vol is full. But I dont hear anything .... Am I doing something stupid here ? Is there other any way to Unmute volume ? What should be value of the parameter line-out set to in order to get sound from (internal/external) speakers

---

### Post by Yellow Pasque on 2008-01-23
What output do you get from an ossinfo -v command?

---

### Post by akwatve on 2008-01-23
Here is the output :
I have also attached my mixer settings.


Version info: OSS 4.0 (b1012/200801022339) (0x00040003)
Platform: Linux/x86_64 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 (alok-lappy)

Number of audio devices:	8
Number of audio engines:	16
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: hdaudio0 ATI HD Audio interrupts=9635773 (9635773)
    HD Audio controller ATI HD Audio
    Vendor ID    0x1002437b
    Subvendor ID 0x1025010f
     Codec  0: Unknown (0x14f12bfa)
     Codec  1: ALC883 (0x10ec0883/0x10250000 Ferrari5k/ALC883)
      Codec  3: Not present
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support


Mixer devices
 0: High Definition Audio ALC883 (Mixer 0 of device object 1)
    Device file /dev/oss/hdaudio0/mix0, Legacy device /dev/mixer0
    Priority: 10
    Caps:

Audio devices
High Definition Audio front       /dev/oss/hdaudio0/pcm0  (device index 0)
    Legacy device /dev/dsp0
    Caps: DUPLEX TRIGGER MMAP
    Modes: IN/OUT
      Out engine  1: Available for use
      Engine      2: Available for use
      Engine      3: Available for use
      Engine      4: Available for use
      Engine      5: Available for use
      Engine      6: Available for use
      Engine      7: Available for use
      Engine      8: Available for use
      Engine      9: Available for use
High Definition Audio rear        /dev/oss/hdaudio0/pcm1  (device index 1)
    Legacy device /dev/dsp1
    Caps: TRIGGER MMAP
    Modes: OUTPUT
      Out engine  1: Available for use
High Definition Audio center/LFE  /dev/oss/hdaudio0/pcm2  (device index 2)
    Legacy device /dev/dsp2
    Caps: TRIGGER MMAP
    Modes: OUTPUT
      Out engine  1: Available for use
High Definition Audio side        /dev/oss/hdaudio0/pcm3  (device index 3)
    Legacy device /dev/dsp3
    Caps: TRIGGER MMAP
    Modes: OUTPUT
      Out engine  1: Available for use
High Definition Audio pcm4        /dev/oss/hdaudio0/pcm4  (device index 4)
    Legacy device /dev/dsp4
    Caps: TRIGGER MMAP
    Modes: OUTPUT
      Out engine  1: Available for use
High Definition Audio spdif-out   /dev/oss/hdaudio0/spdout0  (device index 5)
    Legacy device /dev/dsp5
    Caps: TRIGGER MMAP
    Modes: OUTPUT
      Out engine  1: Available for use
High Definition Audio rec1        /dev/oss/hdaudio0/pcmin0  (device index 6)
    Legacy device /dev/dsp6
    Caps: DUPLEX TRIGGER MMAP
    Modes: IN/OUT
      In engine   1: Available for use
      Engine      2: Available for use
      Engine      3: Available for use
      Engine      4: Available for use
      Engine      5: Available for use
      Engine      6: Available for use
      Engine      7: Available for use
      Engine      8: Available for use
      Engine      9: Available for use
High Definition Audio rec2        /dev/oss/hdaudio0/pcmin1  (device index 7)
    Legacy device /dev/dsp7
    Caps: TRIGGER MMAP
    Modes: INPUT
      In engine   1: Available for use

---

### Post by Yellow Pasque on 2008-01-23
Hmm. YOur ossinfo looks ok. Some suggestions:

Have you changed to OSS in the System -> Preferences -> Sound menu?
Have you changed your output to OSS in Amarok?

---

### Post by raffytaffy on 2008-01-23
Is full duplex enabled?

---

### Post by akwatve on 2008-01-23
I use KDE, so In my Menu--->System Settings---> Sound Settings I have selected "Open Sound System" as preferred audio device.

Raffytaffy,

I have checked "full duplex" 
Please see the attached files for my sound system settings.

Is there any other way in KDE to check which default sound system is being used ?
 
 One observation: In my mixer the channel numbering start from 9(i.e. pcm8, pcm9....pcm15) Is that normal ? Shouldnt it start from pcm0 ?
 Also what are vmix0-* options ? especially what does vmix0-src mean/do ?

---

### Post by akwatve on 2008-01-24
Thanks Temüjin and Raffytaffy for ur help but as I did not have any success with OSS4 so I reinstalled ALSA and removed OSS4.
Coming back to my original question:
Is there any way to stop firefox from blocking ALSA ? I am having difficulty usinf firefox and amarok together

---

### Post by akwatve on 2008-01-26
Summary of the entire thread, in case some one else faces a similar issue.

Alsa has problems with multiple applications trying to access sound card. Further it CANNOT record from mic.

OSS4 can record sound. It also allows multiple applications. It also pretends to play files BUT NO SOUND comes out of speakers.

This is quite weird.....
I am wondering if we can use alsa for output and OSS4 for capture ?

Thanks,

---

