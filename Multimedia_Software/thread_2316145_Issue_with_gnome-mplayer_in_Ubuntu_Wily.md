---
title: "Issue with gnome-mplayer in Ubuntu Wily"
date: 2016-03-05
forum: Multimedia Software
---

### Post by cogset on 2016-03-05
I've tried to see some mp4 videos using gnome-player in Wily, to my surprise I've discovered that it doesn't work at all: in fact, it can't display anything, only the audio is reproduced.

The same videos can be played with zero isssues in VLC and mplayer as well, which is IMHO surprising as gnome-mplayer should be -as I understand- just a GUI frontend for mplayer.

I've tried already to set different video output modules and also specified the actual path to the mplayer executable, which has made no difference at all.

I have mplayer2      2.0-728-g2c378c7-4build1  and  gnome-mplayer     1.0.9-3build1 installed.

Is gnome-mplayer broken or am I missing something to make it actually work?

---

### Post by QDR06VV9 on 2016-03-05
Hey cogset..Well this has been a long time bug..
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014)
They had kind of a dirty fix then,.. don't know if it still works or not but it should.
> Those would be the most likely to fail to be decoded but certainly  not limited to kust them.
These files are commonly found online though many users will have locally.
Also affected  other than totem, totem youtube plugin, &  banshee would be the mozilla-plugin & minitube.
Typically the audio will play with no video though sometimes neither
 *Moving libgstvideoparsersbad.so to a .bak allows decoding to take place on the previously affected files, **but *is not the recommended fix***


But most of the Video files i play are with Smplayer, VLC, and Kodi MC and all the mp4 video I throw at them they all work at least here.
Regards

---

### Post by cogset on 2016-03-07
Thanks, but  that bug dates back to 2012, and the last comment is from 2013 referring to Ubuntu 13.04 ... it's 2016 now and we're talking about Ubuntu 15.10, is that particular bug still not fixed?  

Apart from the last comment, it seems to have been fixed in [comment88]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/973014/comments/88") : maybe there has been some regression?

Besides, I've also tried a live CD of Lubuntu 15.10 which comes with gnome-mplayer as the default video player, and I believe should have the same exact packages gnome-mplayer (1.0.9-3build1) and mplayer2 (2.0-728-g2c378c7-4build1) as Ubuntu-MATE 15.10 : and _it works _there, which is really confusing.  

Thinking of it, if gnome-mplayer is actually just a GTK frontend for mplayer2, and the latter definitely works in Wily, it should be actually possible to launch gnome-mplayer from a terminal with the correct arguments and it should work, without having to manually rename some files, which seems kind of dirty way of "fixing" things.

As for other options, well VLC is still my media player of choice, but I'd like to have an alternative too - also it looks like mplayer is rendering some videos a tiny bit better than VLC, although it may be a matter of advanced settings and/or default video output.

As for Smplayer, I've tried it briefly and it works, but after installation it has tried twice to launch Firefox opening the project webpage on sourceforge.net : that's just a no go in my book, so how don't care how good it is, it's gone.

---

### Post by QDR06VV9 on 2016-03-07
> **cogset said:**
> 
As for Smplayer, I've tried it briefly and it works, but after installation _**it has tried twice to launch Firefox opening the project webpage on sourceforge.net : that's just a no go in my book**_, so how don't care how good it is, it's gone.
I also agree with that sort of behaviour but it stops doing that.
You can use what ever works for you..but I myself not a big fan of mplayer due to it's lacking consistency.
Kind Regards
EDIT: I found the way to disable the browser open problem
Under Prefernces On the Left Tree <Updates> and disable 
Open an informative page after an upgrade.

---

### Post by mc4man on 2016-03-07
Don't know about 15.10, but in 16.04 gnome-mplayer works ok.
There are some packaging & config issues that should be fixed, addressed in this bug.
[https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/1554224](https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/1554224)

Otherwise if you get the proper vo should be ok. Here I have nvidia optimus so installed mplayer over mplayer2, enabled Video Hardware support, changed vo to vdpau (with libvdpau-va-gl1 installed) & the player is ok. Not what I use but should be usable for others if they so choose.

---

### Post by cogset on 2016-03-14
Thanks, but I'm not sure the above could work for me: I have (unfortunately, may I say) an ATI card instead of Nvidia, so I don't think that vdpau as output may solve this issue.

Truth to tell, I think by now I've tried any vo in gnome-mplayer in Wily, and enabled/disabled Video Hardware support as well, it just never works: I've never seen a single video.

Furthermore, this statement  > The control file should list mplayer before mplayer2, mplayer2 is long dead, should be removed from disk looks kinda confusing to me, I thought it was the other way around: in fact, in Wily I believe mplayer is a virtual package provided by mplayer2.

And I can confirm that mplayer2 works in Wily, whilst gnome-mplayer on the other hand is utterly useless.

---

### Post by mc4man on 2016-03-14
> **cogset said:**
> .

Furthermore, this statement   looks kinda confusing to me, I thought it was the other way around: in fact, in Wily I believe mplayer is a virtual package provided by mplayer2.

And I can confirm that mplayer2 works in Wily, whilst gnome-mplayer on the other hand is utterly useless.
development in mplayer2 stopped quite some time ago while mplayer is still going. For 16.04 mplayer2 has now been dropped & won't be available,ie.
[http://packages.ubuntu.com/xenial/mplayer2](http://packages.ubuntu.com/xenial/mplayer2)

Your best bet is to check out 16.04 come May, hopefully it will treat your hardware better.

---

