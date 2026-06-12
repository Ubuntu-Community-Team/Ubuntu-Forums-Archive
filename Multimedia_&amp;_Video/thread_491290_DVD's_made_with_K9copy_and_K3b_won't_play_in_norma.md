---
title: "DVD's made with K9copy and K3b won't play in normal dvd players?"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by andyanderso on 2007-07-03
I have been trying to back-up some of my movie collection and I want all the menus and extras on the DVD.  K9copy has been super easy to use to do this, but when I burn them they play just fine in my computer but not in DVD player's or on my wife's Apple laptop.  Does anyone else have this problem and/or does anyone know how to solve it?

andy

---

### Post by SPRL on 2007-07-12
hey Andy...

I have the same problem. I can play it on my computer and on my Philips 727 dvd player, but I've tried the disks in 4 other dvd players and it would not play. I'm wondering if its an option in K3b that we are missing or a problem with region or version. I'm thinking that because I hacked my Philips 727 to play all region codes and both NTST and PAL. and its the only one so far that will play them, besides my computer...

dvd burner I'm using LG GSA-4163B.

---

### Post by maxjivi05 on 2007-07-12
I've had that problem for awhile, I was using Avidemux / Varsha / K3B to burn my Movies. I come to find out half the movies made that way would not play in a lot of DVD players... So I tried a few other programs "Its not the burning software its the DVD Compiling Software"

The Software I used to fix this mess well heres a few I found to work...

1. DeVeDe "Makes you're DVD ISO / Burn with K3B"
2. ManDVD "Makes you're DVD ISO but won't encode Audio to AC3 so you have to do that with Avidemux first"

If there are any better programs for this let me know, I've found DeVeDe very useful and pretty neat to play with.

---

### Post by andyanderso on 2007-07-19
That is good to know.  I will go back to trying DeVeDe.  The one thing about it is that I would really like to have all the menus and subtitles and stuff that is on the original DVD.  K9Copy does this so easily and I don't know how to do it with DeVeDe.  Can it be done?  If so how?

There must be a way to make K9copy work...what all have you guys tried in terms of k9copy options?

andy

---

### Post by RamblinMushroom on 2007-10-31
I have the same problem... Anyone figure this out yet?

---

### Post by fiskking on 2007-12-27
well, I´ve tried w/ DeVeDe and K3B and was successful in burning a DVD.  The only problem is that it works on only 1/5 DVD players that I own.    I had to adjust the bit-rate (from 5000 to 500) in order to compensate for disk space.  

dvd: philips DVD +R , 4.7GB 

Burner: LG 18x Super Multi DVD GSA-E40L

---

### Post by wjston on 2007-12-28
> **andyanderso said:**
> I have been trying to back-up some of my movie collection and I want all the menus and extras on the DVD.  K9copy has been super easy to use to do this, but when I burn them they play just fine in my computer but not in DVD player's or on my wife's Apple laptop.  Does anyone else have this problem and/or does anyone know how to solve it?

andy

I was having the same problem until just this past weekend. I uninstalled K9copy using Synaptic Package Manager and then I compiled the latest version. During this process, I believe I discovered a couple of libraries that I was missing since I upgraded to Gutsy. Follow this link and make sure you have all the necessary libraries installed (post #26): [http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy&page=3](http://ubuntuforums.org/showthread.php?t=607991&highlight=k9copy&page=3)

Pay special attention to these two: ibavcodec-dev and libaformat-dev. After building from source, I have been able to play my DVD's on my home DVD player. If K9copy crashes while opening a disc, it is due to the encoding. So far, I have only had this happen once since I did the build from source. Hope this helps.

---

### Post by cowboyjo on 2008-03-02
There is a more recent, related thread at [http://ubuntuforums.org/showthread.php?t=696668](http://ubuntuforums.org/showthread.php?t=696668) (" Burnt dvds wont play in standalone player")

---

### Post by dexterchief on 2008-03-04
I am pretty sure that most DVD players only play -R disks...

---

