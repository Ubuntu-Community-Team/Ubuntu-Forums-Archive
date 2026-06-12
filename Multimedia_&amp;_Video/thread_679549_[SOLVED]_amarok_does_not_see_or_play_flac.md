---
title: "[SOLVED] amarok does not see or play flac"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by mandrill on 2008-01-27
All earlier posts looked like they were from the Feisty era. How do I get Amarok (running on Ubuntu Gutsy) to play nice with flac? They don't even show up in the playlist, which sucks because a little "I Robot" would be cool right now.

I know there HAS to be a fix! Can someone help?

---

### Post by whazooo on 2008-01-27
What engine are you using for amaroK?

---

### Post by dreadlord_chris on 2008-01-27
> **whazooo said:**
> What engine are you using for amaroK?
What other engine besides xine is available for Amarok?

---

### Post by dreadlord_chris on 2008-01-27
> **mandrill said:**
> All earlier posts looked like they were from the Feisty era. How do I get Amarok (running on Ubuntu Gutsy) to play nice with flac? They don't even show up in the playlist, which sucks because a little "I Robot" would be cool right now.

I know there HAS to be a fix! Can someone help?
Sounds like you are missing one (or more) of the GStreamer packages
fire up your package manager and search for **gstreamer0.10-plugins-**
You should see _base_,_good_,_bad_, and _ugly_.
I'd recommend installing them all - which should take care of *most* of your codec needs.

---

### Post by mandrill on 2008-01-27
Am using xine engine - not aware of another that will work, and as far as gstreamers, I tried the one suggested from from several posts that said no such package, has been discontinued and replaced by "X", tried to install *that*, says already installed at most recent release.

Found one post says try using xmms-flac, but a lot of these posts look a little too old to be  applicable.....

More ideas?

---

### Post by dreadlord_chris on 2008-01-27
sounds like you don't have all you Repositories enabled - you should turn on (at least) Universe, & Multiverse. Then reload the package list. Now all the gstreamer packages should show up.

Actually, I just dug a little deeper - flac's are handled by gstreamer0.10-plugins-good, which is available in the _Main_ Repo...

so, (from a konsole)
```

sudo apt-get install gstreamer0.10-plugins-good

```

will install the proper codec...

---

### Post by mandrill on 2008-01-28
> **dreadlord_chris said:**
> sounds like you don't have all you Repositories enabled - you should turn on (at least) Universe, & Multiverse. Then reload the package list. Now all the gstreamer packages should show up.

Actually, I just dug a little deeper - flac's are handled by gstreamer0.10-plugins-good, which is available in the _Main_ Repo...

so, (from a konsole)
```

sudo apt-get install gstreamer0.10-plugins-good

```

will install the proper codec...

Thanks for the feedback and help. However, this is a known bug with Amarok, and I run it on Ubuntu, not Kubuntu. I have tried every backdoor trick in the book that I can think of - activated non-supported repos, etc....newest version of Amarok, (got 19 upgrades, by the way)....I mean, Amarok not only won't play flac, it doesn't even see it!

[edit] May have something to do with xine reading mp3 tags on .flac file extension. Now what?

---

### Post by dreadlord_chris on 2008-01-28
I never said you were running Kubuntu - the instructions I gave have been fairly *buntu agnostic. Except for, maybe, my mention of konsole. I guess I assumed you'd know you could use **any** terminal app the same way...

Anyway... Ubuntu, Kubuntu, heck - you could be using Fluxbuntu, wouldn't matter...
These steps have worked for **every** *buntu box I have set up - the underlying codecs are the same...

You say this is a _known_ bug in Amarok?
3/4 of my library are flac's - I use Amarok every day to listen to them - I have **never** had a problem with them. Feisty, Gutsy, & Hardy; my Amarok has used the same codec sets.
Would you mind providing a reference to this bug - I've never heard of it....

Now, on to the matter at hand - these are **not** *backdoor tricks*, there is nothing hidden. As I posted, you don't even have to enable the extra repos - since the one you need (for flacs) is in the main repo.

Try playing flacs on a Windows machine - you'll go through, pretty much, the same process:

1) shut down Amarok
2) Install the codec(s):
```

sudo apt-get install gstreamer0.10-plugins-good

```
3) start Amarok back up
4) load flacs
5) groove to tunes

uhmmm and xine trying to read mp3 tags on flacs - that makes no sense. Flacs don't use mp3 (uh, actually id3...) tags, they use vorbis comments - a **very** different critter...
Also, if it _were_ actually trying to read id3 tags on your flacs - that would imply that it does, actually, see them (the flacs). This would have **nothing** to do with lack of playback though - the two functions (tag reading & audio playback) are completely seperate.

---

