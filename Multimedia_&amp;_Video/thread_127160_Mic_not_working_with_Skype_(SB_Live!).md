---
title: "Mic not working with Skype (SB Live!)"
date: 2006-02-08
forum: Multimedia &amp; Video
---

### Post by wook on 2006-02-08
I've installed Breezy Badger on an older Dell computer. I'm a n00b to Ubuntu, but not Linux.

I'm trying to get Skype working, but can't use the mic. I can hear the Skype test echo123 as well as anything outputing sound, but can't record anything. I found this thread and setup my system as it says below (OSS default sink and source), but it didn't help.

lspic shows...

Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Alsa Mixer shows...

SBLive! Value (CT4780)

Should I abandon the mic for a USB headset. What's the best combination for Skype? Any help would be appreciated.

> 
Originally Posted by mpvano
Make sure you are NOT running the esd (enlightenment!) sound daemon.

...

Go to your "sound" preferences and make sure "enable sound server startup" is not checked.

Then go to "multimedia systems selector" preferences and make sure the default for desktop programs is OSS for default sink and default source.

Then check the preferences, man pages and documentation for every sound application you use to make sure they're not set to use esd for output.

...

At any time you are having trouble starting other sound applications, open the "System Monitor" program in "System Tools" and select the "processes" tab. Look for "esd" in the list. 

---

