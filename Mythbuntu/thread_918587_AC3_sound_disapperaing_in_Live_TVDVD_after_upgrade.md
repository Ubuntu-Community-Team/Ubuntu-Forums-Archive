---
title: "AC3 sound disapperaing in Live TV/DVD after upgrade"
date: 2008-09-13
forum: Mythbuntu
---

### Post by Freddan101 on 2008-09-13
After my upgrade to version 0.21.20080304-1 of MythTV (still running 7.10 of Ubuntu) the AC3 sound is not working well in Live TV, Recordings and DVD, i.e. MythTV internal player. I get sound in about one second before it disappears. Sometimes it comes back after a while just to disappear again. All non AC3 sound work well.

This worked before the upgrade of MythTV and in Mplayer, i.e. ripped material, there is no problem. The frontend log doesn't reveal much unfortunately.

Anyone with the same experience?

---

### Post by volkswagner on 2008-09-13
This is an ongoing problem.

Please post your hardware.  Are you using spdif, or multi analog out>

Some have had joy by changing max channels set to stereo rather than 5.1 in frontend general settings.  This setting still plays multichannel on spdif, not sure about analog outputs.

Some have had joy by changing the sound card from ALSA:Default

see last post here

[http://ubuntuforums.org/showthread.php?p=5516332#post5516332]("http://ubuntuforums.org/showthread.php?p=5516332#post5516332")

I still have issues with AC3 on HD channels.  It appears myth cant make up it's mind on weather to use AC3 or stereo since they are both present.

---

### Post by Freddan101 on 2008-09-15
I'm using spdif out from my motherboard Abit An-M2HD (AMD AM2)with Nvidia chipset and Realtek onboard sound. 32bit Mythbuntu OS.

I've tried all the settings combinations in the other post but no luck. :(

---

### Post by volkswagner on 2008-09-15
Did you check the frontend.log after each edit?  Were there any changes to the logs?  Does your receiver have a display, showing current audio format?  I wonder if your receiver shows the same input constantly change from analog to AC3 back to analog? 

Does the video play at proper speed when you have no sound?

---

