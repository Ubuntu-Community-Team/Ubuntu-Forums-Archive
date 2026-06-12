---
title: "[SOLVED] Help configuring M-Audio Revolution sound card"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by cjv998 on 2007-11-03
Hi everyone.  After messing around with 7.04 for a few weeks on my flash drive, I decided to take Ubuntu a step further and dual-boot XP and Gutsy from my 80GB IDE drive (Ubuntu got 7.5GB out of my 20GB of free space).  I have an ASUS A7N8X-X motherboard (nForce 2 chipset), and I have an M-Audio Revolution 5.1 PCI sound card.  I have an amp going to pair of stereo speakers connected to the front L/R channels, and a separate powered sub connected to the LFE channel.  Anyway, in XP, I used the sound card's software to divert bass to the sub (so the sub plays with stereo sources as well).  Is there a way to do this in Ubuntu?

In case anyone is confused about why I don't just hook the sub up to my amp...the amp is a simple 2-channel amp I built myself, and doesn't have fancy crossovers or anything in it.  I suppose I could put some in if I really wanted, but I'd like to avoid that.

Thanks for the help!

Edit: Solved the problem, used this guide that said it would upmix to 5.1, and now I have a working sub without any noticeable loss to my main speakers.  (Here's the .asoundrc file I found: [http://ace.pastey.net/64611](http://ace.pastey.net/64611), and here's the thread that goes into a little more detail about it: [http://www.nabble.com/noise-only-t3718152.html](http://www.nabble.com/noise-only-t3718152.html).  Also, there were a few threads on here that referenced that .asoundrc file, but I can't find them at the moment...a simple search would find them I'm sure.)

---

### Post by cjv998 on 2007-11-03
After some thinking, I realized I'm using the crossover that's built into my sub anyway.  So all I need to be able to do is splice together the left and right channel signals into a mono signal, and send that out the LFE port on my soundcard...the sub will handle the rest.  Any ideas, anyone?

---

### Post by cjv998 on 2007-11-10
Bump..anyone know how to do this? Thanks.

---

### Post by tgalati4 on 2007-11-10
Does your subwoofer take speaker power inputs?  If so, then route the L+R to the subwoofer first then out to the speakers.  You really don't need the LFE for most sources.

Did you activate all of the channels in the Volume Mixer (Edit-->Preferences)?  There may be a switch that does it automatically.

Because of the wide dispersion of low frequency, you can simply split the left channel and get 90% of the low frequency response.

You may need to bump the left channel slightly to compensate and turn up the sub slightly to compensate for L only vs L+R.

---

### Post by cjv998 on 2007-11-10
My sub will accept line-level inputs, but I'm trying to avoid using them at all possible costs, because I'm slightly obsessive about sound quality.  I'm pretty sure all the channels are activated; I'll double-check and get back to you on that.

Edit: I checked the Volume Control, and enabled the rest of the options under Preferences, but I still didn't see anything under the Switches or Options tabs about filters or crossovers or anything.

---

### Post by Yellow Pasque on 2007-11-10
If you're using ALSA, you need to uninstall it and download/install OSSv4, because that's who officially supports this card. One you have OSS installed, you'll have accesss to all the volume controls and inputs, but I don't know if what you want to do is possible. 
[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

---

### Post by cjv998 on 2007-11-10
Okay, I installed OSS, and when I run osstest in the terminal, it says it doesn't recognize my audio hardware.  Any thoughts?

After looking around a bit, it would appear the Revolution 5.1 is only supported by the retail version of OSS.  I assume that's the version you have to pay for?  (Also, on a related note, I can't find the license key for the version of OSS that I downloaded, where should I be looking?)

---

### Post by GameGod on 2007-11-10
> **Temüjin said:**
> If you're using ALSA, you need to uninstall it and download/install OSSv4, because that's who officially supports this card. One you have OSS installed, you'll have accesss to all the volume controls and inputs, but I don't know if what you want to do is possible. 
[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

This is just flat out wrong. ALSA supports the M-Audio Revolution cards just fine. If you try to "uninstall" ALSA, I'd suspect you'd break quite a few things.

Here's some useful links:
[seehuhn.de/pages/revolution]("http://seehuhn.de/pages/revolution")
[alsa.opensrc.org/index.php/Ice1724]("http://alsa.opensrc.org/index.php/Ice1724")

---