### Post by mandrill on 2008-01-28
> **dreadlord_chris said:**
> I never said you were running Kubuntu - the instructions I gave have been fairly *buntu agnostic. Except for, maybe, my mention of konsole. I guess I assumed you'd know you could use **any** terminal app the same way...

Anyway... Ubuntu, Kubuntu, heck - you could be using Fluxbuntu, wouldn't matter...
These steps have worked for **every** *buntu box I have set up - the underlying codecs are the same...

You say this is a _known_ bug in Amarok?
3/4 of my library are flac's - I use Amarok every day to listen to them - I have **never** had a problem with them. Feisty, Gutsy, & Hardy; my Amarok has used the same codec sets.
Would you mind providing a reference to this bug - I've never heard of it....

Now, on to the matter at hand - these are **not** *backdoor tricks*, there is nothing hidden. As I posted, you don't even have to enable the extra repos - since the one you need (for flacs) is in the main repo.

Try playing flacs on a Windows machine - you'll go through, pretty much, the same process:

1) shut down Amarok
2) Install the codec(s):
```

sudo apt-get install gstreamer0.10-plugins-good

```
3) start Amarok back up
4) load flacs
5) groove to tunes

uhmmm and xine trying to read mp3 tags on flacs - that makes no sense. Flacs don't use mp3 (uh, actually id3...) tags, they use vorbis comments - a **very** different critter...
Also, if it _were_ actually trying to read id3 tags on your flacs - that would imply that it does, actually, see them (the flacs). This would have **nothing** to do with lack of playback though - the two functions (tag reading & audio playback) are completely seperate.

Alright. Here's what I've been saying: 

jim@monkey:~$ sudo apt-get install gstreamer0.10-plugins-good
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-plugins-good is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

The bug report was from a launchpad in 2005 or 2006 - unable to re-locate now.

As far as tags, truthfully grasping at straws....but Amarok does not even see the folder the files are in. Open the folder, ask to play with Amarok, zip, dead air.

---

### Post by archivator on 2008-01-28
Have you tried opening up the files from a terminal? That might yield some feedback on the matter.

cd to the folder in question and try **amarok file.flac**. Make sure Amarok is closed before doing this, though.

---

### Post by mandrill on 2008-01-28
> **archivator said:**
> Have you tried opening up the files from a terminal? That might yield some feedback on the matter.

cd to the folder in question and try **amarok file.flac**. Make sure Amarok is closed before doing this, though.

I think we have might the culprit.....dunno why permission denied, though....how to fix?

jim@monkey:~$ cd
jim@monkey:~$ '/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla' amarok file.flac
bash: /media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla: Permission denied

[edit] strangely, I have one other folder with flac, totally forgot about it, and it plays. Also have lost substantial volume since installing the newer version of Amarok...

---

### Post by dreadlord_chris on 2008-01-29
> **mandrill said:**
> I think we have might the culprit.....dunno why permission denied, though....how to fix?

jim@monkey:~$ cd
jim@monkey:~$ '/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla' amarok file.flac
bash: /media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla: Permission denied

[edit] strangely, I have one other folder with flac, totally forgot about it, and it plays. Also have lost substantial volume since installing the newer version of Amarok...
umm, ok - this may be a silly question, but here goes...
is there actually a file in that folder named _file.flac_
or were you just using that as an example?

Anyway - sounds like the permissions might be out of wack:
from the folder with the offending flacs:
```

ls -la

```
do you have permission to _read_ - is there an **r** in the 2nd column?
how about the user & group owner - is it your user  & group name?
if you don't have read permission:
```

chmod +r *.flac

```
if you're not the owner of the files:
```

sudo chown NAME *.flac

```
of course, substituting your user name for NAME

HTH

---

### Post by mandrill on 2008-01-29
Per archivator's suggestion, I did this:

[I]Have you tried opening up the files from a terminal. That might yield some feedback on the matter.

cd to the folder in question and try *amarok file.flac*. Make sure Amarok is closed before doing this, though.[/I]

However, I believe I did it incorrectly. It was very late when I tried it And no, there is no file called -file.flac.

Afraid you lost me right here: "- from the folder with the offending flacs:

Code:
---------
ls -la
--------- 



When I check permissions, I have read & write, but I'm obviously not doing this the way you are trying to explain it. I can play these files with vlc and rhythmbox, but amarok doesn't even see the folder (its not in amarok's collection)

---

### Post by dreadlord_chris on 2008-01-30
> **mandrill said:**
> 
jim@monkey:~$ cd
jim@monkey:~$ '/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla' amarok file.flac
bash: /media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]/01. I Robot.fla: Permission denied

[edit] strangely, I have one other folder with flac, totally forgot about it, and it plays. Also have lost substantial volume since installing the newer version of Amarok...

from that post it *looks* like you opened a terminal and typed in: **amarok file.flac**

> **mandrill said:**
> Per archivator's suggestion, I did this:

