---
title: "Audacity/LAME problems in GUTSY (worked in FEISTY)"
date: 2007-10-20
forum: Multimedia Production
---

### Post by ticstah on 2007-10-20
Hey everyone. I installed Gutsy clean and fresh, downloaded Audacity and LAME through the repositories, and for some reason when I try to have Audacity select LAME in the preferences, it does nothing. I installed liblame-dev, nothing worked. I don't understand it, I'm CLICKING ON THE FILE THAT ITS ASKING FOR.. libmp3lame.so (as well as *.so.0 an *.so.0.0) is in /usr/local/.. its the file it needs, in the directory it wants it in.. and when I click on it.. nothing. It's not recognizing it.
is the version of LAME in the repositories not compatible with the version of audacity? am I doing something wrong on my end?

HELP! my podcast is in jeopardy if I don't get this working!

---

### Post by the_arm on 2007-10-22
Hey there; you're not alone, I'm experiencing the same problem.  Audacity, Soundconverter both broken after upgrading from Feisty to Gutsy.  complaining that they can't find the right library.

I tried reinstalling LAME and Soundconverter through the synaptic package manager.  that didn't work. I'm a total amateur, so not sure what else to do!

Let me know if you solve it, and I'll do the same!
-arm

---

### Post by ticstah on 2007-10-22
still no luck. re-installed feisty, set up audacity and lame (which worked fine), then upgraded feisty to gutsy using the upgrade manager... that didn't work either. audacity and lame were still there, with their updated versions... audacity is not seeing lame.

anyone? if I can't get this to work I'll have to downgrade to feisty.. which is fine I suppose.. its been rock solid.. I had hoped to be able to upgrade and be up to speed with everyone else.

as the lol-cats say.... HALP!:mad:

---

### Post by the_arm on 2007-10-22
This isn't the solution we're looking for...but in the mean time I'm using lame from the commandline as a work around.  The fact that lame from the commandline works is somewhat befuddling, but, at least it does.

What I've discovered so far: it's not a global audio conversion issue.  Soundconverter will convert wavs to flacs just fine.  It's just the mp3 conversion that seems to be screwed up.  Likewise in audacity: I can save as wav and then use lame to convert.  Furthermore, MP3 playback works great. 

I'll keep monkeying around and see what I find.
-arm

PS: Looks like this person is having the same issue, too:
[http://ubuntuforums.org/showthread.php?t=585641](http://ubuntuforums.org/showthread.php?t=585641)

---

### Post by ticstah on 2007-10-22
> **the_arm said:**
> This isn't the solution we're looking for...but in the mean time I'm using lame from the commandline as a work around.  The fact that lame from the commandline works is somewhat befuddling, but, at least it does.

What I've discovered so far: it's not a global audio conversion issue.  Soundconverter will convert wavs to flacs just fine.  It's just the mp3 conversion that seems to be screwed up.  Likewise in audacity: I can save as wav and then use lame to convert.  Furthermore, MP3 playback works great. 

I'll keep monkeying around and see what I find.
-arm

PS: Looks like this person is having the same issue, too:
[http://ubuntuforums.org/showthread.php?t=585641](http://ubuntuforums.org/showthread.php?t=585641)

would you be so kind as to an example of command line instructions for LAME? although, I suppose I can just RTFM for LAME :rolleyes:

I really hope a fix for this comes through the pipes soon. ever since feisty I've been an ubuntu junkie, tagging any story that comes into my reader. I keep seeing all of these stories about how gutsy is the next step, vista is faltering blahblah... yet I can't even convert an mp3. it's kind of lame (ha!).. but oh well. I'll stay with ubuntu.

---

### Post by peatrap on 2007-10-22
Add me to the group having problerms with lame. Worked fine for 7.04, ran into the wall in 7.10. Looking forward to a update.

---

### Post by ticstah on 2007-10-22
> **peatrap said:**
> Add me to the group having problerms with lame. Worked fine for 7.04, ran into the wall in 7.10. Looking forward to a update.

likewise. I did a quick search in launchpad, but didn't notice anything listed concerning this. maybe one of us should submit it as a bug? would it be an audacity bug or a LAME bug? it should definitely be addressed.

---

### Post by the_arm on 2007-10-22
Hi.  Regarding lame...I just did

lame <input filename> <output filename> and it made a 128kbps mp3.

this looks like it has more info:
[http://wiki.hydrogenaudio.org/index.php?title=LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME)

It's not just audacity, at least for me.  Can you guys use Soundconverter to convert wavs to MP3s?  I can't.  (But it will do WAVs to FLAC)

So, i'm thinking it's a problem with lame, or gstreamer (soundconverter uses gstreamer, but it looks like gstreamer uses lame.)

beats me...it "just worked" before!
-arm

---

### Post by the_arm on 2007-10-22
I don't want to be leading anyone down the wrong path if they are debugging this:

I was wrong: the soundconverter and audacity were separate issues.

If anyone had soundconverter broken with the upgrade I was able to fix it by doing a **complete removal** of gstreamer0.10-plugins-ugly-multiverse and then reinstalling it.

This didn't fix audacity, though.  It's still broken (unable to export mp3s).
-ARM

---

### Post by whiskyprajer on 2007-10-25
Re; Audacity, I had similar problems. This thread helped me solve that:

[http://ubuntuforums.org/showthread.php?t=589891&highlight=gutsy+audacity](http://ubuntuforums.org/showthread.php?t=589891&highlight=gutsy+audacity)

HOWEVER, re: SOUND CONVERTER, I'm having similar troubles ripping OGGs to MP3. Is there some setting I'm supposed to change?

---

### Post by whiskyprajer on 2007-10-25
I should add: I tried removing/reinstalling the gstreamer uglies, but that didn't work for me.

---

### Post by Dai777 on 2007-10-30
[http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html](http://dai-videotutes.blogspot.com/2007/10/audacity-ubuntu-710-exportmp3.html)
here is my video tute on exporting mp3's

---

### Post by schoeee on 2007-11-08
> **the_arm said:**
> I don't want to be leading anyone down the wrong path if they are debugging this:

I was wrong: the soundconverter and audacity were separate issues.

If anyone had soundconverter broken with the upgrade I was able to fix it by doing a **complete removal** of gstreamer0.10-plugins-ugly-multiverse and then reinstalling it.

This didn't fix audacity, though.  It's still broken (unable to export mp3s).
-ARM

This soundconverter part worked for me. Thanks. I use it a lot to convert mp3's to ogg vorbis.

---

