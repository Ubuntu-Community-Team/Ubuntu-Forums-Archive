---
title: "Anyone getting 5.1 DTS/DD via SPDIF using ALC888?"
date: 2009-03-12
forum: Multimedia Software
---

### Post by nicoloks on 2009-03-12
Hi All,

I've been stumped by this issue for some time now, and have now started to wonder if it is hardware rather than anything software. 

In a nutshell I have an [Asrock ALiveNF6G-DVI]("http://www.asrock.com/mb/overview.asp?Model=ALiveNF6G-DVI&s=AM2") mATX motherboard which has onboard ALC888 based audio. The [ALC888]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=28&Level=5&Conn=4&ProdID=135") is supposed to provide 10 simultaneous  channels supporting 7.1 surround.

I have a 5.1 receiver, and using the analog connection have no issue getting all 6 channels working between my Mythbuntu 8.10 box and my receiver. I recently purchased a SPDIF cable to connect to the SPDIF header on the motherboard so I could do digital audio pass through so that my receiver did all the DTS/DD decoding. 

This all worked well, however I only seem to be getting 2.1 sound (fronts and sub woofer) via the SPDIF output, regardless of if I use the optical or coax connections. I've tried all sorts of configuration options with ALSA, including upgrading to 1.0.19 and creating my own asound.conf forcing audio to use the SPDIF output. Since then I've installed Windows XP on another drive, and to my surprise it has the same issue in that during playback I am only getting 2.1 surround when using digital pass through over the SPDIF connection.

I have double checked my media with mediainfo which has confirmed they all have 5.1 channel DTS or Dolby Digital audio. I have triple checked all my connections between my receiver and my MythBuntu box, including using several different optical and coax cables. Nothing seems to work.

Has anyone using the ALC888 actually gotten 5.1 sound over the SPDIF connection? Any ideas at all on what might cause this? My next step I think is to get a DVD player and test 5.1 audio over that, but I am sure it will work as that is the setup I used to have. It is almost like the ALC888 only supports 2.1 over SPDIF, but can't find any documentation anywhere to support/deny this idea.

---

### Post by oschadit on 2009-03-27
I have the same problem vith this chip ACL888
Only 2.1 through SPDIF. Do you find a solution ?

---

### Post by nicoloks on 2009-03-27
No, but I did email Realtek support who replied with;

> Since driver does not support Dolby Digital / DTS encoder for SPDIF-Out ( Digital Output ) , the digital output only send the PCM Data format

By the sounds, the only way you can get full surround sound when using the ALC888 is to use the analog connection. Not ideal, but short of getting a new sound card (which I don't have room for in my case) it is the only option.

---

### Post by dutchwonderer on 2009-04-18
I use a Gigabyte GA-EP35-DS3L with ALC888 on board.
5.1 DTS is working for 44100Khz DTS music files on Ubuntu Intrepid and Jaunty (never tried mythbuntu). DVD's don't play at all here.

Main problem is that half of the DTS music files get recognized as DTS by most players and automaticly converted back to 2 channels when you use SPDIF. To overcome this, 1 bit in the header of these files has to change so the player (Totem in this case) thinks it's an 'Uncompressed 16-bit PCM audio'.
Not a nice way but for me, until now, the only way that works.

Vista plays everything in every way, Gigabyte put in a special utility to set up the ALC888 in any way desired.

Seems to be a software problem to me.

---

