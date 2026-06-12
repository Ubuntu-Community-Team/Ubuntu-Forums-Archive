---
title: "Trying to convert a CD I bought to .Mp3 insted of .ogg"
date: 2009-01-12
forum: Multimedia Software
---

### Post by BrownDoggBrew on 2009-01-12
I got a few CDs that I put in to my cd drive. When I go to put them on my hard drive their saved as .OGG but I would like them saved as .mp3 files so that I can make one data CD with them and play them on my Mp3 disk player at work.

---

### Post by cozmicharlie on 2009-01-12
> **BrownDoggBrew said:**
> I got a few CDs that I put in to my cd drive. When I go to put them on my hard drive their saved as .OGG but I would like them saved as .mp3 files so that I can make one data CD with them and play them on my Mp3 disk player at work.

I assume you are ripping these from the cd?  You should be given an option to rip to mp3.  Have you installed the mp3 codecs?

---

### Post by BrownDoggBrew on 2009-01-12
Yes I have. I put the CD in to the drive and sound juicer pops up. I hit extract and it will automatic put it in .OGG but edit pref and output MP3 audio and theirs nothing I can hit like apply. May be I should just hit close. I'll try that.

---

### Post by cozmicharlie on 2009-01-12
> **BrownDoggBrew said:**
> Yes I have. I put the CD in to the drive and sound juicer pops up. I hit extract and it will automatic put it in .OGG but edit pref and output MP3 audio and theirs nothing I can hit like apply. May be I should just hit close. I'll try that.

Yes - all you do is set the preference and close.

---

### Post by BrownDoggBrew on 2009-01-12
No its acting funny. ok I got this CD I put it in to the CD Drive... Sound Juicer pops up. If I hit extract It will in .OGG so I hit edit pref. in the list of output formats their is no option for .MP3 but if I go to edit profiles their is a cd quality mp3. click it and close but that dosn't do any thing.

---

### Post by cozmicharlie on 2009-01-12
Open the preferences and go to "output format">edit>cd quality mp3>edit.  What does it show for gstreamer pipeline?

The other option is to try another program.  I really prefer K3b - it is a kde program but it works great in gnome and it offers a lot more options.  It can be installed from Synaptic.

---

### Post by BrownDoggBrew on 2009-01-12
Its says... audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux ... 
Im going to try kb3 now

---

### Post by cozmicharlie on 2009-01-12
You probably need to install the gstreamer codecs.  First install the medibuntu repository then install the gstreamer (good, bad ugly) codecs.  This tutorial shows you how.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by BrownDoggBrew on 2009-01-14
I went to [http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree) and did a bunch of stuff and it worked. how do I mark this as resolved?

---

### Post by cozmicharlie on 2009-01-14
> **BrownDoggBrew said:**
> I went to [http://www.psychocats.net/ubuntu/nonfree](http://www.psychocats.net/ubuntu/nonfree) and did a bunch of stuff and it worked. how do I mark this as resolved?

Excellent - psychocats has a lot of great info.  Do you remember what you did specifically?  If so, it would be helpful if you posted the solution.  I believe the solved is in thread tools.

---

