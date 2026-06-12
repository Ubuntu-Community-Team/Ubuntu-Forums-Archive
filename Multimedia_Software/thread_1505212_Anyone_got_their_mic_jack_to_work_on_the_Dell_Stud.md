---
title: "Anyone got their mic jack to work on the Dell Studio 1535?"
date: 2010-06-08
forum: Multimedia Software
---

### Post by Jammanuser on 2010-06-08
Hello,

I have a Dell Studio 1535 and can't seem to get recording from the mic jack to work. I was wondering if anyone has got it to work or not on Ubuntu 8.10 64 bit.

I fiddled with the settings in System->Preferences->Sound and in Volume Control: HDA Intel (Alsa mixer), as well as the settings in the semi-CLI program alsamixer, but it doesn't matter what I do. I have failed to get it to record from the mic jack. It will only record from my internal mics, and I don't want that at all.

Thanks in advance for any help.

---

### Post by Yellow Pasque on 2010-06-08
You should upgrade to the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
(actually, you should upgrade to Lucid ;) )
You may also need to specify a model keyword in /etc/modprobe.d/alsa-base.conf (or was it just alsa-base in Intrepid :? )
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```
copy/paste this line to the end of the file:
```
options snd-hda-intel model=*KEYWORD*
```
where *KEYWORD* is one of the following (e.g. dell-eq)
```
STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)
```

---

### Post by Jammanuser on 2010-06-09
> **Temüjin said:**
> You should upgrade to the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
(actually, you should upgrade to Lucid ;) )
You may also need to specify a model keyword in /etc/modprobe.d/alsa-base.conf (or was it just alsa-base in Intrepid :? )
```
gksu gedit /etc/modprobe.d/alsa-base.conf
```

Ok, thanks.
Yeah, its just alsa-base in Intrepid. 
I edited it already, and now I'm going to go install the Alsa upgrade.
I'll let you know if it solves anything or not.
> 
copy/paste this line to the end of the file:
```
options snd-hda-intel model=*KEYWORD*
```
where *KEYWORD* is one of the following (e.g. dell-eq)
```
STAC92HD73*
===========
  ref		Reference board
  no-jd		BIOS setup but without jack-detection
  intel		Intel DG45* mobos
  dell-m6-amic	Dell desktops/laptops with analog mics
  dell-m6-dmic	Dell desktops/laptops with digital mics
  dell-m6	Dell desktops/laptops with both type of mics
  dell-eq	Dell desktops/laptops
  alienware	Alienware M17x
  auto		BIOS setup (default)
```
I used dell-m6, since I believe my laptop has two digital mics built-in and I think the mic jack is considered analog, right? I don't know for certain, but dell-m6 seems like the best choice.

---

