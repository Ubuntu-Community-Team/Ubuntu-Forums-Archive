---
title: "MythTV Edgy channel 2 does not exist"
date: 2006-12-18
forum: Multimedia &amp; Video
---

### Post by pheno on 2006-12-18
when I run mythtv-setup and then exit, I get this message:

Card 0 (type) is set to start on Channel 2, which does not exist. do you want to fix the problem?

clicking on "Yes, fix it" doesn't seem to fix it, because when go back into mythtv-setup and exit, i get the same message

what am i doing wrong?

---

### Post by NT4usB on 2006-12-18
Nothing.
I get that too. Evidently it's not a problem though. 
I just click 'no thanks, I know what I'm doing...' and move on.
btw, channel 2 exists where I live so I don't know what's up with the error message.

---

### Post by majoridiot on 2006-12-18
i got that message when i didn't do a COMPLETE setup initially... i.e. starting with the first
menu item and working through each one completely from start to finish.  once it is set up
completely the first time, there is no problem going in and tweaking indiviual settings.

at least this is what i've experienced.

---

### Post by pheno on 2006-12-19
thanks for the replies...

when you say "a COMPLETE setup initially", do you mean the "MythTV mythtvsetup" or the whole "MythTV Edgy Backend Frontend Desktop" How-to?

---

### Post by superm1 on 2006-12-19
> **pheno said:**
> thanks for the replies...

when you say "a COMPLETE setup initially", do you mean the "MythTV mythtvsetup" or the whole "MythTV Edgy Backend Frontend Desktop" How-to?
I'm thinking he means the MythTV_mythtvsetup.  Usually warnings like this will pop up if you haven't properly added a videosource (zap2it/xmltv) and/or set the default channel to a channel on this video source.

---

### Post by NT4usB on 2006-12-19
> **superm1 said:**
> ... and/or set the default channel to a channel on this video source.

Are you saying the default channel _should not_ be set to a channel on the video source?

I have zap2it for both tuners and both tuners are set to a channel that exists (afik...)
I get the error message. I ignore it. MythTV works fine...

btw... any tips on getting the remote volume control to work with mplayer (ie, playing videos in MythTV?) I had it working once, maybe as far back as 0.19, but now I got nothing. Pause, skip forward/backward, play, stop, all work. Stinkin volume is being stubborn.
I'm assuming that it's mplayer that plays videos in MythTV...

---

### Post by pheno on 2006-12-19
what the heck is "ll /dev/video?", on page two of
MythTV Edgy hardware pvr-350 TV-out?

---

### Post by superm1 on 2006-12-19
> **NT4usB said:**
> Are you saying the default channel _should not_ be set to a channel on the video source?

I have zap2it for both tuners and both tuners are set to a channel that exists (afik...)
I get the error message. I ignore it. MythTV works fine...

btw... any tips on getting the remote volume control to work with mplayer (ie, playing videos in MythTV?) I had it working once, maybe as far back as 0.19, but now I got nothing. Pause, skip forward/backward, play, stop, all work. Stinkin volume is being stubborn.
I'm assuming that it's mplayer that plays videos in MythTV...

It should be set to a channel on the video source.  If your getting this error still with it set to a channel, I'm not sure why, but as long as you have it working, just ignore it.

As for getting the remote to work with mplayer, are you using irxevent, or plain old native lirc to control things?  If your using irxevent, its a matter of making sure mplayer is keeping focus, if you rusing native lirc control, you need mplayer configuration listed in your ~/.lircrc

---

### Post by superm1 on 2006-12-19
> **pheno said:**
> what the heck is "ll /dev/video?", on page two of
MythTV Edgy hardware pvr-350 TV-out?
You'll have to ask trubblemaker.  He wrote that page, I just formatted it :)

---

### Post by NT4usB on 2006-12-20
> **superm1 said:**
> It should be set to a channel on the video source.  If your getting this error still with it set to a channel, I'm not sure why, but as long as you have it working, just ignore it.
It is, It works, I ignore it.

