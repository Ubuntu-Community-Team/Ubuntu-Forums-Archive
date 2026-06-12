---
title: "Why is burning a Video DVD so hard"
date: 2011-04-08
forum: Multimedia Software
---

### Post by Ghost_Mazal on 2011-04-08
Lo guys ,

I am struggling. I have a Video DVD on HDD. Complete structure in VIDEO_TS folder. Problem is I can't find a program to successfully burn it. Brasero doesn't even have an option for Video DVD. The Video DVD option it has wants to try and do encoding or something. It doesn't even take the VIDEO_TS folder. If you choose data disc and burn the VIDEO_TS folder then the disc don't work in stand-alone DVD players and only works on the Linux pc itself.

Gnomebaker has the same problem as above.

K3B doesn't want to work. Just keeps giving the error "Unable to determine size of image".

So where to turn ? Is there an app for Ubuntu that can actually burn a video dvd to be playable in a stand-alone dvd player ?

---

### Post by bobgoblin on 2011-04-08
I've arrived here with the same problem. Thought I had it solved because I have Imgburn on my Windows laptop and found an article on the Imgburn website on how to install in Ubuntu - basically install Wine and use that.
 
I thought Imgburn would be the answer to my troubles but, although it installed ok it can't see the DVD drive. Wine appears to see the drive and label it correctly. Not sure what to do now.
 
I'm using Wine 1.2.2 and Imgburn 2.5.5.0
 
So near and yet so far!!

---

### Post by cotcot on 2011-04-08
> **Ghost_Mazal said:**
> 
So where to turn ? Is there an app for Ubuntu that can actually burn a video dvd to be playable in a stand-alone dvd player ?

Normally it should be enough to burn a data DVD dragging the VIDEO_TS and AUDIO_TS folder to the dvd. If you do not have an AUDIO_TS just make an empty folder with this name.

Yes there is a app in Linux to make a DVD :  it is called [[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html").

Succes

---

### Post by Ghost_Mazal on 2011-04-08
> **cotcot said:**
> Normally it should be enough to burn a data DVD dragging the VIDEO_TS and AUDIO_TS folder to the dvd. If you do not have an AUDIO_TS just make an empty folder with this name.

Yes there is a app in Linux to make a DVD :  it is called [[COLOR="Red"]devede[/COLOR]]("http://www.rastersoft.com/programas/devede.html").

Succes

Simply burning the VIDEO_TS doesn't work. It then only works on the Linux pc like I said.

DeVeDe is not an option. That's for building a DVD compatible output from single video files.

I simply want something that can burn the already completed VIDEO_TS so that it works on stand-alone players.

---

### Post by ron999 on 2011-04-08
> **Ghost_Mazal said:**
> 
K3B doesn't want to work. Just keeps giving the error "Unable to determine size of image".


Investigate this.

Maybe your "Video DVD on HDD. Complete structure in VIDEO_TS folder" isn't suitable.

---

### Post by madjr on 2011-04-08
hi, not sure if you tried all the ones listed here:

[https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

*note: while the link is still relevant, is a bit old, so there might be a few more tools not mentioned there.*

---

### Post by madjr on 2011-04-08
some people had the same problem and found their solution:

[http://ubuntuforums.org/showthread.php?t=823219](http://ubuntuforums.org/showthread.php?t=823219)

[http://ubuntuforums.org/showthread.php?t=1457989](http://ubuntuforums.org/showthread.php?t=1457989)

---

### Post by Ghost_Mazal on 2011-04-08
> **ron999 said:**
> Investigate this.

Maybe your "Video DVD on HDD. Complete structure in VIDEO_TS folder" isn't suitable.

VIDEO_TS on hdd is correct. Just burned it with Win 7 and it works perfectly in standalone player

---

### Post by Ghost_Mazal on 2011-04-08
> **madjr said:**
> hi, not sure if you tried all the ones listed here:

[https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring)

*note: while the link is still relevant, is a bit old, so there might be a few more tools not mentioned there.*

None of that is what I'm looking for , again that is tools to build dvd's from single video files

---

### Post by Ghost_Mazal on 2011-04-08
> **madjr said:**
> some people had the same problem and found their solution:

[http://ubuntuforums.org/showthread.php?t=823219](http://ubuntuforums.org/showthread.php?t=823219)

[http://ubuntuforums.org/showthread.php?t=1457989](http://ubuntuforums.org/showthread.php?t=1457989)

Out of all those only tovid is an app I haven't tried yet. Will give that a go.

---

### Post by Ghost_Mazal on 2011-04-08
Alas Tovid is also just another DVD author app and not what I need.

---

### Post by lemik on 2012-04-24
Here is the answer:

[http://ubuntuforums.org/showpost.php?p=9557968&postcount=10]("http://ubuntuforums.org/showpost.php?p=9557968&postcount=10")

---

### Post by Spc 4 on 2012-04-28
> **bobgoblin said:**
> I've arrived here with the same problem. Thought I had it solved because I have Imgburn on my Windows laptop and found an article on the Imgburn website on how to install in Ubuntu - basically install Wine and use that.
 
I thought Imgburn would be the answer to my troubles but, although it installed ok it can't see the DVD drive. Wine appears to see the drive and label it correctly. Not sure what to do now.
 
I'm using Wine 1.2.2 and Imgburn 2.5.5.0
 
So near and yet so far!!
Open "configure wine" and on the aplications tab click "Imgburn" At the botom of the window it will say "windows version"  change it from XP to windows ME. Press Apply close it and save. Start Imgburn and you should see your DVD drive.

---

