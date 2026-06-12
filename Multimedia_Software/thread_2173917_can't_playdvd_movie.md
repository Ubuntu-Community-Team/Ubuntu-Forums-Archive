---
title: "can't playdvd movie"
date: 2013-09-11
forum: Multimedia Software
---

### Post by macstl on 2013-09-11
I looked it up here at the restrictedformats/playing dvd's and followed instructions the last of which is to execute the file install-css.sh which I can't get to work even if I go all theway the directory it is in. I use sudo and I checked to make sure it is executable ok. It keeps telling me command not found. I do a ls and it is there ok. Any idea of what is going on here.
I use ubuntu 12.04 desktop.
the dvd is "Southland Tales" printed in USA

---

### Post by perspectoff on 2013-09-11
Try one of these methods for installing libdvdcss instead:

[http://ubuntuguide.org/wiki/Ubuntu_Precise_Audio_Video_Conversion#DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu_Precise_Audio_Video_Conversion#DVD_Playback_Capability)

The script you referenced (from libdvdread4) for installing libdvdcss2 relies on Medibuntu (I believe), which is now unmaintained.

---

### Post by zombienerd1 on 2013-09-12
It may not be the solution you were looking for, but have you tried VLC and used the Open Disc feature?  I'm pretty sure it will natively play DVD's without any dependency on other software.

---

### Post by macstl on 2013-09-12
zombienerd1 @   Is that any different than inserting the dvd and then selecting VLC to play it? That I have done to no avail.

---

### Post by i-420-man on 2013-09-12
i have a similar problem. I cant play DVDs ether I have VLC and it loads DVDs but wont play them im running Ubuntu 13.04 also used  	[**[COLOR=#000000]perspectoff[/COLOR]**]("http://ubuntuforums.org/member.php?u=257693") 	 's repositories and still nothing

---

### Post by macstl on 2013-09-12
perspectoff:@
when i enter sudo add-apt-repository deb [http://download.videolan.org/pub/debian/stable/](http://download.videolan.org/pub/debian/stable/) /
i get message= need a repository as arguement

when I try to install 64 bit windows multimedia codecs
it tells me it can'tfind w64codecs in drive e:

---

### Post by macstl on 2013-09-12
perspectoff:@
I put a ' before deb and after stable// and then it worked.
I can now play dvd movie in VLC
thank you a lot

---

### Post by perspectoff on 2013-09-21
[https://www.videolan.org/developers/libdvdcss.html](https://www.videolan.org/developers/libdvdcss.html)

is the VideoLAN tutorial

---

### Post by macstl on 2013-09-21
> **perspectoff said:**
> [https://www.videolan.org/developers/libdvdcss.html](https://www.videolan.org/developers/libdvdcss.html)

is the VideoLAN tutorial

Thanks!):P

---

