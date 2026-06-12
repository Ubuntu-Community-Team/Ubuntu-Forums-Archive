---
title: "Making a DVD from the VIDEO_TS Folder"
date: 2007-09-21
forum: Multimedia &amp; Video
---

### Post by Whitewater155 on 2007-09-21
Hey everyone,

I'm trying to figure out how to make a Video DVD from the VIDEO_TS Directory of the original DVD. I want it to work on my DVD player hooked to the TV.   

If I were still using Windoze, I'd use ImgBurn, but I'm now 100% Linux (ubuntu). Even on Windoze, I'm pretty much clueless when it comes to making DVDs.

It there anything under Linux that will make the DVD?

Thanks in advance
Dave :confused:

---

### Post by Alex1200GS on 2007-09-22
A DVD is supposed to have two folders, one named VIDEO_TS and another named AUDIO_TS. The latter is not used but has to be there for some reason.

So, I'd use Gnome Baker to copy the entire contents of the original DVD into the new disk and presto!
If you don't have a DL burner and need to squeeze the files into a SL disk, then you should use another utility for this purpose, but I'm also a linux newbie and can't help you with this, sorry. In Windows I'd use DVDfab. 

Alex

---

### Post by Gremlinzzz on 2007-09-22
If you want too burn dvd image K3B would be the burner i would use.

---

### Post by srt4play on 2007-09-22
I will second K3B I use it exclusively for this purpose and it works great.

---

### Post by RomeReactor on 2007-09-22
Hi. I also recommend K3B. In it, look in the **Tools** menu for "Video DVD"; then just copy the contents of your VIDEO_TS folder to the one K3B will provide you, and burn it.

---

### Post by Whitewater155 on 2007-09-22
Hey everyone,

Thanks for the replies. I used K3B and it worked like a charm. :) 

Dave

---

### Post by skralljt on 2008-03-14
I did this very thing but K3b responds that there are files missing "The project does not contain all necessary videodvd files."  I will throw a random wav file into the audio_ts folder, but how annoying!  I tried a data dvd but that isn't read by mplayer, vlc, or "movie player", whatever that is.  vlc will play some of the vob files though, so i know that the data is there.

---

### Post by megamania on 2008-04-02
> **skralljt said:**
> I did this very thing but K3b responds that there are files missing "The project does not contain all necessary videodvd files."  I will throw a random wav file into the audio_ts folder, but how annoying!  I tried a data dvd but that isn't read by mplayer, vlc, or "movie player", whatever that is.  vlc will play some of the vob files though, so i know that the data is there.
I was having the same problem. After some searching, what I understood is that VOB files are not enough, and you need an "authoring" tool to create the proper dvd structure.
The best solution seems to be to use a program like devede (in synaptic). You drag and drop your vob files there, then you can either create an ISO (and burn it with k3b) or the file structure for the DVD.

Here's where I found most on this info;
[http://www.mepislovers.org/forums/showthread.php?t=11626](http://www.mepislovers.org/forums/showthread.php?t=11626)

Hope that helps! Things that look easy are never easy (at least to me!)...

---

### Post by disturbedite on 2008-04-02
if you have the VIDEO_TS folder & its 4.3GBs in size, you can simply burn it as a data disc with any burning software.

---

### Post by megamania on 2008-04-02
> **disturbedite said:**
> if you have the VIDEO_TS folder & its 4.3GBs in size, you can simply burn it as a data disc with any burning software.
Of course, **if** you have the **full** VIDEO_TS folder. My suggestions apply to the problems you may experience if you only have the VOB files.

---

### Post by disturbedite on 2008-04-03
> **megamania said:**
> Of course, **if** you have the **full** VIDEO_TS folder. My suggestions apply to the problems you may experience if you only have the VOB files.
ok.  but mine didn't, so what.  he asked, so i assumed he didn't know.

---

### Post by megamania on 2008-04-04
> **disturbedite said:**
> ok.  but mine didn't, so what.  he asked, so i assumed he didn't know.
Please see what I quoted in my first post. He was wondering why K3B was complaining about missing files. I tried to help with that problem.

Cheers.

---

