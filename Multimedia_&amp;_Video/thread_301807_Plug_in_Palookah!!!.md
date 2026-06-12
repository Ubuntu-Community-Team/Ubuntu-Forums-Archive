---
title: "Plug in Palookah!!!"
date: 2006-11-17
forum: Multimedia &amp; Video
---

### Post by John Murphy on 2006-11-17
Yesterday I installed dapper on a Friends Toshiba Satellite and edgy on my Dell Inspiron - Apart from the pure horror install for edgy compared with Dapper:

 (*Dapper takes 20 minutes - has a lovely wizard-type interface and even the grub manager is nice for dual booters... / edgy takes about an hour and a half, you're left sitting in front of a black screen, get GUI bugs in the process and  is nowhere near as nice or informative as Dapper in terms of start up etc.*

I find various inconsistencies. The one that's bugging me most right now being Firefox plugins for .mov content in particular.

I have loaded AutomatixII codecs even downed MPLayer codecs separately as RPMs - converted them to debs and installed them - even tried the media player manager add on (which only made things worse...) all this on Edgy and nothing seemingly will fix the problem. Before I mention the problem(s) I will state that in Dapper there is no siuch problem - same sources used!!!

**_The Problem_**
Try accessing any of the tutorials at [http://digitaltutors.com](http://digitaltutors.com) and you get thrown out with totem errors every time (I removed gstreamer and installed xine but this made no difference at all)

Typically I am met with 'Totem could not play'..... messages.

That is only half the injury however, I dont want them to play in Totem in the first place but in MPlayer like they do in Dapper. Not only that but  I would like support too for DivX and maybe XVid

So what's changed in that following identical insatall routines for two Ubuntu releases I get totally contrasting results? More importantly - how can I get Firefox associated with MPLayer? The options in the manage > content tabs are lightweight to say the least. No mention of the more popular formats such as .mov, .wmv. divX etc - let alone options to associate them with a preferred player like MPlayer as opposed to Totem. I've spent hours googling to try resolve this issue and all I've really come up with so far is a lot of folk with similar issues and not much in the way of answering my particular question. Could it be that Totem quite possibly sucks????

Regardless of what platform I find myself on I would like at the very least be able to view embedded content in popular formats such as .swf, .mow. wav.divX and even the crummy flv and other new 'quirks' from Micro$oft. It's not much to ask especially when recently they have held talks in Athens (Greece) vis a vis globalizing the Web.

Anyone have a QUICK fix for this prob????

Thanks in advance

---

### Post by John Murphy on 2006-11-18
sudo apt-get helpful feedback from someone Pleez
bash my friends dapper lookslike it's in real trouble too after only 2 days - he has lost add remove prorams and apps continually crash

---

### Post by John Murphy on 2006-11-19
bump - again!

---

### Post by rougecoder007 on 2006-11-20
Hello.  Just a quick mention that I have Dapper and Firefox 2.0 and I am getting the same problem with that site.  I attempted to view a movie but got the totem error.  I then went into preferences and tried to modify the action for a quicktime movie.  Though there was no option for the .MOV extension, there was one for quicktime.  Upon modifying that the same thing occured.

Just to let you know that at least someone listened.  I will play a little with it and if I find a fix will post.

Good luck.

---

### Post by aleska on 2006-11-20
Do you have a problem playing all .mov files from websites, or just those from digital tutors?  I ask b/c I too got an error about totem not being able to find file.  I tried mplayer from terminal:
```
mplayer http://www.digitaltutors.com/web/flash/683/683.mov
```
as I find mplayer can usually run things that don't seem to work as embedded in browser.  Anyway, got a weird result:
```
Playing http://www.digitaltutors.com/web/flash/683/683.mov.
STREAM_HTTP(1), URL: http://www.digitaltutors.com/web/flash/683/683.mov
Resolving www.digitaltutors.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.digitaltutors.com
Resolving www.digitaltutors.com for AF_INET...
Connecting to server www.digitaltutors.com[67.15.145.172]: 80...
Server returned 404: Not Found
STREAM_ASF, URL: http://www.digitaltutors.com/web/flash/683/683.mov
Resolving www.digitaltutors.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.digitaltutors.com
Resolving www.digitaltutors.com for AF_INET...
Connecting to server www.digitaltutors.com[67.15.145.172]: 80...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
STREAM_HTTP(2), URL: http://www.digitaltutors.com/web/flash/683/683.mov
Resolving www.digitaltutors.com for AF_INET6...
Couldn't resolve name for AF_INET6: www.digitaltutors.com
Resolving www.digitaltutors.com for AF_INET...
Connecting to server www.digitaltutors.com[67.15.145.172]: 80...
Server returned 404: Not Found
File not found: 'www.digitaltutors.com/web/flash/683/683.mov'
Failed to open http://www.digitaltutors.com/web/flash/683/683.mov.


Exiting... (End of file)

```

---

### Post by kerry_s on 2006-11-20
Try linuxmint-> [http://lt.k1011.nutime.de/about.html](http://lt.k1011.nutime.de/about.html)

---

### Post by John Murphy on 2006-11-21
Am having problems with other sites as well as files I already have on my HD. In the past MPlayer has been fione for opening them as it was a few days ago on my friends machine running Dapper- so why do I have the problem on Edgy?

I don't like Totem as a preferred player anyway - and that thtrows up another bunch of problems. Totem wont open many files and when I try to open them with MPlayer I'm getting I/O error messages all the time - in fact around 95% of filers are the same....

---