> 
As for getting the remote to work with mplayer, are you using irxevent, or plain old native lirc to control things?  If your using irxevent, its a matter of making sure mplayer is keeping focus, if you rusing native lirc control, you need mplayer configuration listed in your ~/.lircrc

Using lirc. It's listed in lircrc. It worked for a while.
I'm using a morphed version of 6.06 with some Edgy stuff to make 0.20 work. Probably jacked it up.

---

### Post by superm1 on 2006-12-20
> **NT4usB said:**
> 
Using lirc. It's listed in lircrc. It worked for a while.
I'm using a morphed version of 6.06 with some Edgy stuff to make 0.20 work. Probably jacked it up.
Well does anything work for lirc right now?  Or is just mplayer broke?

A good way to identify your true problem is with irw.

Irw will connect to lircd and output anything it gets from lircd that it can match to your remote info in /etc/lirc/lircd.conf.  Say you press up on your mceusb remote, it should show up and a remote code in the console.

If this doesn't work, then either your /etc/lirc/lircd.conf is broke, your remote broke, or your kernel module for your remote broke.

If it does work, then the problem most likely lies in your .lircrc.  This can be tested using ircat.

---

### Post by NT4usB on 2006-12-20
Everything that should work still works via remote. irw shows the correct responses to remote buttons.
All the Myth controls are ok while watching live or recorded TV, including volume. 
When playing videos or DVDs via Myth, most of the controls respond. Not sure how/if they are all configured but I can pause, play, skip forward/backward, etc.
Just no volume control.
I'm pretty sure remote volume worked for video and DVD after I upgraded to 0.20.
Could changing /dev/dsp? etc. to ALSA:default have jacked just the volume?
I remember screwing around and getting the remote to control mplayer volume when playing videos on mplayer. 
I've screwed up a conf somewhere... probably mplayer.
Problem is, I don't document all the messing around I do, trying to make things work. 
Makes it hard to backtrack and undo what I've borked up. *g*

---

### Post by superm1 on 2006-12-21
> **NT4usB said:**
> Everything that should work still works via remote. irw shows the correct responses to remote buttons.
All the Myth controls are ok while watching live or recorded TV, including volume. 
When playing videos or DVDs via Myth, most of the controls respond. Not sure how/if they are all configured but I can pause, play, skip forward/backward, etc.
Just no volume control.
I'm pretty sure remote volume worked for video and DVD after I upgraded to 0.20.
Could changing /dev/dsp? etc. to ALSA:default have jacked just the volume?
I remember screwing around and getting the remote to control mplayer volume when playing videos on mplayer. 
I've screwed up a conf somewhere... probably mplayer.
Problem is, I don't document all the messing around I do, trying to make things work. 
Makes it hard to backtrack and undo what I've borked up. *g*

Well to rule out problems with your .lircrc for mplayer, run

```
ircat mplayer
```
This will test all the mplayer buttons you have mapped in your .lircrc.  It will also let you know if there is a syntax error at all anywhere in your .lircrc.

---

### Post by NT4usB on 2006-12-21
> **superm1 said:**
> Well to rule out problems with your .lircrc for mplayer, run

```
ircat mplayer
```
This will test all the mplayer buttons you have mapped in your .lircrc.  It will also let you know if there is a syntax error at all anywhere in your .lircrc.

The buttons that work, work. 
Up and Down volume doesn't report anything.
Somethings borked in the mplayer conf. I think I made a backup before I started messing with it. Gonna see if I can find it... (...see if I can remember what it's called?)

Thanks for the pointers!

ed: might have found the answer...
[http://www.mythtv.org/pipermail/mythtv-users/2003-April/003296.html](http://www.mythtv.org/pipermail/mythtv-users/2003-April/003296.html)

---

### Post by michwill on 2007-04-24
Check out this post:

[http://www.mythtv.org/pipermail/mythtv-users/2006-March/128258.html](http://www.mythtv.org/pipermail/mythtv-users/2006-March/128258.html)

---

### Post by NT4usB on 2007-04-24
Sounds like the answer.
I have several orphaned cardinputs from failed attempts at configuring my A180... 
My setup looks something like card0, card1, and the A180 is card17 or 18.
Guess I'll clean that up and see if it fixes it.

---

