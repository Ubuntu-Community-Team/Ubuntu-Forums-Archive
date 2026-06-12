---
title: "dvd rip problem: &quot;no jobs and nothing else to do. you could rip a dvd&quot;"
date: 2008-12-07
forum: Mythbuntu
---

### Post by scottnj on 2008-12-07
i just installed mythbuntu for the first time.

when i try to rip a dvd it tries for a while, then i get "no jobs and nothing else to do. you could rip a dvd".

i tried playing dev/dvd in mplayer and it shows a scrambled image and stops. vlc media player plays it fine. what am i doing wrong?

---

### Post by scottnj on 2008-12-07
i forgot to mention, i do have libdvdcss2, w32codecs, and ffmpeg enabled in the control center. if they are installed properly and working, i don't know enough linux to know.

---

### Post by klc5555 on 2008-12-08
> **scottnj said:**
> i just installed mythbuntu for the first time.

when i try to rip a dvd it tries for a while, then i get "no jobs and nothing else to do. you could rip a dvd".

i tried playing dev/dvd in mplayer and it shows a scrambled image and stops. vlc media player plays it fine. what am i doing wrong?

This may or may not have a bearing on your problem, but I frequently use the app DeVeDe as a necessary supplement to Mytharchive for archiving recordings. DeVeDe uses mplayer and mencoder, and I've noticed that on my installation, mplayer and mencoder are very fussy, and produce nothing but scrambled green screen if I have watched liveTV or a recording since the last time X and the mythtv frontend were started. I've found that to successfully use DeVeDe, or any other app that relies on mplayer or mencoder, I have to restart the frontend (ctrl-alt-backspace) then go directly and use the app that requires mplayer or mencoder.

After using the mplayer- or mencoder-dependent app, liveTV will produce scambled green screen (or a lockup) unless I restart X+the frontend again. Then everything is OK again until the next time I need to run DeVeDe.

So, as an experiment, you might wish to try restarting X + the frontend just prior to playing your newly ripped DVD with mplayer. See if that coaxes the perpetually beta mplayer to function properly. VLC and Xine are good alternatives.

Cheers! :)

---

### Post by rhpot1991 on 2008-12-08
Odds are you are fighting with some DRM, if you want to rip as an ISO you can do the following:

sudo apt-get install gddrescue

then do: ddrescue -d /dev/dvd /wherever/you/want/the/iso.iso /same/path/as/before.log

If you specify the log you can ^C to kill it and resume at a later point with the same command.  This will run for a while and skip over the bad bits (normally the DRM, unless the disc is damaged) and then come back and choke on them some more later (you can normally kill it at this point).  Be aware that this is a slow process compared to ripping within myth itself.

---

### Post by scottnj on 2008-12-08
> **rhpot1991 said:**
> Odds are you are fighting with some DRM, if you want to rip as an ISO you can do the following:

sudo apt-get install gddrescue

then do: ddrescue -d /dev/dvd /wherever/you/want/the/iso.iso /same/path/as/before.log

i think you are right about drm. the dvd is "Chronicles of Narnia: Prince Caspian". when i put in a different dvd the rip seems to go fine.

why was vlc able to play it fine, but not mplayer and whatever program myth uses to rip a dvd to an iso?

i am only evaluating myth as an option for a htpc system. i want something that is easy and reliable. if i was going to be the only one using it, switching to a different program for a rip would be fine. but don't want to be doing constant tech support for family/friends.

i was hoping myth would be mature enough by now, but i don't think it is there yet. i also looked at some of the other oss solutions, but they don't have the needed backend features needed yet. i haven't actually tried any of the commercial offerings, but from reading what they offer, they don't have the features and flexibility i would like. it looks like i will probably not be building my htpc anytime soon. oh well, maybe next year.

---

### Post by rhpot1991 on 2008-12-08
> **scottnj said:**
> i think you are right about drm. the dvd is "Chronicles of Narnia: Prince Caspian". when i put in a different dvd the rip seems to go fine.

why was vlc able to play it fine, but not mplayer and whatever program myth uses to rip a dvd to an iso?

i am only evaluating myth as an option for a htpc system. i want something that is easy and reliable. if i was going to be the only one using it, switching to a different program for a rip would be fine. but don't want to be doing constant tech support for family/friends.

i was hoping myth would be mature enough by now, but i don't think it is there yet. i also looked at some of the other oss solutions, but they don't have the needed backend features needed yet. i haven't actually tried any of the commercial offerings, but from reading what they offer, they don't have the features and flexibility i would like. it looks like i will probably not be building my htpc anytime soon. oh well, maybe next year.

Unfortunately as long as mega corporations are employing DRM you will have this problem.  In most instances it only hurts the end user and not those who it is meant to deter.  The latest tactic is to inject bad sectors into the disc in an area that the player will never see during playback, but when you are making a copy you see these bad sectors.  Your computer will then either have a read failure or choke on these bad sectors causing a corrupt copy/rip.  Some recent Sony discs employ this technique and cannot even be played on some newer players or computers because of this.

I see a few options for you:
1. You could try setting up some sort of system to allow them to easily run ddrescue
2. Research some programs to rip dvds that have a nice GUI that you can let them use.  Worst case if this has to be on windows you could give them a samba share and let drop the files over when they are done.

There are a lot of solutions out there, but when you get into the constant changing world of DRM protection there generally is no ring to rule them all.

---

### Post by scottnj on 2008-12-09
> **rhpot1991 said:**
> Worst case if this has to be on windows you could give them a samba share and let drop the files over when they are done.

i am a quadriplegic so handling physical disks just is not an option for me, but i can control a computer. i already rip my dvds using dvdfab on windows and copy them to my server. i was hoping to set something up that my parents and brothers houses, but everything i checked out so far is still too temperamental.

because of drm i refuse to buy blu-ray disks because they are so difficult to back up to my computer. well, that and the fact the media companies treat us consumers as criminals and are preventing us from doing what we are legally allowed under copyright law.

---

### Post by tehbeermang on 2009-01-26
> **rhpot1991 said:**
> Odds are you are fighting with some DRM, if you want to rip as an ISO you can do the following:

sudo apt-get install gddrescue

then do: ddrescue -d /dev/dvd /wherever/you/want/the/iso.iso /same/path/as/before.log 

They're on to that trick. I just tried that with my legally purchased copy of WALL E. 

"Play movie" from the menu flips between "comments are not rated" and the FBI anti-piracy warning.

Not trying to be a pirate. I want an uncluttered and convenient home theater experience.

What are some other methods I could use?

---

### Post by rhpot1991 on 2009-01-26
> **tehbeermang said:**
> They're on to that trick. I just tried that with my legally purchased copy of WALL E. 

"Play movie" from the menu flips between "comments are not rated" and the FBI anti-piracy warning.

Not trying to be a pirate. I want an uncluttered and convenient home theater experience.

What are some other methods I could use?

Google may be your best friend here.

---

### Post by tehbeermang on 2009-01-26
How well does handbrake work?

---

### Post by rhpot1991 on 2009-01-26
> **tehbeermang said:**
> How well does handbrake work?

I've used it for dvds on my iPod, but at the time it had a hard time dealing with copy protection.  This was quite some time ago, so things may be different now.  Give it a try?

---

