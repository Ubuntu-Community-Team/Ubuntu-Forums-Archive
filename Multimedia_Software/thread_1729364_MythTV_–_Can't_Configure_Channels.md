---
title: "MythTV – Can't Configure Channels"
date: 2011-04-14
forum: Multimedia Software
---

### Post by TennTux on 2011-04-14
While trying to configure the back-end of MythTV I appear unable to configure channel(s). As I understand Verizon encrypts the signal (or something like that) unless you use one of their cable-boxes. The cable-box is suppose to retransmit on either channels 3 or 4 (configurable on cable-box). I have done my best to set things up as I understand them, see details below, however, nothing seems to work and from what I have found in searching the forum nobody has had this problem.

I was able to configure in “Capture cards” the two HD HomeRun Tuners XXXXXXXX-0 and XXXXXXXX-1. I can ping the Tuner card and MythTV configuration appears to see the Tuner. However, in “Input connections” when I scan for channels I never seem to be successful. I have tried varying the configurations in “Scan Configuration” to no avail.

Any suggestions? Clues? Help would be appreciated.

I'm first trying to get Live TV and I plan on using the cable-boxes' remote (baby steps).

Hardware:
> [Verizon FiOS CableBox QIP2500-3]  Coax from FiOS to CableBox
[SiliconDust HD HomeRun Dual] Coax from CableBox to HD HomeRun
Twisted Pair Eathernet from HD HomeRun to Router with DHCP configured
Twisted Pair Eathernet from Router to MythTV Computer System

Software:
> Computer already had Ubuntu 10.10 on it.
MythTV 0.23.1+fixes26437-0ubuntu1 (Running Single Computer with Combined Front and Backend)
Ran System->Administration->MythTV Backend Setup

---

### Post by bance on 2011-04-16
You might have better luck, asking in [_[COLOR=Red]this[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=301") forum.

I use mythtv, but not with cable!..... have you set up a video source?

You must have a source associated with each tuner, in your case this would be your set top box. you would also need an EPG..... Schedules Direct if in USA or EIT/some other grabber elsewhere.

HTH  Steve

---

### Post by TennTux on 2011-04-18
> **bance said:**
> You might have better luck, asking in [_[COLOR=Red]this[/COLOR]_]("http://ubuntuforums.org/forumdisplay.php?f=301") forum.

Thanks. I had looked for this forum but didn't find it when I looked. I checked several forums for sub-forums but not the right one.

I will look around and see if there is a way to move this thread to the better forum, Otherwise, I'll open a new one there.

> **bance said:**
> You must have a source associated with each tuner, in your case this would be your set top box. you would also need an EPG..... Schedules Direct if in USA or EIT/some other grabber elsewhere.
HTH  Steve

I do have a Video Source that I use EIT with. I'm in the US, should I interpret your statement as EIT is only for NON-US or is this just a preference?

Also in while trying to get it to work I chose "Channel frequency table: try-all" in "Video source setup" figuring it would give me the most chances to find the channels.

---

### Post by bance on 2011-04-18
Ok, to have your thread moved, use the thread tools button, and report abuse:- it should give you a dialogue, where you can ask to have the thread moved..... at least I think that is the correct procedure.:P

EIT is over the air data that is transmitted with the video stream and provides the EPG (electronic programme guide) , as far as I know, cable providers don't do this.... they charge you for a set top box, which decrypts their own guide data.

Looking at [_[COLOR=Red]this[/COLOR]_]("http://www.mythbuntu.org/wiki/input-connections") page, it seems as though you should have a schedules direct account (it's not for profit, about $20 per annum) this will give you your EPG (video source). Then you would need to 'Fetch channels from source'

I should stress that I don't use cable.... so I am only surmising from what I have read!

HTH Steve.

---

