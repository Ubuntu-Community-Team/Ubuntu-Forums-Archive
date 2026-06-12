---
title: "Gnome Mplayer"
date: 2010-09-30
forum: Multimedia Software
---

### Post by trj021782 on 2010-09-30
Hello, just a quick background on what i am running so there is no confusion:

PS3 running Ubuntu 9.10 K ( I refuse to use those ridiculous nick names)

I installed Gnome Mplayer because I want to play HD MKV files and the resounding theme seems to be that Mplayer is the best, i also received good reviews of the Gnome Mplayer front end, there is only one problem - it sucks at playing my HD mkv files. I do not think I am quite skilled enough with linux command lines to be able to use the straight up mplayer so I was hoping for some optimization advice or maybe some info on common rookie mistakes (I am probably making one as I type)

in a funny side note: I tried looking for some Gnome Mplayer plugins to help and found an article that was titled "make mplayer run better when playing hi-def h264 content" the actual article went on to say "by just re-compiling" and yeah, you guessed it - I can't compile to save my life. . . . . .yet

---

### Post by kerry_s on 2010-09-30
> PS3 running Ubuntu 9.10 K ( I refuse to use those ridiculous nick names)

get over it. giving the right info means you get the right help, there is a big difference between ubuntu 9.10 & kubuntu 9.10.

open the gnome-mplayer preferences, click the mplayer tab, put this in the bottom box:
```
-lavdopts skiploopfilter=all
```

& try your hd mkv.

---

### Post by trj021782 on 2010-09-30
I do appologize because i did not make myself clear, I am running Ubuntu not Kubuntu or Xubuntu or Edubuntu - I meant that i find the "karmic koala" and other nick names for ubuntu releases to be stupid - sorry i didn't explain myself properly

Now, I did try the line you offered up and it improved performance a little but it is not yet perfect

---

### Post by kerry_s on 2010-09-30
> **trj021782 said:**
> I do appologize because i did not make myself clear, I am running Ubuntu not Kubuntu or Xubuntu or Edubuntu - I meant that i find the "karmic koala" and other nick names for ubuntu releases to be stupid - sorry i didn't explain myself properly

Now, I did try the line you offered up and it improved performance a little but it is not yet perfect

try this one then, it's for really slow systems:
```
-lavdopts skipframe=nonref:skiploopfilter=all
```

---

### Post by SeijiSensei on 2010-09-30
My understanding is that Ubuntu has very limited abilities to talk to the video hardware on a PS3.  Even though the machine itself is pretty powerful, Sony locked a lot of the proprietary stuff away from the "other OS" users.

What are you using Ubuntu for on the PS3?  If it's mainly to play videos, and you have another computer, available, you might consider putting the media content on the computer and using [PS3MediaServer]("http://http://code.google.com/p/ps3mediaserver/") to stream the content to the PS3.

---

### Post by Yellow Pasque on 2010-09-30
> **trj021782 said:**
> I do appologize because i did not make myself clear, I am running Ubuntu not Kubuntu or Xubuntu or Edubuntu - I meant that i find the "karmic koala" and other nick names for ubuntu releases to be stupid - sorry i didn't explain myself properly
Then just use the version number since you're too l33t to type 'karmic' and had to rant a paragraph instead. Anyway... what kind of video codec is in the matroska container?

---

### Post by trj021782 on 2010-09-30
First of all I am done discussing my distaste for naming schemes, I am only interested in making this OS do what I want

[kerry_s]("http://ubuntuforums.org/member.php?u=132335") - thanks for all the advice, the second command line was an improvement but I still have a bad A/V sync

[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") - wouldn't video decoding rely on the CPU and not the video card? Also I have another computer in the house and we do run PS3 media server on it but it is to slow to decode HD content that is why I wish to do it on the PS3 and cut out the middle man

[Temüjin]("http://ubuntuforums.org/member.php?u=327594") - (the last I have to say on this subject) I don't know what l33t is

as to your question, to my knowledge most if not all of my HD MKV files are h.264

I have also been looking into converting the MKV's to AVI's since most of my files won't really benefit from MKV however because these files occupy the bulk of 2T drive it would require another 2T drive and many months of non stop conversion

---

### Post by Yellow Pasque on 2010-09-30
> I don't know what l33t is but if it is an insult..
It was constructive criticism disguised as helpful advice. ;)

---

### Post by trj021782 on 2010-09-30
> **Temüjin said:**
> It was constructive criticism disguised as helpful advice. ;)

very well, Comment withdrawn

---

