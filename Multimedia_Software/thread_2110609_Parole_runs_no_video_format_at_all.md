---
title: "Parole runs no video format at all"
date: 2013-01-30
forum: Multimedia Software
---

### Post by puzzledinportorchard on 2013-01-30
First: I do hope I'm not being rude by asking here a question I should ask in a Parole-specific forum.  I haven't found such.

I'm running 12.04.1 LTS on a Pentium 4 which - the root of most of my probs - is offline.  Online (right now, obviously) I am in a LiveCD of 10.04 on a computer that I can't permanently put Linux on.  I've spent the last month since I got my offline computer(yay freegeek!) figuring out how to install programs by using Synaptic and trotting things back and forth on a USB drive, and only today have I managed to put Inkscape and some games on my offline computer.  When I tried the same process with VLC -generating a script on the offline, one-month-old version of Synaptic Program Manager and carrying it to the online - I get a lot of '404' error messages when I run the script online and Synaptic can't finish the process on the offline.  I suspect it's due to repositories having changed in that time.  I have followed the process described in this forum for offline repository updating and have saved to the USB drives the four packages.gz files but haven't completed it on the offline because, frankly, I'm afraid of screwing the package manager up; and the command line terrifies me.

Sorry if this is more explanation than is needed, but when one doesn't know, one also doesn't know what people who do know need to know to help one know.

