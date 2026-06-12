---
title: "Burning an audio CD with Serpentine doesn't work"
date: 2007-04-10
forum: Multimedia &amp; Video
---

### Post by KanadaKid on 2007-04-10
Hi,

I am running Ubuntu Edgy, and I'm having a problem trying to burn audio CDs. I tried to make such a CD, containing only mp3 files, with Serpentine. However, when I try to burn the disk (Write to Disk), nothing happens. I tried removing some files, assuming that perhaps a certain one was corrupt, but to no avail. As a last resort, I started Serpentine through the command line, but no error messages were displayed when I, once again, unsuccessfully tried to burn the CD. At this point, I'm not sure as to what I can do to fix this problem.

Any ideas? Thanks in advance!

---

### Post by indica on 2007-05-01
bump, same problem

---

### Post by UncleFoo on 2007-05-07
Make that 3. Same problem here.

---

### Post by UncleFoo on 2007-05-07
Update - I was able to burn .wav files to a CD as Data files Using Nautalus. But Serpentine does nothing when you click "write to disk". No errors, beeps, notification of any sort.

---

### Post by UncleFoo on 2007-05-08
Ok so nobody wants to respond. Here is what I did, I tried several CD Burners until I found one that worked. Side note: I am doing home recording and mixing and I want to put the files on to an audio CD

Here is what I tried
xcdroast - Result - What the hell? You need to run it as root and set up a config file, and then run as user and do something else and then do 6 other things..... Screw that! - gone

Banshee - Seems cool but I could not load any files into the library. It would zip through my .wav files and kick each one out with an error (and not a descriptive error either) - gone.

GnomeBaker - Yay! install it find the files, press burn and ...... it works! Thats all I want, something that works, without a ton of screwing around.

Why is this so friggin hard? I bought the official Ubuntu book, what a waste of money. "To burn a CD, use serpentine". Great! What if it doesn't work? No answers. Go to the forum, no answers. Screw around until you stumble onto an answer. What is this, Windows?

End Rant.

---

### Post by Madmoose on 2007-05-08
TTT

Doesn't work for me also. Not on any of my three Ubuntu computers. 

Moose

---

### Post by Madmoose on 2007-05-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/serpentine/+bug/77655](https://bugs.launchpad.net/ubuntu/+source/serpentine/+bug/77655) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hey, 

I wen to log a bug, and I found this bug. 

I'm about to give it a try. 

Moose!

---

### Post by UncleFoo on 2007-05-08
Cool, can't wait to hear how it works out.

In the meantime I found this article about trying to burn A CD using M$ Vista

[http://www.groklaw.net/article.php?story=20070422083715451](http://www.groklaw.net/article.php?story=20070422083715451)

OK Ubuntu all is forgiven, you suck less than Vista. Answers are available (with some digging), and you don't try and force me into a DRM nightmare.

:guitar:

---

### Post by Madmoose on 2007-05-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I got it installed, and the "Write to CD" worked. It did it thing, and asked me to put in a blank disk. This was odd, cuz there was one in there. Okie then... Open close the disk drive. Still nothing: Found my self in this bug:


[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/66254)

Needless to say... I'm still without an audio CD.

Moose

---

### Post by UncleFoo on 2007-05-09
Mad Moose

Maybe I can help. As far as getting your player to work and any other sound card issues try easyubuntu.

[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

I t has all the drivers that are missing in the normal install, it got a lot of stuff working for me. And for a CD writer search for gnomebaker in synaptic. It works for me first try.

Good luck.

---

### Post by Dave67 on 2007-05-09
Mp3 support is not included by default so you must install the support. I like K3B burning  program to do this and it is not hard to install the mp3 support that it needs. If you have the restricted repositories etc enabled you can search in synaptic for K3B and install these files below. 

k3b
libk3b2-mp3 ( this will help lots :) )
libk3b2 (this one may be selected automatically)

after 3kb and the libs install, there will be a entry in your launch menu under multimedia I believe. 


I like this program since it can rip a CD and burn CD's all in one program and I uninstalled juicer since this does it all. I still use Rhythmbox to play my music.


dave

---

### Post by KanadaKid on 2007-05-11
Indeed, by following Dave67's suggestion, I now have a functional k3b that can burn my audio CDs. I still haven't tried Serpentine yet after installing k3b, but I've used the latter in the past, and so I'm satisfied now. ;)

Thanks!

---

### Post by stchman on 2007-05-11
> **KanadaKid said:**
> Hi,

I am running Ubuntu Edgy, and I'm having a problem trying to burn audio CDs. I tried to make such a CD, containing only mp3 files, with Serpentine. However, when I try to burn the disk (Write to Disk), nothing happens. I tried removing some files, assuming that perhaps a certain one was corrupt, but to no avail. As a last resort, I started Serpentine through the command line, but no error messages were displayed when I, once again, unsuccessfully tried to burn the CD. At this point, I'm not sure as to what I can do to fix this problem.

Any ideas? Thanks in advance!

I have never had much luck with Serpentine.  I use K3B for all my CD burning duties and Sound Juicer for all my CD ripping duties.  Between those two programs I feel pretty good.

Refer to my homepage on CD/DVD ripping/burning/mp3s/etc.

[http://www.stchman.com](http://www.stchman.com)

---