### Post by SeijiSensei on 2010-09-30
> **trj021782 said:**
> [SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") - wouldn't video decoding rely on the CPU and not the video card? Also I have another computer in the house and we do run PS3 media server on it but it is to slow to decode HD content that is why I wish to do it on the PS3 and cut out the middle man

Not necessarily.  Remember that Linux distributors like Ubuntu depend on cooperation from hardware manufacturers to create effective drivers for their hardware.  Sony has no interest in being that cooperative because it would have to reveal proprietary features about the PS3's graphics hardware.  Decoding HD streams in formats like H.264 is very processor-intensive.  On a computer with a recent NVIDIA card installed, the computer can offload the decoding process to [specialized software]("http://en.wikipedia.org/wiki/VDPAU") that runs on the graphics hardware itself.  My guess is that a PS3 running Linux simply isn't as capable of decoding HD media as a recent computer with a modern graphics card.

If you're looking for something to connect to your TV to watch HD content, I'd recommend something like [this](http://www.newegg.com/Product/Product.aspx?Item=N82E16856173001&cm_re=ion-_-56-173-001-_-Product).

Looking around on the web about this subject I found this article:
[http://boardsus.playstation.com/t5/PlayStation-3-Media/3D-Accelerated-Graphics-Are-Coming-to-PS3-Linux/m-p/43061234](http://boardsus.playstation.com/t5/PlayStation-3-Media/3D-Accelerated-Graphics-Are-Coming-to-PS3-Linux/m-p/43061234)

Perhaps this might work for you.

---

### Post by trj021782 on 2010-10-01
> **SeijiSensei said:**
> Not necessarily.  Remember that Linux distributors like Ubuntu depend on cooperation from hardware manufacturers to create effective drivers for their hardware.  Sony has no interest in being that cooperative because it would have to reveal proprietary features about the PS3's graphics hardware.  Decoding HD streams in formats like H.264 is very processor-intensive.  On a computer with a recent NVIDIA card installed, the computer can offload the decoding process to [specialized software]("http://en.wikipedia.org/wiki/VDPAU") that runs on the graphics hardware itself.  My guess is that a PS3 running Linux simply isn't as capable of decoding HD media as a recent computer with a modern graphics card.

If you're looking for something to connect to your TV to watch HD content, I'd recommend something like [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173001&cm_re=ion-_-56-173-001-_-Product").

Looking around on the web about this subject I found this article:
[http://boardsus.playstation.com/t5/PlayStation-3-Media/3D-Accelerated-Graphics-Are-Coming-to-PS3-Linux/m-p/43061234](http://boardsus.playstation.com/t5/PlayStation-3-Media/3D-Accelerated-Graphics-Are-Coming-to-PS3-Linux/m-p/43061234)

Perhaps this might work for you.

This is foolish, in your fisrt pot you said that i would have a hard time with HD content because of the lack of a video driver, in your second post you said that SOME computers running CERTAIN software can make the GPU help with HD decoding (Which I already knew about) I am sorry if i am being rude but I HATE it when people repeat what i am saying in a slightly different way - it feels like they are trying to make me look like an ***

---

### Post by SeijiSensei on 2010-10-01
> **trj021782 said:**
> This is foolish, in your fisrt pot you said that i would have a hard time with HD content because of the lack of a video driver, in your second post you said that SOME computers running CERTAIN software can make the GPU help with HD decoding **(Which I already knew about)**

I'm not a mind reader.  Most people know very little about any of these subjects.  I was certainly not trying to demean you in any way.

> I am sorry if i am being rude but I HATE it when people repeat what i am saying in a slightly different way - it feels like they are trying to make me look like an ***

Yes, you are being rude and over-sensitive to boot.  I told you that I thought running Ubuntu on a PS3 was not going to work.  You apparently didn't want to hear that.  I also made a constructive suggestion about a couple of effective low-cost alternatives to using the PS3.  You apparently didn't want to hear that either.  So I'm done with you now.  Good luck with your PS3.

---

### Post by trj021782 on 2010-10-03
> **SeijiSensei said:**
> I'm not a mind reader.  Most people know very little about any of these subjects.  I was certainly not trying to demean you in any way.



Yes, you are being rude and over-sensitive to boot.  I told you that I thought running Ubuntu on a PS3 was not going to work.  You apparently didn't want to hear that.  I also made a constructive suggestion about a couple of effective low-cost alternatives to using the PS3.  You apparently didn't want to hear that either.  So I'm done with you now.  Good luck with your PS3.


No go get f*ck*d, I don't care if its a PS3 or a POS. You handed out b*llsh*t information and now your sore because I called you on it. I said the CPU was responsible for HD decoding because you implied that a good video card was NEEDED and then you retracted your statement because it was ridiculous, so if you don't like people being rude get your facts right the first time.

***EDIT***

ANYWAY - all differences aside I do not care to continue fighting with you in this post, I only care to get answers to my questions and become more experienced with linux. That being said I say again

I am looking for any advice on making Gnome Mplayer or SMplayer run better - right now I can't run standard def video in fullscreen without massive problems and I suspect it is just a matter of choosing the right output driver and settings to make it go smoothly

---

