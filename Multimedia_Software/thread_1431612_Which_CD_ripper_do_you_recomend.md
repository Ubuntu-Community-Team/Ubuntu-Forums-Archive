---
title: "Which CD ripper do you recomend?"
date: 2010-03-16
forum: Multimedia Software
---

### Post by oxf on 2010-03-16
I' having some problems with Sound Juicer. There seems to be  all sorts of unresolved bugs. So I'm going to try another one...

I want to rip from CD to MP3 with a  variable bit rate. Which ripper do you recomend that does the job accurately, high quality with max control of the variables?

Feel free to give your overall comments/experiances!

Thanks!

---

### Post by ron999 on 2010-03-16
RubyRipper
Lame parameters can be set to anything you like.
There's an installation tutorial here:-[http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper]("http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper")

---

### Post by andrew.46 on 2010-03-16
Hi oxf,

> **oxf said:**
>  Which ripper do you recomend that does the job accurately, high quality with max control of the variables?

I still have soft spot for abcde, and I wrote a guide for its use a long time ago:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

The options passed to lame are manipulated with this line in the ~/.abcde.conf file:

```
LAMEOPTS='--preset extreme' 
```

Give it a try, it is a small download and a fast ripper/transcoder.

Andrew

---

### Post by oxf on 2010-03-17
> **ron999 said:**
> RubyRipper
Lame parameters can be set to anything you like.
There's an installation tutorial here:-[http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper)

Thanks for that, especially the tutorial. I'd heard some ref to it when I was searchung around trying to find a fix for the Sound Juicer bugs but not followed up. Seems people prefer it over SJ

> **andrew.46 said:**
> Hi oxf,



I still have soft spot for abcde, and I wrote a guide for its use a long time ago:

HOWTO: Convert music CDs to MP3 using the Command Line.
[http://ubuntuforums.org/showthread.php?t=535950](http://ubuntuforums.org/showthread.php?t=535950)

The options passed to lame are manipulated with this line in the ~/.abcde.conf file:

```
LAMEOPTS='--preset extreme' 
```Give it a try, it is a small download and a fast ripper/transcoder.

Andrew
Thanks

Any other contenders?

---

### Post by oxf on 2010-03-17
> **ron999 said:**
> RubyRipper
Lame parameters can be set to anything you like.
There's an installation tutorial here:-[http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper)

Reading further about Ruby it looks like this might have what I'm looking for! :) I'm a little bothered by the fact I don't see instructions on how to set variables such as CBR/VBR and VBR quality (eg like in the gstreamer pipeline in Sound Juicer) But maybe that comes with the download? Thats my only concern as it looks pretty thorough otherwise.

Before I go and install, however, I'd like to hear any comments on some of the others like AcidRip, Asunder, Ripper X, CDplayer etc or anything else.

Thanks

---

### Post by mc4man on 2010-03-17
Both abcde and rubyripper will accept any valid lame options (lame --longhelp)
RR's are set in the box as seen in screen

(I actually use abcde a bit more, mainly for a slightly easier use of neroAacEnc and atomicparsley, but find rr quite good too. ( have rr set to autorip upon cd insertion

---

### Post by cascade9 on 2010-03-17
> **ron999 said:**
> RubyRipper
Lame parameters can be set to anything you like.
There's an installation tutorial here:-[http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper](http://ubuntuforums.org/showthread.php?t=799621&highlight=Ruby+ripper)

+1. Its the closest thing I've found to EAC in linux. (yay, it actually does test+copy and makes logfiles)

---

### Post by ron999 on 2010-03-17
My screenshot's similar to mc4man's.

---

### Post by oxf on 2010-03-17
> **ron999 said:**
> My screenshot's similar to mc4man's.

Thanks all! That looks a little more like what I expected to see

---

### Post by VanillaMozilla on 2010-03-17
Indeed, Sound Juicer crashes when it can't find data for your CD on line.

K3b has always worked perfectly for me, for CD's and DVD's.  Includes ripping CD's but not DVD's.  It appears to be among the best-written programs.

---

### Post by oxf on 2010-03-18
> **VanillaMozilla said:**
> Indeed, Sound Juicer crashes when it can't find data for your CD on line.

K3b has always worked perfectly for me, for CD's and DVD's.  Includes ripping CD's but not DVD's.  It appears to be among the best-written programs.

I never had problems with Sound Juicer finding data or crashing. It was the unstable VBR ripping, unable to control the VBR rate and wonky file sizes. Searching around revealed this to be an ongoing problem thats still not fixed.

---

### Post by howefield on 2010-03-18
I don't rip that many cds but ripperx does what I need.

---

### Post by andrew.46 on 2010-03-19
Actually I confess these days to ripping a lot of cds 'by hand' with cdparanoia and then tagging and transcoding with oggenc. It is a little more painstaking but the results are always certain :).

Andrew

---

### Post by oxf on 2010-03-20
Well I guess the only thing to do is try several and see what I like!  :)

---

