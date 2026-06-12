---
title: "DVD doesn't work after libdvdcss"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by Hex_Mandos on 2007-07-06
Hi, I installed Ubuntu on a laptop you probably never heard of before (Olvetti Olibook 810, assembled and sold in Argentina). It works perfectly with Ubuntu, but I'm having a problem with DVD playback. I installed libdvdcss2 and w32 codecs, and of the 2 discs I tried on it, just one worked. The other gives me an error message, saying it's encrypted. Both DVDs are legally bought (and thus protected) discs, yet one works and the other doesn't. Any ideas?

---

### Post by avik on 2007-07-06
For me, it's always been a bit o f a long shot to play a DVD on Totem or even VLC.  I like gxine, and for me, that's pretty much the only one that works for me in terms of playing a DVD.

```
sudo apt-get install gxine
```

Try using that.

---

### Post by AlanR8 on 2007-07-06
Download Automatix and do the codec install from there.

Faultless install

---

### Post by Hex_Mandos on 2007-07-06
avik: I still get an error message saying the stream's scrambled

Alanr8: Automatix is nice, but can be hard to troubleshoot. Do you know which packages Automatix installs to descramble DVDs beyond libdvdcss2?

---

### Post by david_2001 on 2007-07-06
Not all DVDs are copy protected, so it may be that the one that plays isn't protected and the one that doesn't play is protected.  On that basis, the first thing that I would check is that libdvdcss is properly installed.  The next point is that the w32codecs package is not required to play DVDs.  What is necessary is an mpeg2 codec, for example the libxine-extracodecs package (now called libxine1-ffmpeg) if you are using xine or gxine.

---

### Post by Hex_Mandos on 2007-07-06
After installing the mpeg codec, it's still not playing (again, I get an error message saying it's scrambled). Libdvdcss is installed, and I presume it to be correctly configured since I can play other protected DVDs. The interesting part is that the DVD that won't play works perfectly in my Ubuntu desktop, and I don't remember ever installing anything other than libdvdcss2 from Medibuntu (I certainly didn't use Automatix, as I wanted to learn how to do this manually).

---

### Post by Bablefish on 2007-07-06
Take some advice from someone who HAD the same problem go here and download and install Automatrix
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

Believe me this will fix the problem

---

### Post by RomeReactor on 2007-07-06
Hi. make sure that you have **totem-xine** instead of **totem-gstreamer**, and also the required libraries and extra codecs:
```
sudo apt-get install totem-xine libxine1 libxine1-ffmpeg libxine-extracodecs libdvdnav4 libdvdread3 libdvdcss2 libdvdplay0
```
and then:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
I would advise against installing Automatix; All it does is enable other repositories and somewhat simplify the installation procedure for certain packages (e.g. a single click vs. manually searching and installing required packages), at the cost of probably corrupting your **sources.list**, which seems to be a very common occurrence.

---

### Post by Hex_Mandos on 2007-07-06
I know Automatix. I used it in my Edgy install, but I don't want to use it in Feisty. I'd rather learn. Plus, as RomeReactor says, Automatix isn't magic but another package management tool. I'd rather know what packages to install rather than letting a script do its work. (I'm not strongly anti-automatix, though, as nobody ever told me HOW it kills systems)

Still, I just tried RomeReactor's tips, and the DVD still isn't playing.:( I wonder why it plays on my desktop, but not here.

---

### Post by djrobthaman on 2007-07-06
I think you should just install (re-install?  I didn't see which video player you were using) vlc.  vlc will play pretty much anything.  But if you have it already installed (like I did when I had a similar problem) and install libdvdcss2 afterwards, for some reason vlc doesn't automatically pick up that  installed.  You need to reinstall it so that it knows it's there (that's what it seems like from my experience at least).

You can do this in a few ways.  The easiest is to go to Applications -> Add/Remove Programs.  Then on the top right corner there's a drop down menu that asks you what kind of programs you want to be able to see when you search.  Select "all available applications"  Then search for vlc (or videolan) and download.

Anyway, have fun watching your movies now.

---

### Post by Hex_Mandos on 2007-07-07
Nope. Still not working (tried installing VLC and reinstalling totem-xine), I'm considering the possibility of a hardware problem, but I'd have to install Windows to troubleshoot it (and I don't want to activate Vista, I'm trying to get a rebate from MS).

---

### Post by Hex_Mandos on 2007-07-07
A friend helped me out. Turns out that the region wasn't set correctly. I hate media companies, a pirated DVD would've worked perfectly out of the box.

---

### Post by myotheralt on 2007-07-08
ok, my dvds play, but the video is jacked up.  i installed AUD-DVD codecs and Multimedia codecs through Automatixs and i am running gxine, but i have the same problem in Kaffeine and totem.  audio is fine.  here is a pic [http://myotheralt.blogspot.com/](http://myotheralt.blogspot.com/)

---

### Post by RomeReactor on 2007-07-09
Hi **myotheralt**, the video looks like it's still scrambled; did you run:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
after installing the codecs?

---

