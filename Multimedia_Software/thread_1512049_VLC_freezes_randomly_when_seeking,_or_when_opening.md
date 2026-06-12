---
title: "VLC freezes randomly when seeking, or when opening a subsequent media file"
date: 2010-06-17
forum: Multimedia Software
---

### Post by ThinkEntropy on 2010-06-17
I did a search first but didn't find anyone with the same symptoms that I have.  For whatever it's worth, VLC worked flawlessly before I upgraded to 10.04, which I am now running...

The title describes the problem, but more specifically if I start skipping through a movie or song that's playing, sometimes the program will totally freeze.  It stops playing audio and video altogether.  Similarly, if for instance I'm listening to a music playlist, often times when VLC skips to the next track it stops playing audio, but continues through the track like it's still playing.  Once it reaches the end of the first track it had a problem with, it freezes altogether and I have to close the program.  In fact, the program stays running even after I "x" out of it, and I have to kill the process in system monitor and restart VLC in order to restore functionality.  This happens quite often (as in, a few times a day), and as I'm sure you can imagine, this gets quite annoying, lol.

I've looked in the various logs in Log Viewer, but I don't see any obvious problems.  There are no error messages pertaining to VLC, or audio or video output so far as I can tell.  I've also tried reinstalling VLC to no avail.  I think the next thing I'll try is to remove it completely first, and then reinstall it.

...but if that doesn't work, is there anything else you guys think I should be looking at?  Lucid is the first Ubuntu release that's worked well for me (9.04 and 9.10 had serious issues on my machine) so I'd like not to revert back to an older release just for VLC if at all possible.  Thanks for any suggestions you guys post up!!

---

### Post by ThinkEntropy on 2010-06-18
Bump...

Last night I completely removed VLC and then re-installed it, and it just now froze again when it went to the next track in my playlist.

---

### Post by ThinkEntropy on 2010-06-19
bump...

---

### Post by yoshimitsuspeed on 2010-06-23
Same problem and a pile of others. 

Unfortunately this is the worst buggiest version I have ever run and haven't gotten jack for help on any of it.

[http://ubuntuforums.org/showthread.php?t=1514390](http://ubuntuforums.org/showthread.php?t=1514390)

---

### Post by ThinkEntropy on 2010-06-23
> **yoshimitsuspeed said:**
> Same problem and a pile of others. 

Unfortunately this is the worst buggiest version I have ever run and haven't gotten jack for help on any of it.

[http://ubuntuforums.org/showthread.php?t=1514390](http://ubuntuforums.org/showthread.php?t=1514390)

That is so frustrating!!  I can definitely empathize with you yoshi...

Even just a nudge in the right direction would be nice.  I'm new to Linux/Ubuntu so I'm not entirely familiar with the process in diagnosing/correcting these sorts of problems.   I'm genuinely surprised by the lack of input here.

I'll keep playing and poking at my setup, and if I find anything useful I'll post it up...

---

### Post by yoshimitsuspeed on 2010-06-23
Thanks I will too.

I tried to install google earth and it freezes up almost identical to VLC. 

I am thinking this might be a bigger issue. 
You should try installing google earth just to see if you got the same results. If so it might help track it to a common program/driver/app whatever might be causing the issue.

---

### Post by ThinkEntropy on 2010-07-02
Well, no one else that posted in this thread seemed to encounter the same problem as I did, but just in case someone has this same issue in the future...I found out what was causing the random freezes and I'm sure many will be surprised, lol:

PulseAudio.

Back when I was running Jaunty my audio quality was awful, and saltmore recommended uninstalling PulseAudio.  I tried it, and amazingly that fixed the issue.  So PulseAudio was doing something funny to the sound.

Fast forward...

I noticed when I installed Lucid the crappy audio quality returned, and I was also blessed with that VLC freezing issue.  I TOTALLY forgot that PulseAudio was doing funny things on my rig until I dug up one of my old posts, and saw my previous fix:

[http://ubuntuforums.org/showthread.php?t=1355950](http://ubuntuforums.org/showthread.php?t=1355950)

So on a whim, I tried uninstalling PulseAudio again (I followed the same procedure as indicated in the above link) and not only is the audio crisp and clear again...BUT VLC STOPPED RANDOMLY FREEZING!!  I'm so happy :D

So, if you found this thread while searching and are having random freezing issues with VLC...try removing PulseAudio.

---

### Post by yoshimitsuspeed on 2010-07-03
Lol this is interesting because I installed Pulse Audio in Kubuntu in an effort to get a global equalizer. I removed it a while ago when I was having these problems but didn't do a complete removal as in those instructions. 
I just did and removed several pulse related files. 
I think my troubles go much deeper than that but we will see if it has any effect. 
 Thanks for the update.

---

### Post by ThinkEntropy on 2010-07-03
> **yoshimitsuspeed said:**
> Lol this is interesting because I installed Pulse Audio in Kubuntu in an effort to get a global equalizer. I removed it a while ago when I was having these problems but didn't do a complete removal as in those instructions. 
I just did and removed several pulse related files. 
I think my troubles go much deeper than that but we will see if it has any effect. 
 Thanks for the update.


I wish you the best of luck.  I'll keep my fingers crossed for you that removing pulse helps!

---

### Post by yoshimitsuspeed on 2010-07-03
I think I found my problem too. 
Posted it in my thread. 
[http://ubuntuforums.org/showthread.php?t=1514390](http://ubuntuforums.org/showthread.php?t=1514390)

Interesting I had pulse installed too but it also could have been a combination of problems. 
I'm just gonna keep my fingers crossed for now.

---

