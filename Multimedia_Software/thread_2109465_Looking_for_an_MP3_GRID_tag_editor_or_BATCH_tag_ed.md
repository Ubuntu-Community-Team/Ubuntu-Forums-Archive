---
title: "Looking for an MP3 GRID tag editor or BATCH tag editor"
date: 2013-01-27
forum: Multimedia Software
---

### Post by cforput on 2013-01-27
Do any of the tag editors have a grid edit format? I tried puddletag but it kept putting blank gray windows over the app every time I opened a new folder so it's useless. 

Any suggestions?

---

### Post by ajgreeny on 2013-01-27
I don't know what you mean by grid edit, but have a look at tagtool or easytag, both in repos (for 10.04, not sure about 12.04 or 12.10).

---

### Post by tgalati4 on 2013-01-27
Easytag is in 12.10:

tgalati4@Dell600m-mint14 ~ $ apt-cache policy easytag
easytag:
  Installed: (none)
  Candidate: 2.1.7-2
  Version table:
     2.1.7-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe i386 Packages

I'm a BIG fan of grid-editing--whatever that is.  If you mean stamping several files with the same field, then yes, easytag can do that.

---

### Post by cforput on 2013-01-28
What I mean by a grid is think of Libre Office Calc or MS Excel. I want to open a folder of mp3 songs and have them show up in a "grid" so I can quickly copy / paste, edit, add info in a grid. 

I've looked at EasyTag and you have to tediously edit one song at a time. I'm looking for something much quicker and easier.

---

### Post by andrew.46 on 2013-01-29
> **cforput said:**
> Do any of the tag editors have a grid edit format? I tried puddletag but it kept putting blank gray windows over the app every time I opened a new folder so it's useless. 

Seems a little odd, might be well worth your while investigating exactly what is causing the puddletag error. I post a screenshot here to show others what I assume you are after (the 'grid').

---

### Post by cforput on 2013-01-30
Thanks. Yes, that's exactly what I am looking for. I will search around see if I can get a lead on the error in puddletag.

---

### Post by cforput on 2013-02-01
I did some research and found a work around to the puddletag problem so I'm using that. Quite a handy tool.

I was using Cinnamon as my UI and what I found was that people were reporting issues with the pop up boxes not going away. I switched to gnome and the problem disappeared. Not my preference but I just change back and forth between Cinnamon and Gnome when I know I want to do some tag editing.

I'm marking this as solved.

---

### Post by sycorix on 2013-02-27
Hi!

I have the same problem of the popup window not closing in Cinnamon. It even stays visible after closing EasyTag. 
I found out that you get rid of the popup window by restarting Cinnamom (Alt-F2 r). The Cinnamon restart will not close the running applications.

Cheers,
Sycorix

---

