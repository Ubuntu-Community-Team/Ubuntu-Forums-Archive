---
title: "0x2001 codec problem with mplayer"
date: 2010-08-03
forum: Multimedia Software
---

### Post by sutefunu on 2010-08-03
Hi there,
I'm running ubuntu 10.04 64bit but I'm quite new to linux.
 I've got a problem with .mkv files playing with mplayer and smplayer (which I prefer to use for the gpu video acc.). Anyway when I try to play the file with mplayer it shows message "cannot find codec for audio format 0x2001. I think its a dts format or something.
I have searched google for hours and tried everything that I have found but so far with no luck.
Just to mention that VLC works fine with the same file.

---

### Post by sutefunu on 2010-08-03
whats up? is the problem that serious that nobody can help?

---

### Post by andrew.46 on 2010-08-03
Hi sutenfu,

> **sutefunu said:**
> I've got a problem with .mkv files playing with mplayer and smplayer (which I prefer to use for the gpu video acc.). Anyway when I try to play the file with mplayer it shows message "cannot find codec for audio format 0x2001. I think its a dts format or something

Seems a little odd:

```

andrew@skamandros~$ **[COLOR="Red"]mplayer -ac help | grep -i dts[/COLOR]**
ffdca       ffmpeg    working   FFmpeg DTS  [dca]
dts         libdca    working   DTS-libdca
hwdts       hwac3     working   DTS through S/PDIF

```

What does your system show for this command?

Andrew

---

### Post by sutefunu on 2010-08-04
Hi, that command shows exactly the same stuff as yours. All "DTS"s are in red if that matters. I guess that makes it even stranger then.
I tried many things but nothing helped so far.

---

### Post by andrew.46 on 2010-08-04
Hi sutefunu,

Only 2 thoughts: firstly can you post the file somewhere so I can have a proper look at it? And second if vlc can play this file you should be able to get an exact identification of the codecs involved from Tools --> Codec Information.

Andrew

---

### Post by duhovnik on 2010-10-06
I have experienced the same problem within Manhattan OS (Ubuntu 10.04 equivalent). You are probably using the Smplayer and Mplayer from PPA, right? The 20100604 version? From here? 
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

I think that this build of mplayer is missing the DTS codec. You must have the newest version of the mplayer from the webpage....

I am not at my home pc now but I will find the page with full info for installation that worked for me later and then update this topic :D

---

