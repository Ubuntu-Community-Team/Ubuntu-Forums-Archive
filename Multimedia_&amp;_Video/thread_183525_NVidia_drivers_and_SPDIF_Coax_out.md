---
title: "NVidia drivers and SPDIF Coax out"
date: 2006-05-28
forum: Multimedia &amp; Video
---

### Post by andefeldt on 2006-05-28
Hi,

I hope you can help me out with these things:

I'm about to connect my LCD tv to my Ubuntu machine (so I can play games with my friends etc. on 32" instead of 19" ;)  The connection is going to be made with a DVI-I --> VGA cable, since my tv only allows for VGA connections. 

As far as I've read there has been problems with TwinView in nvidias drivers (you can't select which display is the primary etc). This should have been fixed in the latest driver (however, we still need confirmation on this one). I would then like to install the latest nvidia driver by using the installer-package from nvidia instead of the supplied nvidia driver from Ubuntu (this one is getting a bit old). 

So how do I install the newest nvidia driver and uninstall the driver supplied by Ubuntu? I think I gave up on it once, since it was a bit tricky, right? But now I kinda need to do it... So please help!

Also, I'm going to connect my computer with my surround receiver via a SPDIF coax cable. My motherboard is an Asus A8N-SLI with the NForce 4 chipset. However, I have not installed the nforce drivers from nvidia. I'm using the "standard" drivers from Ubuntu, namely the snd-intel8x0m for my soundcard. 

I've read that the SDPIF coax output isn't working by default. So how can I make this work in my Ubuntu? I'm using ALSA (at least I think I am). However, I can't find any asound.conf or .asound.conf files anywhere. 

But if anyone can help me out with these things I would be extremely thankful!

Anders

---

### Post by andefeldt on 2006-05-29
Ok, I found the answer to my NVidia driver question :) 

So now the questions if just, how do I get sound out of my coax SPDIF port in Ubuntu?

Anders

---

### Post by andefeldt on 2006-05-31
Sorry, but is this really a problem that NO ONE knows anything about? 

Anders

---

### Post by andefeldt on 2006-06-09
*Bump*

I seriously need help here. I can't get any sound out from my Coax connection.

Couldn't someone just try and help me?

Anders

---

### Post by chimpsky on 2006-06-09
Hello,

I managed to get the SPDIF on my A8N-SLI32 by investigating/installing/using the ALSA drivers. 

I'm sorry to say that I didn't make a note of how I did it, but there are guides within this forum which will show you how to do it. I just searched within here and managed to figure it out. It's not too difficult :D Just search for SPDIF and there will be some responses..

Good luck

---

### Post by andefeldt on 2006-06-10
I've searched so much... I'm using ALSA.

I've tried the following line in mplayer:

mplayer -ao alsa:device=spdif test.mp3

This results in no audio in my regular speakers (at my monitor) and no audio from my coax (spdif). However, mplayer plays the file without any warnings. It's like the output might be muted or something. But my alsa-mixer shows, that IEC958 Playback AC97-SPSA is turned on and turned up.

I really don't get this! 

Anyone else?

And is there a way to get all sounds from linux send to both the regular speakers and to the coax spdif?

Anders

---

### Post by Blind-Summit on 2006-06-16
I'd love to know how to set this up. It seems there are no easy answers. Having to patch up with little config files seems to be the only way I have read that people have it working. I have sound from XMMS via SPDIF to my yamaha amp but nothing else will pass sound out of that - they use the 3.5mm line out jack

hmm

---

### Post by andefeldt on 2006-06-16
[QUOTE=chimpsky]
I managed to get the SPDIF on my A8N-SLI32 by investigating/installing/using the ALSA drivers. [/QUOTE]

Hi,

Can't you post your .asoundrc file or asound.conf (or what it's called)? That would help a lot!

Anders

---

