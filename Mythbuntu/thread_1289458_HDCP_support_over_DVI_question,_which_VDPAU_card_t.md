---
title: "HDCP support over DVI question, which VDPAU card to pick?"
date: 2009-10-12
forum: Mythbuntu
---

### Post by CyyberSpaceCowboy on 2009-10-12
I'm building a MythBuntu media box using a single core P4 for recording OTA HD.  With the old CPU, I've learned I need to get an old style PCI nVidia 8x or 9x series that supports VDPAU for HD playback.  While I'm at it, I'd also like a card that supports HDCP (I'm not sold on the advantages of BlueRay, but playback only drives aren't very expensive and I'd like to at least have the capability).

I've read VDPAU runs on a dedicated co-processor that is the same on all supported Vidia cards, so the rest of the specs are unimportant for playing recorded HD.  However, this page, [http://www.mythtv.org/wiki/VDPAU](http://www.mythtv.org/wiki/VDPAU) ,  suggests faster cards with more memory are better at de-interlacing.  Since my TV is only 720p, do I even need to care?

On NewEgg, I can find 256Mb 8400 cards with HDMI out, but faster cards with more memory all have DVI and S-Video and no native HDMI. I understand HDCP is also supported through the DVI out, but my TV only has HDMI ports or VGA in plus component audio.  Is it as simple as using a DVI to VGA adapter on the card?

While I'm here, what protocols do I need to install to support HDCP and it's DRM, or do I need to dual boot into Window$ to play a Blue-Ray?

---

### Post by nickrout on 2009-10-12
Use a DVI to HDMI cable. 

You won't play a bluray disk in linux, but you will play a bluray ripped video on linux.

---

### Post by CyyberSpaceCowboy on 2009-10-13
How would I handle audio.  Will sound come out the DVI port?

---

### Post by utar on 2009-10-13
With a DVI to HDMI converter cable you will need to use separate audio inputs on your TV as DVI doesn't do sound.  This is what I use on my HDTV and it works great.  You will need to check your TV manual though to ensure it will work for you.

A graphics card with HDMI out may well have an internal connector so as to mix the sound with the video, but this will depend on the graphics card.



Utar

---

### Post by CyyberSpaceCowboy on 2009-10-13
Thanks Utar, I should have checked my TV manual, it would have explained a lot.  I knew it had specific audio inputs for each separate non-HDMI video input, but I found they are redirected if DVI is connected to HDMI.

Anyone have an opinion on whether a more powerful card will do me any good at 720p?

---

### Post by nickrout on 2009-10-13
> **utar said:**
> With a DVI to HDMI converter cable you will need to use separate audio inputs on your TV as DVI doesn't do sound.  This is what I use on my HDTV and it works great.  You will need to check your TV manual though to ensure it will work for you.

A graphics card with HDMI out may well have an internal connector so as to mix the sound with the video, but this will depend on the graphics card.


no, audio can go over dvi to hdmi.

---

### Post by utar on 2009-10-14
> **nickrout said:**
> no, audio can go over dvi to hdmi.

Done some more reading ([http://en.wikipedia.org/wiki/Digital_Visual_Interface](http://en.wikipedia.org/wiki/Digital_Visual_Interface)) and yep you're right. At least I've learnt something new today!


Utar

---

### Post by jyavenard on 2009-10-14
Technically, if you carry audio as well, it isn't DVI anymore, it's HDMI...

It just happened that DVI and HDMI are electrically compatible and with the audio embedded in the TMDS signal, a DVI cable as such can carry audio.

I have a gigabyte board with a nvidia 9400M chipset, it has a HDMI port, all I had was a dvi->hdmi cable. As this board output the same signal on both the hdmi port and the dvi port, I enjoy audio over the DVI cable.

---

### Post by CyyberSpaceCowboy on 2009-10-21
Just wanted to let everyone know I selected a Sparkle (because it has passive cooling) 8400 GS 512 Mb and a DVI to HDMI cable over the 9400 GT 1Gb because they have the same GPU and the reviews on NewEgg suggested the 9400 might be to much clockspeed with out a fan.  If I read the MythTV Wiki right, I would only see the advantage of a faster card over 720p.  I'm going to wait now for 0.22 to install Myth, I'll post a review of my mileage with a single core / PCI GeForce / OTA HD rid then.

---

