---
title: "Burning MP3 CDs (for the car)"
date: 2012-02-03
forum: Multimedia Software
---

### Post by e4xit on 2012-02-03
Hi,
 
So I am quite new to Ubuntu (and these forums) so apologies if this is in the wrong sub-forum or anything.
 
I am trying, as the title says, to burn MP3 CDs for use in my car. NOT burn MP3s to regular audio CD - there are a ton of apps for that and I found them, thanks :D
 
I am aware Brasero has a "data CD" function, but have tried this and it didnt work in my car (but to be fair I'm not sure about the burn quality as it was on a laptop, might try slower burn later).
 
What I am worried about is the fact that iTunes [ :-\" ] has three options when burning to disc:
1) Audio CD
2) MP3 CD
3) Data CD
and I am worried brasero is doing the equivalent of option 3 here, which perhaps is not quite the same as option 2 (although again, I must admit I dont know this for sure: perhaps options 2 and 3 are the same except 2 has no folder structure??)
 
Was just wondering if someone knew for sure how to do this as google turns up only results of how to burn .mp3s to audio CD (ie convert to .wav first), whether I need another program etc...
 
Anyway sorry for the essay, just wanted to avoid any confusion!!
 
Linux love
x
 
:tongue:

---

### Post by Steeperton on 2012-02-03
Burn it as a Data CD. As far as I'm aware, there's no difference between "Data CD" and "MP3 CD"

I'd have thought the problem was with the burn itself.

---

### Post by ajgreeny on 2012-02-03
You mention iTunes, and that worries me a bit as I wonder whether the DRM problem is causing your difficulties.

I hasten to add that I have never used, nor even seen iTunes in action, so I may be speaking out of turn here, however, it is worth checking out.

---

### Post by e4xit on 2012-02-03
OK Steeperton I will give it another go then.
 
A little more intensive googling (of the difference between the two in iTunes) returned that MP3 CD will only burn MP3 files whereas data CD will burn MP3 files *and* any video files/other files if they are in the same playlist, which kinda seems pretty obvious now I know.
 
Guess I just thought:
Audio CD - CD players
MP3 CD - MP3 CD players
Data CD - Computers etc
 
Should I change thread type to "Solved" or something? (sorry its probably in the readme but im at work right now)
 
Thx

---

### Post by zaentzpantz on 2012-02-03
You should be fine with "data cd", I've done that with no problems and it works. Try burning at 8x speed. Modern hi-speed CDRs have such a thin layer that a high speed burn may give "just acceptable" results but a slow speed really makes sure it burns well.

---

### Post by shantiq on 2012-02-03
hi there e4xit       MP3 CD is another name for data Cd containing mp3s

see [**here**]("http://www.freerip.com/frmmanual/tutorials/what_is_an_mp3_cd.php")


so yes brasero or k3b or any program will make a data CD/mp3 CD with no problems

**ONLY PROBLEM WILL BE** does your CD player in your car handle data CDs

my stereo at home which is ancient only plays audio CD    only in the last five years or so do stereos handle data discs too


so i would look into that if you have not already...

---

### Post by cb5online on 2012-12-30
I'm going to try burning at 8x speed myself too, as I have had the same issue.
The car cd player happily plays data CDs made with Windows XP third party software, but with Ubuntu's default burner, it only plays the first 20 seconds of some songs, completely misses out others seemingly at random. But it's the same songs which like someone else mentioned indicates an issue with the burn itself. Hmm..
I'll report back if I have success.

---

### Post by Zteam on 2012-12-30
Try K3b and see if that works better for you.

---

### Post by cybrsaylr on 2012-12-30
I've used both K3B and Brasero and burned as "data CD" with no problems in the past. They play mp3s on any player that recognizes the mp3 format including my car. 

Never used iTunes and never plan to.

---

### Post by cb5online on 2013-01-03
I can confirm that burning at 12x speed (which is the slowest mine goes to) doesn't work, same problem. I've also tried DAO and SAO, neither of which worked.
I'm getting more than a little frustrated. 
Are there any other apps which I might try, that anyone could recommend?

---

### Post by evilsoup on 2013-01-03
Have you tried XFburn? Or K3B, as others have suggested.

If neither of these work (and they should, XFburn works like a charm for me), you can try using [ImgBurn](http://www.imgburn.com/), which is a Windows program, but one that runs perfectly under wine - and I consider it to be the best burning program on any platform.

---

### Post by cb5online on 2013-01-04
Ok - I've also tried gnomebaker - at 4x speed - and my cds are still not readable. 
If anyone has any advice I would appreciate it.

---

### Post by cb5online on 2013-01-04
> **evilsoup said:**
> Have you tried XFburn? Or K3B, as others have suggested.

If neither of these work (and they should, XFburn works like a charm for me), you can try using [ImgBurn]("http://www.imgburn.com/"), which is a Windows program, but one that runs perfectly under wine - and I consider it to be the best burning program on any platform.

I've just seen this post, oops. I'll try that now, thanks!

---

### Post by evilsoup on 2013-01-04
If it turns out that even ImgBurn doesn't work, I'd suggest that the problem is probably with your hardware (either the burner or what you're playing it on).

---

### Post by cottfcfan on 2013-01-05
Try NeroLinux from here, you can trial it for free.
If that doesn't work I suggest you have a hardware problem.
Also make sure you have the ubuntu-restricted-extras package installed, although I doubt that will be the issue.
[http://www.nero.com/enu/downloads-linux4-update.php](http://www.nero.com/enu/downloads-linux4-update.php)

---

### Post by cb5online on 2013-01-05
Thanks everyone, I really appreciate your help.
ImgBurn is a cool program, thanks... but you're going to want to throw things at me of an unsavoury nature...
Turns out the issue wasn't with the software or the hardware but with the downloaded music files. They wouldn't play on the pc either, What a noob thing to do. 
I've scrapped the idea of listening to Anti Flag, now on with Coal Chamber and Stone Sour... lol! I'll report back later but pretty sure that's all it was.
I now have four cd writing apps on my pc. Choice! :D

---

