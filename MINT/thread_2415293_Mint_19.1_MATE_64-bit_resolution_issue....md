---
title: "Mint 19.1 MATE 64-bit resolution issue...?"
date: 2019-03-23
forum: MINT
---

### Post by RallyDarkstrike on 2019-03-23
Hi all - having a bit of an odd issue here.

I have a spare desktop PC that works fine - Intel Core 2 Duo, 6GB RAM, Mint MATE 19.1 MATE 64-bit, etc. I also have a Dell 1704FTP 17-inch monitor. These two have always cooperated no problem. 1280x1024 is the max. res. of the monitor so that is what I always had it on. The monitor always identified in the Displays menu as what it was and I was given it's resolution options. The video card is a Radeon HD3850 if that helps.

However, back in October, we had a small basement flood which meant that our basement had to be renovated - that spare computer has been unhooked for the last few months as there was no space to set it back up. I should mention neither monitor nor computer were damaged in the flood, by the way.

I hooked the system back up today to get it back to rights / update it etc. and noticed on boot that the resolution was 1024x768 rather than the 1280x1024 it is supposed to be. It's plugged in with a VGA cable. I thought, "OK, I'll just go through the upgrades and 19.1 upgrade (it was running Mint 19 before the flood) and that should fix it."

No dice, still on 1024x768 in the Displays menu. Also, where it was identified as a Dell monitor before, it simply says 'unknown' now. Any idea what is going on and how I can get my video to properly autoconfigure again...? From when the machine was shut down in October until now, I have made absolutely no changes to the display settings, nor had I done so while or after doing the updates.

Cheers and thanks for any suggestions!

***ADDENDUM #1:***
The machine is running the latest Linux 4.15 kernel. I tried jumping back to an earlier 4.15 kernel and even a 4.13 kernel (I can't remember what kernel was last on the machine when I knew it was working at 1280x768)...no dice, still shows the monitor as unknown and the max res at 1024x768 :(

***ADDENDUM #2:***
Tried hooking the computer up to another different VGA monitor with the same max resolution, same issue.....monitor is 'unknown' and max resolution is 1024x768...? I went back even farther to a 4.4.0-38....did not make a difference. :(

***ADDENDUM #3:***
Hooked the machine up to my LG 32" TV using HDMI, this DID direct it  correctly and listed the correct available resolutions. Is this an issue  with VGA somehow?

***ADDENDUM #4:***
I tried a live-boot from a USB drive with Mint 19.1 on it....same issue....is this due to a change in the display system for Mint 19 that it no longer supports my video card?

---

