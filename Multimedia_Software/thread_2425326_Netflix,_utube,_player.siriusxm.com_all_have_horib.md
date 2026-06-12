---
title: "Netflix, utube, player.siriusxm.com all have horible audio"
date: 2019-08-24
forum: Multimedia Software
---

### Post by Kusho on 2019-08-24
Fresh install of Ubuntu 19.04.  This is on an AMD 8 core Rizen 7 I think it is called with 32 gig ram.  Anyway this fresh install fixed most of my issues.  Before player.siriusxm.com wouldn't even make any sound, with 18.04 but now it works, kinda.  Siriusxm plays alright but I will get 5-20 seconds of lagging.  Just horible audio.  Then it will play like normal for a while.  Netflix I get the same lagging audio but it makes it unwatchable.  Utube is just as bad.  Now my pc is decently new so I don't think that is the problem.  I can't be the only one with this problem but either my searches are not finding the fix, or I just suck at searches.  Any help would be appreciated.  Thanks.

---

### Post by Kusho on 2019-08-24
Ok searched some more and may have found a fix.  Atleast made it better.

[https://ubuntuforums.org/showthread.php?t=2365905&highlight=lagging+sound](https://ubuntuforums.org/showthread.php?t=2365905&highlight=lagging+sound)

Might take longer to see if this completely fixes the issue.

---

### Post by Kusho on 2019-08-24
Not fixed.  But better.  did the 

#
# Decrease swappiness value
vm.swappiness=10

in other post.  Any thoughts on what else to try would be appreciated.  Still using firefox and default plugins that come with ubuntu.

---

### Post by Kusho on 2019-09-04
Is it because I replied to my own post that no one else replied?  Or is this forum just dead?  Still having this issue.  Thanks.

---

### Post by wildmanne39 on 2019-09-04
Most likely it is because you need to bump your thread once every 12 to 24 hours to keep it in view of the volunteers here on the forum.

---

### Post by CatKiller on 2019-09-05
While it's true that people might not have seen your thread (I hadn't before now) a big problem is that you haven't given any details of your hardware or configuration: there's nothing to go on for someone to help you with.

There's a stickied Sound Troubleshooting thread that will show you how to provide detailed information, and there may also be something there that would help directly.

I've not had any real trouble with audio on Ubuntu, but I use external devices that I knew would work in advance. Onboard sound can have all sorts of quirks.

---

### Post by Kusho on 2019-09-07
I will look into that.  Thanks.  I'm using an ASUS AMD ROG STRIX B350-F Gaming motherboard and yes using the onboard sound.  It's late here to look for that thread, but will do.  Don't know if that is the kind of info you were wanting.

---

### Post by CatKiller on 2019-09-07
Well, that's enough to know that they've given the sound chip their own branding (SupremeFX in this case), which is often a sign that it's been monkeyed with as a "value add." Support for the underlying chip (S1220A) appears to have been added relatively recently, and there are quite a few reports of various sound problems being fixed by a BIOS update.

Hopefully someone more versed in the quirks of onboard sound will be able to give you more concrete help once you post details of your configuration.

---

### Post by Kusho on 2019-09-12
Tried streaming on Cromium and there are no audio issues.  So it is isolated to Firefox.  Is it still my onboard sound?

---

### Post by (kyT%0) on 2019-09-12
> **Kusho said:**
> Is it still my onboard sound?

seems highly unlikely.

---

### Post by Yellow Pasque on 2019-09-13
> **Kusho said:**
> Tried streaming on Cromium and there are no audio issues.  So it is isolated to Firefox.  Is it still my onboard sound?

Just to confirm, if you play a file locally (in Rhythmbox or whatever), there are no issues?

---

