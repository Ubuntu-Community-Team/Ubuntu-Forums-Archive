---
title: "[SOLVED] Sound stopped working in 8.10"
date: 2008-12-29
forum: Multimedia Software
---

### Post by gruss on 2008-12-29
Lost all sound today, I'm at a loss. 
PC seemed to be a little unstable and transmission of all things locked up on me when I VNC'd in to check progress.  When I physically got to the pc my daughter wanted to watch a movie on it and I noticed there was no sound so i back tracked and tried to figure out what happened.

I read that my Hauppage WinTV pvr USB was "plug and play" but when plugged in the pc does not shut down properly, so unplug that and reboot...still no sound.  Its been plugged in for a couple days so I didnt think that was it.  Caused a shutdown issue but didn't seem to effect anything else.

Tried a little changed to xorg.conf earlier today, still had sound after change BUT to be on safe side reverted to backup, reboot still no sound.

Plugged in KNOWN working headphones to make sure it wasnt speakers, nope

Threw in my old faithful 1st gen SB Audigy to see if it was the built in card on this pc...nope still nothing on headphones or speakers.

I'm at a loss, like I said didnt really notice anything wrong until I remoted in?  can VNC hose something up that bad?  When I play a song it looks like everything is A-OK, I can even notice a spike in CPU usage if I hover over a song...when i got to the pc after my remote session it showed it was muted, of course I turned that off but still seems, to me anyway, to be the most likely culprit.  Any ideas how to kickstart it would be appreciated and I'm fully aware it may just be my ignorance or one of the kids clicking where they ought not be clicking, but I'm out of ideas ;)


Not sure exactly what happened to the onboard card initially but solved via these threads:


[http://ubuntuforums.org/showthread.php?t=1023895](http://ubuntuforums.org/showthread.php?t=1023895)

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Re-installing alsa did it!  Kudos markbuntu!

---

