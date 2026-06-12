---
title: "External Sound card not producing Sound"
date: 2011-09-02
forum: Multimedia Software
---

### Post by seekerphn on 2011-09-02
I have ubuntu 10.10 installed in my lappy and windows 7 also. I use  External sound card of 'Quantum' for sound because my internal sound  card don't produce good sound. I have been using External sound card  since Feb'11. 
Unfortunately for last 4-5 days my ubuntu is not producing sound with  external sound card but with internal card it is working. My external  sound card is working with my friend's lappy who has Fedora and it is  producing sound in my windows 7 too. Hence i conclude problem lies in my  Ubuntu.

I have checked :
Sound Preferences --> Hardware  ( it is showing extenal sound card )

I run this command :
sudo aplay -l

--- output ---
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Set [USB Headphone Set], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I have searched on google and tried many other commands ... couldn't get  the success ... Please somebody help me out. Otherwise i have no choice but to reinstall ubuntu 10.10

Thnx in advance for every relevant response.

---

### Post by shantiq on 2011-09-02
checking the obvious first      you have clicked output to your external ?     see second attached image (lexicon is name of my external)


[B]if yes
[/B]
======================================

would then suggest installing pavucontrol


```
sudo apt-get install pavucontrol 
```


and playing with the settings


i use an external sound card all the time   and good


but sometimes it resets itself to default (internal audio) so keep an eye on settings


===========================


**also**    looking at this

> I run this command :
sudo aplay -l

--- output ---
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Set [USB Headphone Set], device 0: USB Audio [USB Audio]
Subdevices: 1/1
Subdevice #0: subdevice #0



which one is your external in there or is not picked up at all?

---

### Post by seekerphn on 2011-09-02
I really thank you Shantiq for your assistance.  I have sort out my problem after upgrading from 10.10 to 11.04. Now i become Natty from Maverick :)

I have installed sbackup utility ( system restore ) for similar sort of problems. I hope this would help.

well, thnx again

---

### Post by seekerphn on 2011-09-02
Now I am facing average sound quality with 11.04 :( ... trying to update :)

---

### Post by lidex on 2011-09-02
> **seekerphn said:**
> Now I am facing average sound quality with 11.04 :( ... trying to update :)

Not sure what that means...do you know how to use alsamixer?

---

### Post by seekerphn on 2011-09-03
@ Lidex

> Now I am facing average sound quality with 11.04It means , i observed that my sound quality was better and louder in 10.10 than in 11.04

and brother I really don't know how to use this aslamixer and what is this Asla have to do with ubuntu sound.

---

### Post by dhrayofhope on 2011-09-03
I m using an external sound card in my desktop... but it failed to give 5.1 output........:( i have a 5.1 sound system connected to this sound card.

Actually sound comes in only one speaker......
How to get the sound from all the speakers.....

sudo aplay -l

----------output----------------------------------------------------------------------------------
*** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
----------------------------------------------------------------------------------------------------

[IMG]file:///tmp/moz-screenshot.png[/IMG]attached screenshot of sound preferences........

Please Help:(:([ATTACH]201383[/ATTACH]

[ATTACH]201384[/ATTACH]

---

### Post by lidex on 2011-09-04
> **seekerphn said:**
> @ Lidex

It means , i observed that my sound quality was better and louder in 10.10 than in 11.04

and brother I really don't know how to use this aslamixer and what is this Asla have to do with ubuntu sound.

Alsa is the linux sound framework and supplies the audio drivers. An acronym for Advanced Linux Sound Architecture.

**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by lidex on 2011-09-04
> **dhrayofhope said:**
> I m using an external sound card in my desktop... but it failed to give 5.1 output........:( i have a 5.1 sound system connected to this sound card.

Actually sound comes in only one speaker......
How to get the sound from all the speakers.....

sudo aplay -l

----------output----------------------------------------------------------------------------------
*** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
----------------------------------------------------------------------------------------------------

[IMG]file:///tmp/moz-screenshot.png[/IMG]attached screenshot of sound preferences........

Please Help:(:([ATTACH]201383[/ATTACH]

[ATTACH]201384[/ATTACH]

Don't see much C-Media action around here. Your fader should be in the middle, not all the way to the front.
Aplay doesn't require sudo so please don't use it - if it only works with sudo you have a permissions issue. See the info provided here: ```
zless /usr/share/doc/alsa-base/driver/CMIPCI.txt.gz
```

---

### Post by seekerphn on 2011-09-04
@ Lidex 

Brother, when i type alsamixer something appeared new and interesting. I configure it and sound got louder. It really solved my major problem. 

I am still feeling my system lacking in sound quality. 

well, thank you very much for paying your kind attention. I will remember this Favour :)

---

### Post by dhrayofhope on 2011-09-04
> **lidex said:**
> Don't see much C-Media action around here. Your fader should be in the middle, not all the way to the front.
Aplay doesn't require sudo so please don't use it - if it only works with sudo you have a permissions issue. See the info provided here: ```
zless /usr/share/doc/alsa-base/driver/CMIPCI.txt.gz
```

First so many thanks but problem still persists....
read the document but can't figure out the solution......:(

Only center and rear-right speaker along with the sub-woofer are producing sound.......
the rear-right speaker is louder than the center one.... i can not hear any sound from the other speakers........:(

And how can I adjust the separate volumes of individual speakers..... 
Please help...........

Thanks in advance........


one more thing i just want to know... the 5.1 sound system i m using ... have three input jacks..... the sound card has three separate slots for each jack..... but the inbuilt motherboard sound output has only one slot.......Is there any way to connect the three jack to one slot?? Please help ..... i m messing up the whole things to configure the sound system in ubuntu.........

---

### Post by lidex on 2011-09-17
> **dhrayofhope said:**
> First so many thanks but problem still persists....
read the document but can't figure out the solution......:(

Only center and rear-right speaker along with the sub-woofer are producing sound.......
the rear-right speaker is louder than the center one.... i can not hear any sound from the other speakers........:(

And how can I adjust the separate volumes of individual speakers..... 
Please help...........

Thanks in advance........


one more thing i just want to know... the 5.1 sound system i m using ... have three input jacks..... the sound card has three separate slots for each jack..... but the inbuilt motherboard sound output has only one slot.......Is there any way to connect the three jack to one slot?? Please help ..... i m messing up the whole things to configure the sound system in ubuntu.........

Have you tried alsamixer?

---