So my problem is this: Parole, the only media player I have currently, will play nothing.  With mpegs of any variety I get no image; with AVIs and other formats I get messages about needing plugins and 'demuxers' (which can't be a real word!)  When I do a search online for Parole plugins or the specific plugins mention in the Parole error messages, I find only web pages that say how nice it is that Parole works on everything without needing plugins.  Which is not helpful to the easily bewildered.  I have found a reference in this forum to the same problem, but I didn't understand the answers, and also it was on Ubuntu 11.04, and stuff changes.

Again, possibly I should be searching some Parole-specific forum.  This is undoubtedly something simple but obscure to the uninformed like me.  Any pointers or hints - somebody somewhere must have answered this like a bazillion times and I'm too dumb to find it - would be appreciated.

---

### Post by evilsoup on 2013-01-30
Please put blank lines between your paragraphs, as it stands your post is borderline-unreadable.

EDIT: I suspect you need ubuntu-restricted-extras (or lubuntu-restricted-extras etc, depending on what version you're running), which downloads various patent-encumbered A/V codecs. I don't have any experience getting that onto an offline machine, though.

---

### Post by puzzledinportorchard on 2013-01-30
About blank lines: will do.  Sorry.  Odd error to make - generally, 'blank' is my forte.

Will try the hint given.  It will work, I gather, if the program is currently on Synaptic's list and links haven't changed in the last month.  Will report results tomorrow (the strange way I have to do things restricts my opportunities to do work.)  Thank you very very much for taking the time.

---

### Post by puzzledinportorchard on 2013-01-31
Hmmm.  Beginning to wish I'd started this in the "I'm A Klunkhead" forum.  As above, the only way I've been able to install anything in Linux is over the last two days, using Synaptic.  And Synaptic never heard of 'ubuntu-restricted-extras'.  I guess what I'm running is actually called Xubuntu, since that's what it says upon startup: but Synaptic doesn't show 'xubuntu-restricted-extras' either, or any other variation of spelling I could come up with, or anything even close. Very possibly I have entirely the wrong idea here, but if Synaptic doesn't know what this is, and generate a script for me, I'm lost.  I should say though this isn't all that important to me.  I now have my Inkscape, and I'm content. Somehow I thought this would be an easy and common problem.

If you wonder why the fear of the CLI - now don't laugh yourself sick, here, but - I once, using bash in Ubuntu 8, turned a working dual-boot system into an inelegant doorstop.  I kid you not.

It was even a lousy doorstop.

---

### Post by Yellow Pasque on 2013-01-31
The packages you need are gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly (and all of their dependencies).

Really, if you don't have a net connection, you are better off using a distro where the whole repo is available on a DVD.

> I once, using bash in Ubuntu 8, turned a working dual-boot system into an inelegant doorstop
Unless you're talking about physically damaging the hardware, it wasn't a doorstop (and you won't be the first/last to bork an OS on the hard disk).
As for me, I fried a hard disk by connecting it to the wrong Molex power connector (I had swapped some pins on the connector to make the fan run off 5V for noise reasons).

---

### Post by puzzledinportorchard on 2013-01-31
Hey, I like that: to 'bork' a hard drive.  And I understand 'distro', but . . . repo?  I never had nuthin repo'd.  Still, you make a good point.  I'll go hunt for - oh, repository!  Okay, with you now - those gstreamer files you mention.  Pretty sure I saw them fly bye once in Synaptic.

I must say, though; 'plugins-bad' and 'plugins-ugly' is a little frightening . . .

---

### Post by puzzledinportorchard on 2013-01-31
WOOHOO! Synaptic had those, made the script for them and their dependencies; booted the online machine with the LiveCD session; no '404's or anything; now have them in my pocket and will trot back to the offline computer and we'll see where we are.  Many many thanks.

---

### Post by puzzledinportorchard on 2013-01-31
Again, hmmm. . . Synaptic did its job successfully, but the results are curious.  Mpeg plays just fine - don't know about sound, I haven't got speakers yet, but they look good.  And nothing gets me a complaint about needing demuxers - man, what an ugly word - but mp4's will seem to be playing with no picture (just the Parole logo) instead of the message about needing a decoder they used to get, .wmv's now need a decoder instead of the previous Advanced Streaming Format demuxer demand, and .mov and .avi still show no picture though appear to play, just as they did before.

So we progress.  A bit.  I think.

Here, if this is not wandering from the task at hand, is what seems odd to me about all this.  My offline computer is a Pentium 4 that was refurbished, and Ubuntu installed, by people who have been doing this for years.  And I have made no changes to anything except installing those few things I've done the last two days, described herein.  So it can hardly be my system.  But that would suggest that everyone using Parole on 12.04 would have the same problems, and that certainly doesn't seem to be the case; all I find when I search is commentary about Parole not needing plugins.  Have I reached a new high in obtuseness?

It all seems so strange and unlikely.  I'm bewildered.

---

### Post by howefield on 2013-01-31
> **puzzledinportorchard said:**
> Here, if this is not wandering from the task at hand, is what seems odd to me about all this.  My offline computer is a Pentium 4 that was refurbished, and Ubuntu installed, by people who have been doing this for years.  And I have made no changes to anything except installing those few things I've done the last two days, described herein.  So it can hardly be my system.  But that would suggest that everyone using Parole on 12.04 would have the same problems, and that certainly doesn't seem to be the case; all I find when I search is commentary about Parole not needing plugins.  Have I reached a new high in obtuseness?

Parole is the default media player that comes with Xubuntu, and with your previous comments it does indeed seem that you are running Xubuntu, so probably best to stop confusing the issue by referring to Ubuntu. :-) 

Yes, I would guess that everyone obtaining a system from this vendor would have the same problem. But most wouldn't have it in an offline situation I guess.

---

### Post by puzzledinportorchard on 2013-01-31
I don't get the significance of the difference.  When I look through the packages, and the shell scripts Synaptic uses, 'xubuntu' is never mentioned; only 'ubuntu'.  The only thing I can find anywhere on my system that says 'Xubuntu' is the start-up screen, briefly. Still, I will comply.  I *think* I get the point: Xubuntu being a particular distro of Ubuntu.  Right?

I tried to download 'gstreamer0.10-ffmpeg' and it's dependencies, but got 404 errors. Got 'libmp4v2' successfully but it made no difference.  So I think now my task will be to make that offline package reload update to Synaptic referred to above, and see if I can get this resolved that way.  Once again: thank you for your time and patience.

---

### Post by puzzledinportorchard on 2013-02-01
For anyone reading this thread because they're having the same trouble, the hint about 'ubuntu-restricted-extras' seems to be the right one.  I'm having problems with installing it, but once I do I'll post how it goes.

---

### Post by mc4man on 2013-02-02
.mp4 vids MAY be affected by a gstreamer bad plugin bug. You may wish to try the fixed plugin that currently is in precise-proposed. Directly available here, pick arch (32 bit - i386 or 64 bit - amd64
[https://launchpad.net/ubuntu/+source/gst-plugins-bad0.10/0.10.22.3-2ubuntu2.2](https://launchpad.net/ubuntu/+source/gst-plugins-bad0.10/0.10.22.3-2ubuntu2.2)

Or in your online install enable the proposed  repo in software sources > updates, reload your sources & update the bad plugin packages
(typically 2 - 

gstreamer0.10-plugins-bad_0.10.22.3-2ubuntu2.2
libgstreamer-plugins-bad0.10-0_0.10.22.3-2ubuntu2.2

---

