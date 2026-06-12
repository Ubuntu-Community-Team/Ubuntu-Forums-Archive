---
title: "Missing Rhythmbox ID3 tag demuxer plugin"
date: 2009-07-19
forum: Multimedia Software
---

### Post by Rowan Berkeley on 2009-07-19
Apparently this problem came up with previous versions of Rhythmbox, and a fix was supposedly found and applied, but I have Ubuntu 9.04 and the latest Rhythmbox release, and I still get the problem. What it is is that on every startup of Rhythmbox it asks to search for a missing ID3 tag demuxer plugin and then fails to find one. Previous discussions have stated that there is one inside one of the "good", "bad" or "ugly" gstreamer plugins accessible via Synaptic, and I have installed pretty well all of them (obtained using the keyword "gstreamer" in the Synaptic search box), and still the problem recurs.

The previous discussion to which I refer is here:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343707](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/343707)
and there is some mention of "good", "bad" and "ugly" plugins here:
[http://ubuntuforums.org/archive/index.php/t-333690.html](http://ubuntuforums.org/archive/index.php/t-333690.html)
but it is two years old and rather inconclusive.

---

### Post by vinutux on 2009-07-19
Try banshee instead of Rhythmbox.....

```
sudo apt-get install banshee
```

---

### Post by Rowan Berkeley on 2009-07-19
I have tried Banshee (which incidentally is markedly inferior to Rhythmbox in its ability to read tags), but Rhythmbox is the default music player for all versions of Ubuntu, and this is a long-running bug. I don't think it's unreasonable to expect a fix for it.

---

### Post by Stochastic on 2009-07-20
Thread moved to Multimedia & Video.

It should be noted that Rhythmbox development is in the process of shutting down (if it hasn't fully died already); the core developer cited the inflexible backend as the main reason to stop.  So due to lack of upstream development there's a major likelihood that the bugs you experience now will continue to be experienced for years to come.  Future Ubuntu versions will no doubt have a different default music player.  

However, the beauty of the GPL license allows you or the community at large to do whatever you like with the Rhythmbox codebase, so if you feel like coding up a solution to that bug, you're welcome to it....     ...just be aware that the previous developers of that codebase got sick of dealing with the headaches inherent in it.

---

### Post by Rowan Berkeley on 2009-07-20
I shall not regard that as a thread-closing comment. Rhythmbox is still being used on new distributions of Ubuntu -- I bought my current computer brand new, two weeks ago, with Jaunty ready installed, and this is what I got. I expect a constructive reply.

---

### Post by bardictiger on 2009-10-14
If Rhythmbox is shutting down, what is taking its place?

---

### Post by jackhynes on 2010-01-15
Can't believe there isn't an answer to this problem. My solution was to delete the offending file. I felt really bad.

---

### Post by sohlside on 2010-01-18
I may have stumbled onto the fix.  Posted it [here]("http://ubuntuforums.org/showthread.php?t=1142209&page=2") ([http://ubuntuforums.org/showthread.php?t=1142209&page=2](http://ubuntuforums.org/showthread.php?t=1142209&page=2)).  If that doesn't fix it I'd like to know what situation(s) it doesn't resolve because it seemed to do the trick on two unrelated issues I was having and I'd love to keep Rhythmbox useful.

---

### Post by jmjohn on 2010-01-24
Ever since Amarok 2 replaced Amarok 1, I haven't been able to find a stable music player in Ubuntu.  

Banshee crashes and moves slowly.

Songbird is ghastly in Linux.

Amarok 2 can't recognize my media collection on a fat32 partition.

Rythymbox runs great.  But now it's not being developed?  

When will we solve this problem?  

Limbo periods for music players are not ok.

PS  The linked solution above doesn't work for me.  I already have those packages installed.

---

### Post by vinutux on 2010-01-26
try Exaile or listen...................:D

---

### Post by jmjohn on 2010-02-01
To who?

You or the guy who suggested Banshee?  

I want a kickin' music player to be included in the default Ubuntu distro and supported.

Let's get this done.

---

### Post by itlarson on 2010-02-19
Exaile has totally broken ipod support. Banshee ipod support, on the other hand, is only mostly broken.  When will we be back to where we were with amarok 1.4?

---

### Post by DudeAlfred on 2010-04-23
hey!
a year -  and a LTS!! -  after it was last said that Rhythmbox would be abandoned, I still have the same problem, I was willing to wait for 6 month, but this really sucks! Why is the only thing that never works the Wicked media player! I can setup a SSH server and login from work ok, but god forbid I could play my songs in peace! :)

---

### Post by galdren on 2010-05-02
Listen isn't that stable..crashes on me all the time (for example: opening wikipedia tab crashes down my compiz). amarok is probably the best media player in existance but it still has some compatibility problems with gnome and a lot of gnome stuff (docky, gnome do) don't have any plugins for it..

quite upsetting...I love gnome but I love my music collection even more :(

---

### Post by 9a3eedi on 2010-05-06
It's a shame that there arent any decent music players on Ubuntu. I've gotten sick of Amarok 2's wierdness (and I really really miss the old one's visualization), so now I switched to rhythmbox. It's nice and fast, but it's just not as good as the old Amarok :(

Is Rhythmbox really dying out? Because it seems to be alive and kicking from the [gnome project page]("http://projects.gnome.org/rhythmbox/"). No mention of it being unmaintaned or anything

What's the cause of Rhythmbox's ID3 bug? Perhaps I can somehow find a fix for it, I've got a bit of C/C++ experience.

---

### Post by dirkoid on 2010-05-12
I've been having much the same problem with mostly the same result. I can't stand Amarok 2 and I don't really like Rythmbox that much either. What really bothered me was losing ipod support.

But ... I used the guide here:

[http://ubuntuforums.org/showthread.php?t=1473566&highlight=amarok](http://ubuntuforums.org/showthread.php?t=1473566&highlight=amarok)

and got Amarok 1.4 installed without a hitch. I can't say whether this will help or not but it worked great for me.

And installing v1.4 on Lucid got me back support for my ipod Nano 5g. Supposedly the new libgpod4 libraries will support the ipod touch now too.

I hope this helps someone else.

---

### Post by HC48 on 2010-05-19
hello,
I also had problems with mp3 files in Lucid which didn't occur in karmic. I checked the gstreamer packages as advised here:
[http://ubuntuforums.org/showthread.php?p=9324532#post9324532](http://ubuntuforums.org/showthread.php?p=9324532#post9324532)
but it didn't work. Then found that soundconverter needed **gstreamer0.10-plugins-ugly-multiverse**,
I installed the packages and mp3 is working in rythmbox,VLC and audacity.
H :)

---

### Post by Subito Piano on 2010-06-08
Found [here]("http://ubuntuforums.org/showthread.php?t=1142209"):

> **Re: ID3 Tag Demuxer**             
                                                                I had this  problem each time I opened Rhythmbox. As it turns out there were some  MP3's, possibly corrupted, causing the problem. Rhythmbox lists* the  files that it's struggling with, so I was able to identify those files  and move/delete them from Rhythmbox's source folders and this solved my  problem.

Even if you don't use Rhythmbox, I suggest setting it up and pointing it  at your MP3's. This way you'll at least be able to identify those MP3's  that are causing the "ID3 tag demuxer" issues.

* See Side Pane >> Library >> Import Errors


This worked for me, i hope it helps....

---

### Post by tnt533 on 2010-06-11
> **Subito Piano said:**
> Found [here]("http://ubuntuforums.org/showthread.php?t=1142209"):



This worked for me, i hope it helps....

Wow. I've been reading this thread top to bottom and all I saw was an individual asking a valid question about a standard package on the release version of Ubuntu and no one had anything for him but "Use a different player" or you're out of luck, fix it yourself.

OWCH. That's not proper support. That is what this forum is about right? Support?

I have the same issue with the ID3 tag demuxer not being found.

Thank you for your APPLICABLE reply to this individual's question.

---

### Post by oxf on 2010-06-11
> **tnt533 said:**
> Wow. I've been reading this thread top to bottom and all I saw was an individual asking a valid question about a standard package on the release version of Ubuntu and no one had anything for him but "Use a different player" or you're out of luck, fix it yourself.

OWCH. That's not proper support. That is what this forum is about right? Support?

I have the same issue with the ID3 tag demuxer not being found.

Thank you for your APPLICABLE reply to this individual's question.

It's rather bizare isn't it! There seems to be some sort of conspiracy of silence about Rhythmbox/Gstreamer and associated problems. Over time I've asked a number of questions on these topics and mostly I get silence (or try something else) Either that or people know very little about the subject. Even the Ubuntu Community Documentation states that "Gstreamer is broken"

---

### Post by duncanmahogany on 2010-06-23
> **HC48 said:**
> Then found that soundconverter needed **gstreamer0.10-plugins-ugly-multiverse**, :)

Thanks for the tip on this. I had thought that .mp3 support was already in place since I was able to play .mp3's already with Rhythmbox; but when using Streamripper with it I was running into the "Missing ID3 tag demuxer plugin probllem".  Installing the package you specified fixed the problem for me.

Cheers!

---

### Post by HC48 on 2010-06-25
Glad I could help!
HC :)

---

### Post by riesengreen on 2011-02-14
> **jmjohn said:**
> Ever since Amarok 2 replaced Amarok 1, I haven't been able to find a stable music player in Ubuntu.  

Banshee crashes and moves slowly.

Songbird is ghastly in Linux.

Amarok 2 can't recognize my media collection on a fat32 partition.

Rythymbox runs great.  But now it's not being developed?  

When will we solve this problem?  

Limbo periods for music players are not ok.

PS  The linked solution above doesn't work for me.  I already have those packages installed.

--

I agree with the dismay, unfortunately. I think that Rhythmbox is great and was surprised to hear that development had stopped!

---

### Post by jjjB on 2011-09-15
I'm still a linux/ubuntu newb. So, apologies if this doesn't work for anyone else. I had the same problem as the OP on my laptop, but had never had it on my desktop (both are LTS 10.04). I tried installing VLC on my laptop and restarted Rhythmbox and I no longer have this problem.

If you don't know of it, VLC is an EXCELLENT video player in that it can play just about anything. So, it's not like you're throwing junk on your system just to fix this.

Hope this helps!

---

