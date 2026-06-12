---
title: "Video Lag Issues"
date: 2011-01-25
forum: Mythbuntu
---

### Post by Nobodyspeshul on 2011-01-25
I'm having some video lag issues but I'm not sure it's with mythbuntu or if it is with some failing hardware.

I've already ran memtest86 on the memory, but how can I check the onboard video card for issues?

The symptoms are that the sound plays normally, but the video freezes every few seconds and then catches back up.

---

### Post by newlinux on 2011-01-25
Need some more info.

What version of mythtv, what make/model video card, what video driver are you using, what playback profile in mythtv are you using, what are you trying to playback? As a shot in the dark, first thing to do is to try a few different playback profiles (try slim, CPU++, normal, etc.).

---

### Post by Nobodyspeshul on 2011-01-25
[http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket%20AM2](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket%20AM2)

This motherboard and I'm using the built in video card with the HDMI output.  Latest version of myth and Ubuntu since I just did a re-image with a new 2TB HD.  I did the re-image because I was experiencing these problems with my last HD and wanted to upgrade anyways.

I checked out the wiki but didn't mention anything about playback profiles so I'll just be using the default one, where can I learn more about them?

---

### Post by newlinux on 2011-01-25
> **Nobodyspeshul said:**
> [http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket%20AM2](http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=AN-M2HD&fMTYPE=Socket%20AM2)

This motherboard and I'm using the built in video card with the HDMI output.  Latest version of myth and Ubuntu since I just did a re-image with a new 2TB HD.  I did the re-image because I was experiencing these problems with my last HD and wanted to upgrade anyways.

I checked out the wiki but didn't mention anything about playback profiles so I'll just be using the default one, where can I learn more about them?

I actually have and use that mobo (nvidia GPU). But you didn't answer most of my questions (video driver, playback profile, type of recording/video you are trying to playback). Take a look at your frontend logs when you are having the playback problems and absent any more information I recommend doing what I mentioned above - changing playback profiles to start with. It could also be an audio configuration issue.

Quick check - can you play back a recording with mplayer? Does it still experience the same laggy play? This can help diagnose whether it is a system problem or a mythfrontend configuration problem (my money is on the latter).

you can learn more about playback profiles in the wiki. You configure them in the Playback settings.
[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

---