[I]Have you tried opening up the files from a terminal. That might yield some feedback on the matter.

cd to the folder in question and try *amarok file.flac*. Make sure Amarok is closed before doing this, though.[/I]

However, I believe I did it incorrectly. It was very late when I tried it And no, there is no file called -file.flac.

right - **file.flac** should be replaced with the file name of one of the flacs that Amarok _won't_ play for you.

> **mandrill said:**
> 
Afraid you lost me right here: "- from the folder with the offending flacs:

Code:
---------
ls -la
--------- 



When I check permissions, I have read & write, but I'm obviously not doing this the way you are trying to explain it. I can play these files with vlc and rhythmbox, but amarok doesn't even see the folder (its not in amarok's collection)

I meant open a terminal, go to the folder with the flacs that won't play (in Amarok), and type in (the terminal): **ls -la**
This is the command line that gives a detailed directory listing - showing such information as; permissions, ownership, size, etc.

You say the folder doesn't show up in Amaroks Collection - silly question, but: have you actually added the folder in Settings > Configure Amarok > Collection?

---

### Post by mandrill on 2008-01-30
dreadlord - I would say this tells the whole story:

jim@monkey:/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]$ ls -la
total 388880
drwx------ 2 jim root    16384 2008-01-29 00:24 .
drwx------ 5 jim root    16384 2008-01-28 23:59 ..
-rw------- 1 jim root 37396020 2008-01-29 00:24 01. I Robot.fla
-rw------- 1 jim root 23448445 2008-01-29 00:24 02. I Wouldn't Want To Be Like You.fla
-rw------- 1 jim root 27583463 2008-01-28 23:58 03. Some Other Time.fla
-rw------- 1 jim root 27702044 2008-01-28 23:58 04. Breakdown.fla
-rw------- 1 jim root 29385463 2008-01-28 23:58 05. Don't Let It Show.fla
-rw------- 1 jim root 35833712 2008-01-28 23:58 06. The Voice.fla
-rw------- 1 jim root 21968268 2008-01-28 23:58 07. Nucleus.fla
-rw------- 1 jim root 27437098 2008-01-28 23:58 08. Day After Day (The Show Must Go On).fla
-rw------- 1 jim root 18233904 2008-01-28 23:58 09. Total Eclipse.fla
-rw------- 1 jim root 21781285 2008-01-28 23:58 10. Genesis Ch.1 V.32.fla
-rw------- 1 jim root 10304927 2008-01-28 23:58 11. Boules (I Robot Experiment).fla
-rw------- 1 jim root 13254010 2008-01-28 23:58 12. Breakdown (Demo).fla
-rw------- 1 jim root 21749623 2008-01-28 23:58 13. I Wouldn't Want To Be Like You (Rough Mix).fla
-rw------- 1 jim root 21829081 2008-01-28 23:58 14. Day After Day (Rough Mix).fla
-rw------- 1 jim root 60137726 2008-01-28 23:58 15. The Naked Robot.fla
-rw------- 1 jim root    31590 2008-01-28 22:51 cover.jpg
jim@monkey:/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]$ amarok I Robot.flac
jim@monkey:/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]$


and this is *amarok flac.file* result:

jim@monkey:/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]$  amarok I Robot.flac
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8239d40 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8239d40 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QPainter::begin: Cannot paint null pixmap
jim@monkey:/media/Disk/Music/ Alan Parsons Project/I Robot  [2007 Remaster]$

---

### Post by mandrill on 2008-01-30
dreadlord:



"Anyway - sounds like the permissions might be out of wack:
from the folder with the offending flacs:
 
Code:

ls -la

do you have permission to read - is there an r in the 2nd column?
how about the user & group owner - is it your user & group name?
if you don't have read permission:

Code:

chmod +r *.flac

if you're not the owner of the files:

Code:

sudo chown NAME *.flac

of course, substituting your user name for NAME"

tried to follow these instructions about a dozen times. could you possibly put the mortar between the bricks for me? I really need precision on the instructions - never done it before - don't want to bork the OS because of 1 file. and why would only 1 file come out as owned by root? and why can I play it on other apps? (and yes, it is listed in amarok's collection)

much appreciation for your help, and your patience - thanks

---

### Post by mandrill on 2008-01-30
Many thanks to dreadlord_cris & archivator. Turns out the file(s) in question were actually mp3 labeled as flac, which strangely did not bother either vlc or rhythmbox. So, I changed the flac to mp3 on the files, re-tagged them, and, problem solved

I forget how I did it, but it was actually Amarok that discovered the discrepancy. So, lots of time spent on something pretty dumb, but I learned a hell of a lot in the process.

So, gentlemen, thanks again for your perseverance.

---

### Post by dreadlord_chris on 2008-02-01
I'm glad you got it worked out - it was **really** starting to puzzle the piss out of me...

---

