---
title: "SN25P sound will not change internal clock from Optical"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by FrozenFOXX on 2007-05-23
Okay, this problem is having me pulling my hair out so I'll try to be as descriptive as humanly possible.

I am using the AMD64 build of Feisty Kubuntu and have been running it reliably now for about a month.  No problems until now.

All sound output has ceased as of about four, five hours ago.  I normally have my 5.1 setup on my Shuttle SN25P (has a built-in VIA Envy24HT audio chip, properly detected) with no additional input aside from the occassional bit of Line-In recording.  No issues prior to this.

I hooked up my XBox 360 in the same room and plugged the optical out jack of that into the optical in jack on the SN25P.  In order to try to get it to play the sound I went into Kmix and changed the inputs to record from the optical input, play the optical input, and changed the timing to the optical input.  Still no sound.  I disconnected the 360 from the computer entirely and went about to set the sound settings back.


Now absolutely zero sound outputs with the default installation.  Trying to change any of the options through either Kmix or alsamixer (either as a normal user or as root) has no lasting effect.  As soon as you touch any other settings the timing and recording buttons go EXACTLY back to what they were.  I have tried some custom .asoundrc files from the ALSA project to no change.  I have using Adept removed the alsa-base and alsa-utils packages and rebooted the system.  For some reason all the installed utilities and such remain anyway (why it says it successfully removed them if they're **still there** is beyond me).  I reinstalled the two aforementioned packages to no avail.


I have turned off the computer completely, including shutting off the main power switch.  No change.  I have cycled the BIOS.  No change.  I've rebooted and restarted services multiple times.  No change.  I have enabled, disabled, and otherwise changed the options around in the KDE Sound System (including "enable sound system" and "sound output system" dialogues) multiple times.  No change.



In a fit of desperation and insanity I booted up the Feisty LiveCD.  Sound works.  Perfectly I might add.  No further configuration required, all settings are as they should be.  Playing sound files is no issue.  I drop the LiveCD, come back to the installed environment, it is as if nothing was changed at all, there is still no sound, none of the settings stuck, and all is as it was before.




Honestly, this is REALLY starting to piss me off.  Any advice would be welcomed.

---

### Post by FrozenFOXX on 2007-05-23
Already off of the front page, figured I'd mention some additional experimentation.

From some extra testing with the LiveCD I've come to determine it must be some program or setting that is preventing the switch back to the 48000 Internal Clock setting from the Optical In setting.  Normally I'd rip out the whole linux-sound-base package but that would basically completely uninstall my system and that's not really a good thing.  I've tried poking around at the config files but I can't find much of anything.


Trying /etc/init.d/alsa-utils stop doesn't seem to quite do what I need.  Is there any way to completely and TOTALLY disable **ALL** access to the sound device?  Perhaps if nothing was accessing it it would allow me to change it?


I dunno, just trying to think up some ideas here.

---

### Post by FrozenFOXX on 2007-05-23
Thanks to crimsun in the #kubuntu channel of IRC I now have my problem resolved.  Essentially the /var/lib/alsa/asound.state file got screwed up.  Removing it fixed the issue.

---

### Post by Liquid2006 on 2008-02-11
If this works I shall be the happiest camper. I've spend days trying to figure out what I did wrong when I plugged in an optical cable into my Shuttle SN25P.

Thanks for posting the fix for the rest of us to gain benefit from.

---

