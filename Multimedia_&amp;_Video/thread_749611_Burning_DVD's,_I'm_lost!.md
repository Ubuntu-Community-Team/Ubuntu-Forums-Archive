---
title: "Burning DVD's, I'm lost!"
date: 2008-04-08
forum: Multimedia &amp; Video
---

### Post by LinuxDumDum on 2008-04-08
I'm needing some help on how I get my avi movie files formatted correctly and burned. My husband is always working, and doesn't really have time to help me with this so can someone explain in simple way how I do this?.  I have a ton of DVD+R"s , so I would like to use those. Also we have the DeVeDe app.  We are new to Linux, so I really have no idea what I'm doing.. :)

---

### Post by tamoneya on 2008-04-08
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_burn_video_DVD](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_burn_video_DVD)
```
sudo apt-get install dvdauthor
```

---

### Post by ron999 on 2008-04-08
Hi
dvdauthor might be a bit difficult if you've not had much DVD experience.

You can use DeVeDe to make a DVD from an avi file.
Use the option 'Create an ISO or BIN/CUE image..
Then you can burn that image to a DVD+R using K3b (Select Tools > Burn DVD ISO image)

---

### Post by soga_genzo on 2008-04-09
> **LinuxDumDum said:**
> I'm needing some help on how I get my avi movie files formatted correctly and burned. ...Do you have a DVD player that supports play back of AVI files? Or do you want to create "normal" DVDs that are playable on every DVD player? If it's the latter you'll have to convert your AVI files into a DVD-compliant format first. Have a look a this tutorial then: [Converting to DVD with Avidemux](http://www.avidemux.org/admWiki/index.php?title=Converting_to_DVD). You can get the latest version of Avidemux [here](http://www.getdeb.net/app/Avidemux).

---

### Post by groovomata on 2008-04-11
> **ron999 said:**
> Hi
dvdauthor might be a bit difficult if you've not had much DVD experience.

You can use DeVeDe to make a DVD from an avi file.
Use the option 'Create an ISO or BIN/CUE image..
Then you can burn that image to a DVD+R using K3b (Select Tools > Burn DVD ISO image)

I find that using Devede to convert avi files to dvd format results in a playable dvd, however sometimes there are little skips in the audio track. Currently I'm encoding an avi file using Avidemux to see if that works better.
Erik.

---

### Post by ubuntu-freak on 2008-04-11
You could also give Tovid a try. There is info and links in part 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). Tovid has two GUIs to choose from - "Simple" (tovidgui) and "Fancy" (todiscgui). Yeah, the names are a bit crappy, but it's a work in progress. :-) 
 
Nathan

---

### Post by groovomata on 2008-04-24
Thanks for that, I'll give it a try!

---

