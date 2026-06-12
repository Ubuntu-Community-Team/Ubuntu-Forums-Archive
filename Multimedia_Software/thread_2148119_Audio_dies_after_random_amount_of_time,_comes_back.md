---
title: "Audio dies after random amount of time, comes back briefly after suspend"
date: 2013-05-24
forum: Multimedia Software
---

### Post by liquidsunshine@gmail.com on 2013-05-24
OS: Linux Mint Nadia (but confirmed to be an issue on LiveUSB of Ubuntu/Kubuntu 12.04.2, 12.10, 13.04 as well)
Computer: Lenovo X201i
lspci -n for Intel HDA card: 00:1b.0 0403: 8086:3b56 (rev 06)

My audio works when I first log in.  The KDE login sounds work, and if I play audio it works.  However, after what seems to be a random amount of time (generally 5-20 minutes) my speakers shut off completely.  This behavior was not a problem in Kubuntu 12.04, but is a problem now (12.04.2).  It does not happen on the Korora 18 LiveUSB (based on Fedora).

But it gets weirder.  Audio still works consistently from the headphone jack, and plugging/unplugging headphones doesn't affect the speakers once they go "dead".  Also, if I suspend the laptop, the KDE alert noise fires through the speakers as it goes to sleep.  And when I wake it up, sound will work normally again, but only for the 5-20 minutes described before.  

Things I've tried to fix the problem (none of them had any noticeable effect):
[LIST]
[*]Updating the BIOS
[*]Installing the [oem-audio-hda-daily-dkms "daily build"]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily/+build/4587392")
[*]Mucking about with the "model" option for the hda-snd-intel module (until I read that this doesn't really do anything with modern versions)
[*]Playing with alsamixer settings to make sure something isn't muted
[*]Googling every phrase related to the issue I could think of, with no obvious symptom matches
[/LIST]

I'm rather at a loss regarding how to proceed, and I'd appreciate any insight that anyone can offer.  I'm happy to respond with any logs, try any commands, etc. that are necessary to troubleshoot the issue, and I'll gladly perform these in a *buntu LiveUSB environment if anyone seriously suspects that Mint (or my previous mucking about) will get in the way of diagnosing it.

---

### Post by liquidsunshine@gmail.com on 2013-05-25
Is there any additional information I can provide to make this easier to investigate?

---

### Post by liquidsunshine@gmail.com on 2013-05-28
Bumping this one last time before giving up.  Does anyone have any advice about this issue?  :-?

---

