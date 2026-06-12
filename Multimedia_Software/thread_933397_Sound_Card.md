---
title: "Sound Card"
date: 2008-09-29
forum: Multimedia Software
---

### Post by tonyh6243 on 2008-09-29
I am looking to complete my HTPC and was wondering what sound card other users can recommend. The card must be stable under Ubuntu 8.04 64-bit. The biggest criteria I have is that the card must support digital output through Ubuntu. Any recommendations you can make would be appreciated.

Thank you

---

### Post by markbuntu on 2008-09-29
I have a SIIG Soundwave 7.1 PCI card which uses the C-Media 8768 chipset. It works OOB with i386 and amd64. It has 7.1 surround and digital in and out and loopback and IEC958 switches to control the digital in and out in the gnome-alsamixer. There are some notes about the CMI cards in

/usr/share/doc/alsa-base/driver/CMIPCI.txt.gz.

This card works great for a $40 card. No problems like with all the Creative Soundblaster cards which drive everyone crazy.

---

### Post by tonyh6243 on 2008-09-29
Does the card provide Dolby Digital out to the receiver?

---

### Post by oldsoundguy on 2008-09-29
Another to check out is Turtle Beach, which, although they do not actually WRITE drivers for Linux, at least have a Linux forum that they HOST on their site.  I have been seriously debating going with them and dumping my Creative stuff .. (5 cards in all) .. which we all know is NOT talking to Linux developers. 
The digital output that is supposed to work DOES, but no stinkin' master volume to the amp.  Volume is totally dependent on the running program in Linux.  Sometimes works, sometimes does NOT work!

I do like the quality of the Turtle Beach and their audio is really superior to almost anything I have heard/used.  Only the Yamaha card in Windows sounds better on a PC based platform.

Then there is Mac .. The musicians machine.

---

### Post by tonyh6243 on 2008-09-29
I will have to give this brand a look.

---

### Post by markbuntu on 2008-09-29
The turtle beach cards also use the c-media chipset, at least some of them do. The lack of volume control over digital streams is available if you use pulseaudio and the digital workaround discused here:

[http://www.pulseaudio.org/ticket/139](http://www.pulseaudio.org/ticket/139)

Controlling digital streams is still very much a work in progress for the alsa driver writers but as the demand to use these is rapidly rising I expect we will see more progress on this issue.

Dolby Digital comes from the stream originating media/program, in VLC it is selectable. As far as I know this gets passed through the card untouched but that is a good question that needs more investigation.

---

### Post by oldsoundguy on 2008-09-29
Running Alsa as am on Gutsy machines and Pulse just did not want to work for me in them.  Maybe Intrepid will solve some of the issues I have had with Hardy, maybe not.  Right now I have three incredibly stable and working machines, really not interested in shooting myself in the foot. LOL
Am running digital out on only ONE of those machines .. the other two are hooked to analog speaker systems.

---

### Post by markbuntu on 2008-09-29
Pulse is not really a gutsy sort of thing and many necessary configurations and pulseaudio parts were left out of the standard hardy install which is why so many people are having such a hard time with PulseAudio. I really hope the same people are not putting together the default sound install for Intrepid.

---

