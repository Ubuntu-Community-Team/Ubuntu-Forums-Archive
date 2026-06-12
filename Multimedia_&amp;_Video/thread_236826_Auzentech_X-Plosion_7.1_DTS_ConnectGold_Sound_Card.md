---
title: "Auzentech X-Plosion 7.1 DTS Connect/Gold Sound Card"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by ckasprzak on 2006-08-15
Does anyone have the Auzentech X-Plosion 7.1 DTS Connect/Gold Sound Card working on their Drapper install?

I'm looking at possibly upgrading from my audigy 2 value to this sound card if it works under my linux distro.  ;)

Thanks!

---

### Post by ckasprzak on 2006-08-15
> Q: Are Auzentech Soundcards compatible with Linux? 
A: Auzentech soundcards have limited compatibility with Linux. C-Media, our chipset manufacturer, has released the Linux driver for 8738, 8768, and 8770 chipsets. However, the driver does not support Dolby Digital Live and DTS Interactive. According to C-Media, Dolby and DTS do not intend to open their source for Linux OS. You can download the Linux Driver for CMI8738, 8768+, and 8770 from the Alsa Project:


So it looks like it could work with limited functionality, but I would like to hear that it actually works for someone.

Thanks!

---

### Post by Flash13 on 2006-12-24
That's a shame :( I've just got a card with the 8768+ chipset and a new surround sound system.

---

### Post by Spent Casing on 2006-12-24
I was thinking of buying an Auzentech X-Meridian for my new system build, which is the newest card.  I've been toying with the idea of building an HTPC.  But without DTS support, it probably wouldn't be an upgrade from my Audigy 2 unless it has a better DAC.

---

### Post by Anaximander Thales on 2007-01-21
> **Spent Casing said:**
> I was thinking of buying an Auzentech X-Meridian for my new system build, which is the newest card.  I've been toying with the idea of building an HTPC.  But without DTS support, it probably wouldn't be an upgrade from my Audigy 2 unless it has a better DAC.

I decided to go with the X-Meridian, because on the Auzentech site, it mentions that ALSA has drivers for the cmedia 8338, 8738, 8768 chips.  Well.  The problem lies in the fact that the X-Meridian uses the cmedia 8788 chipset.  No current ALSA drivers for that.  OSS however has drivers for the 8788 chipset.

Hold off a bit on the X-Meridian until ALSA gets the drivers for it.

BTW, the card does have DTS support (under Windows), but DTS/Dolby is not releasing it's source to the Linux community.

---

### Post by gaillard on 2007-03-16
Why? OSS works wonderfully, get the card!

---

### Post by xanium4332 on 2007-10-23
+1 from me for the X-Plosion card. I read somewhere that the CMI8770 chipset detected in ALSA as CMI8768, and on the alsa card matrix the CMI8770 is listed as supported ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media](http://www.alsa-project.org/main/index.php/Matrix:Vendor-C-Media)), but there's not a lot of real info...

Just want to know whether the surround sound works (i.e. no incorrectly mapped channels) and the SPDIF works (well atleast test to see if the light comes on).

Anyone tried it yet?

Xanium4332

---

### Post by gaillard on 2007-10-23
the oss drivers are very mature with full support for cmi8788, a breeze to install and have good dev support and documentation.  Not to mention very portable with their posix only api.  I use it myself and have to say if you have a 8788 just use OSS. And i mean the current OSS not the old one you have on your machine.  go to [www.opensound.com](www.opensound.com)

Not to mention if you don't want everhything resampled you'll need OSS or have to make a CODE CHANGE with alsa, which is unacceptable, what a joke.

there is my 2 cents

---

### Post by drama1981 on 2007-10-23
i wonder about using ndis wrapper and the windows drivers? any thoughts?

---

### Post by gaillard on 2007-10-23
why would you do that when oss is like 3 commands and you have everything you need?

---

### Post by drama1981 on 2007-10-23
> **gaillard said:**
> why would you do that when oss is like 3 commands and you have everything you need?

sorry i misread your last post. as long as dts and dolby is supported then your right there is no reason really. my appolgies

---

### Post by xanium4332 on 2007-10-23
For me I don't even care about the Dolby/DTS encoding (that can be handles in Linux). I just want to know if it works properly as a normal card, for example do all the surround channels work properly (and line up correctly in alsa), and if the SPDIF works (at least with passthru and 'normal' stereo pcm).

Anyone had any experience with this card?

Xanium

---

### Post by GG_HTPC on 2007-10-25
Gaillard,
I have Azuntech Meridian card as well with OSS drivers. Unfortunately, I can not get the card to output anything on SPDIF other than test sound.

Ideally, I would want to get the DTS/Dolby output from the sound card for movies.

Any tips?
Thank you,

---

### Post by luciferin on 2007-12-05
> **xanium4332 said:**
> For me I don't even care about the Dolby/DTS encoding (that can be handles in Linux). I just want to know if it works properly as a normal card, for example do all the surround channels work properly (and line up correctly in alsa), and if the SPDIF works (at least with passthru and 'normal' stereo pcm).

Anyone had any experience with this card?

Xanium

Sorry to take so long to respond to this, two months late, but it's an importaint question that you're asking and anyone looking at this card deserves to have it answered.  Yes, the surround channels work properly, at least for up to 5.1.  I've watched a DVD with the outputs hooked up to a receiver.  Passthrough also works without a hitch, both coaxial and fibre optic.

---

### Post by GG_HTPC on 2007-12-19
I have an Azuntech Meridian card based on the same chipset. I was able to successfully install the OSS drivers and run the tests from VMIX as well as command line. I am using a coaxial cable to connect the output from the SPDIF port to a receiver.

Unfortunately, none of the applications (Amarok, MythTV) seem to output any sound. I have tried using an optical cable as well but no luck.

Can anyone share exact steps after OSS is install to get sound in 5.1 mode using SPDIF port?

Thank you in advance.

---

### Post by KyRo1989 on 2007-12-22
Can't  tell u anything about SPDIF, but did you switch amarok & co to OSS after u installed it?

---

### Post by -::Bas::- on 2008-01-18
Hi Guys,

I'm intereseted in buying this card since it's supposed to be quite good, and I want to upgrade to a 5.1 stereo set and connect it through the spdif thingy. It's really vital that it runs well under ubuntu, otherwise I'm ******. I can't use Windows in my spare time, under worktime is a drag altogether.

Can anyone confirm that this card runs under Gutsy, and the card can output 5.1 sound through the spdif under linux? So I can finally make the move to 5.1 and ditch my M-Audio 2496....

Thanks.

---

### Post by GG_HTPC on 2008-04-08
One of the users asked me to do changes to devices in the directory but that did not help either.

How do I change the Amarok to OSS?

---

### Post by kraymore on 2008-04-22
i am wondering if this card works ok under Hardy.  its the 22nd (only 2 days till final) and i'm wondering if this will work painlessly with it.

---