### Post by Kusho on 2019-09-14
Downloaded Google Chrome and I can do everything in there that I wanted to do in Firefox and sound works fine. Chrominium wont do Netflix.  So I went with Chrome.   I would still prefer to use Firefox but either no one else experiences this or I don't know.  Yes I never had any issues other than in Firefox.  I play movies with the built in movie player.  Don't have any sound files to try with Rhythmbox.  but games work fine.  Audio works great.  Only issue was in Firefox.  That is the browser that comes standard with Ubuntu and I was trying to stream music or videos thru it and having horrible audio.

---

### Post by Kusho on 2019-09-18
Installed Google Chrome.  I can do everything in there I wanted to do in Firefox and no sound issues.  I would still like to figure out why I can't use Firefox to stream videos or audio without horrible sound thou.  I would prefer to use Firefox to Google Chrome.  Also how do I nudge a post?  Do I have to repost?  I have tried editing but that doesn't seem to do it.

---

### Post by Yellow Pasque on 2019-09-18
> **Kusho said:**
> Also how do I nudge a post? Do I have to repost? 

Yes. wildmanne suggested 12 to 24 hours, but that seems very excessive to me for this subforum. There are still threads on the front page that haven't been replied to in 2 weeks.
Maybe bump/nudge once a week unless you have more information to add.

---

### Post by Yellow Pasque on 2019-09-19
Speaking of information, perhaps you could provide a bit more. Go to the "about:support" page in firefox and copy the text to the clipboard. Paste it here, and remember to use code tags. The part I'm interested in is the Media section (example below), so if you want to trim the rest out, feel free.

```
Media
-----

Audio Backend: remote
Max Channels: 2
Preferred Sample Rate: 44100
Output Devices
Name: Group
Family 17h (Models 10h-1fh) HD Audio Controller Analog Stereo: /devices/pci0000:00/0000:00:08.1/0000:09:00.6/sound/card1
GM206 High Definition Audio Controller Digital Stereo (HDMI 2): /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0
Input Devices
Name: Group
Monitor of Family 17h (Models 10h-1fh) HD Audio Controller Analog Stereo: /devices/pci0000:00/0000:00:08.1/0000:09:00.6/sound/card1
Monitor of GM206 High Definition Audio Controller Digital Stereo (HDMI 2): /devices/pci0000:00/0000:00:01.1/0000:01:00.1/sound/card0
```

---

### Post by Kusho on 2019-09-22
Never figured out how to do Code tags.  I'm sure it's something simple...

Also I'm having a second more serious issue where my monitor goes to sleep and never wakes up.  Started a new forum post 
[https://ubuntuforums.org/showthread.php?t=2426825](https://ubuntuforums.org/showthread.php?t=2426825)

I can boot into Ubuntu but after a few minutes of inactivity my monitor goes to sleep and will not wake up.  I have ordered a new video card, but for now have been using Windows.

I will boot into Ubuntu and try to get this info for you...  but like I said I don't know how to do Code tags.

---

### Post by Kusho on 2019-09-22
Media
Audio Backend	remote
Max Channels	2
Preferred Sample Rate	44100
Output Devices
Name 	Group 	Vendor 	State 	Preferred 	Format 	Channels 	Rate 	Latency
GF114 HDMI Audio Controller Digital Stereo (HDMI 2)	/devices/pci0000:00/0000:00:03.1/0000:26:00.1/sound/card0	NVIDIA Corporation	Enabled	None	default: S16LE, support: S16LE S16BE F32LE F32BE	2	default: 44100, support: 1 - 384000	0 - 0
Family 17h (Models 00h-0fh) HD Audio Controller Analog Stereo	/devices/pci0000:00/0000:00:08.1/0000:28:00.3/sound/card1	Advanced Micro Devices, Inc. [AMD]	Enabled	All	default: S16LE, support: S16LE S16BE F32LE F32BE	2	default: 44100, support: 1 - 384000	0 - 0

---

### Post by Kusho on 2019-10-02
Okay replaced my Video Card and reinstalled Ubuntu from disk.  (For another issue.)  But that did not fix this issue.  Still having the same bad audio in Firefox.  Reinstalling Google Chrome until this is fixed.  Any other thoughts?

---

