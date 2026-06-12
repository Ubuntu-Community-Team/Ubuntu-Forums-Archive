---
title: "Intrepid upgrade: no audio via spdif output"
date: 2008-10-31
forum: Multimedia Software
---

### Post by moba77 on 2008-10-31
Hi Guys !

I've upgraded into Intrepid , i have a problem with audio:

My sound card is ALC885 and is connected to mu 5.1 system trough a psdif . When i play a dvd with VLC there is sound (I've check SPDIF option into the player) but when i try to play music with Banshee or other player there is no sound . Also system sound doesn't work !

I've modified /etc/pulse/daemon.conf

; default-sample-format = s16le

; default-sample-rate = 44100

; default-sample-channels = 2

I've removed the ";" , modified channel into 6 and sample rate into 44800 .

I've checked all volume and they're at maxium


Thanks a lot for support!

---

### Post by fjf on 2008-10-31
I have the same problem with an ALC888.  The trouble is that pulseaudio only works with the first souncard, the analog out, and does not play through the second, the digital one.  You can see them in a terminal with aplay -l.  I've tried all fixes I found and no luck.  The thing with ubuntu is that they are constantly changing things (even those that work) to improve it, and sometimes this brakes the system.

Like the other issue:  no sound with flash within firefox.  No youtube.

---

### Post by beerguzzler on 2008-10-31
I've got similar issues and I've not upgraded! I did run the latest patches yesterday and ever since I cannot get sound via SPDIF. I've been singing the praises of Ubuntu to everyone I know that ownes a pc but tbh it seems to be gettting more buggy and frustating to use. As I use my pc also as a media centre I've got no choice but to go back to Vista. Good job I didn't delete that partition after all!!!

---

### Post by pazanotis on 2008-11-02
I had exactly the same problem. I downloaded and installed gnome alsa mixer through synaptic. From gnome alsa mixer i checked the iec958 and that did the trick. Audio works fine fine now.Hope this helps.

---

### Post by fooman on 2008-11-05
thanks pazanotis,  that was driving me nuts!  

:guitar:

---

### Post by bradb-acc on 2008-11-17
Most common problems which comes with Ubuntu 8.10 are sound related ones. Annoying part is when start to play something in Totem media player you video without sound. So here is a quick fix:

Add Medibuntu repositories to Ubuntu 8.10 Intrepid Ibex:

    sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

Add GPG key for the aforementioned repositories:

    sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Then update your software resources:

    sudo apt-get update

Install w32 codecs (or install with a single click for 32 bit systems, for 64bit systems):
for 32 bit systems:

    sudo apt-get install w32codecs

for 64 bit systems (the w64codecs is only made for feisty and gutsy, works fine in intrepid as far as i know)

    sudo apt-get install w64codecs

That’s all, cheers for Intrepid!

---

