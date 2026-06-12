---
title: "Audio Made Easy"
date: 2009-08-02
forum: Multimedia Software
---

### Post by freakalad on 2009-08-02
Why does audio have to be so RIDICULOUSLY complicated?
Why can't we keep thing SIMPLE & get it TO JUST WORK!?

1st, there was OSS, then ALSA, and now we're stuck with the complete dog's breakfast that is PulseAudio? I kinda understand the reasoning for it (client-server), but not at the cost of making everything SO convoluted that I need a masters degree to get it working.

The simplest way I could work with PulseAudio, is to simply remove it. I've tried using it correctly, but it causes more trouble than it's worth, and never mind trying to explain to laymen users why they need no less than 3 sound subsystems!

I'd be willing to try Pulse again, if it can be clarified in some VERY simple & clear manner, that can be explained to windows users switching over, otherwise, what's the point?

Any ideas if this'll be finally fixed in Koala?

For instance:
At the moment, I'm trying to set a user up with a pretty typical config; nothing overly fancy:
* Netbook, with either Ubuntu NBR, or a custom distro, like eeeBuntu
* FireFox as browser, with necessary Medibuntu/restricted extra's loaded to view videos on YouTube
* Skype client loaded, because that's what they know & what they expect
* Either Pidgin or Empathy as the IM client
* VLC or Totem to watch videos
* RhythmBox or Amarok/Banshee for Audio/iPod sync
* Twinkle (or Ekiga at a push) as a SIP client
* Option for the use of on-board AV devices, or additional USB devices (headset, possibly...)

Now, under the current default installation (whichever way you try & config it) you are unable to load & run all these apps simultaneously; you'll have to shut some down in order to reconfig the audio configs (gnome-sound-properties, ALSA config, PulseConfig, app's own config, etc, etc) in order to use the another app.

Even if ALL audio go into & come out of the same pool without getting locking issues & I can actually then physically mute or turn off the various devices, that'll be fine by me.
If I need anything else more complicated, THEN I'll be willing to go through the whole sing & dance.

---

### Post by alanrburns on 2009-08-02
I have been using ubuntu since 6.10 and I have never seen any thing as stupid as pulseaudio 

WHY when I use rhythmbox and then go to youtube sound stops working? 

I have found this with 8.10 9.04 32bit 64bit tested on more the 5 systems.

pulseaudio is the bug.

---

### Post by lswb on 2009-08-03
I agree, I used dapper until hardy was released, and sound sure was a lot simpler back then, it "just worked" (tm) I understand the reasoning behind PA but it is not a finished product yet. I've had to change configuration/add packages to get PA to work with every release I've tried that uses it (8.04, 8.10, and 9.04) The only perceived advantage at this time, for me, is the per application volume control.

---

### Post by igorzwx on 2009-08-03
PulseAudio is a problem.
It is a security problem first of all.
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[Have anybody tried to penetrate Ubuntu box with PulseAudio installed?]("http://ubuntuforums.org/showthread.php?t=1209361") 			([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1209361") [2]("http://ubuntuforums.org/showthread.php?t=1209361&page=2") [3]("http://ubuntuforums.org/showthread.php?t=1209361&page=3"))

[http://ubuntuforums.org/showthread.php?t=1209361](http://ubuntuforums.org/showthread.php?t=1209361)

read this:
[http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20botnet&ie=UTF-8&oe=UTF-8)

---

### Post by freakalad on 2009-08-03
That's bad.
That's VERY bad.

PA is then not only a bug, but a significant design flaw (if I'm reading that right).

Can't conceive that this is outside of beta, never mind that it's the default in a standard Ubuntu installation!

The complications arising from PA's config could lead to compromisable systems... 
I've seen this happen many times before: users simply "want things to work", and disable many security features to simplify matters

---

### Post by igorzwx on 2009-08-03
[COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[How to remove PulseAudio and fix sound with ALSA and ESound]("http://ubuntuforums.org/showthread.php?t=1230561")
[http://ubuntuforums.org/showthread.php?t=1230561](http://ubuntuforums.org/showthread.php?t=1230561)

[B]Audacity works (playback and recording).
VLC works.
Skype works too.

[/B][State of sound in Linux not so sorry after all]("http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html")

---

### Post by 243kof on 2009-08-04
It works for me. Apart from Skype (for which I'll just wait for a next version) and some cracking noise in Pidgin sound notifications, everything else is ok. I can play music in Exaile, watch Lost in Totem and another video in youtube at the same time. I can surely understand your frustration, I just wanted the other side of the story to be heard, because users for which things work rarely bother to mention it.

---

### Post by freakalad on 2009-08-04
> **243kof said:**
> I can surely understand your frustration, I just wanted the other side of the story to be heard, because users for which things work rarely bother to mention it.

I think PA would be absolutely **fantastic** once the usability issues have been sorted out, and I have a pretty good idea *why* PA should be considered superior, but the problems stem from the complexity in usability & configuration.

If a technology is not easily usable, it matters little how great the tech is, if it does not gain user acceptance.

For me, everything went swimmingly (music, media, skype, etc), until I had to start doing VoIP testing (well, this is the simplest example for now). Granted, this may not be a PA issue in itself, but the fact that PA caused unneeded complication on other areas didn't do it any credit

---

