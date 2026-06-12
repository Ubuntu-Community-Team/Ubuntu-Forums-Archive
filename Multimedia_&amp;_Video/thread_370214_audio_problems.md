---
title: "audio problems"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by kippertoffee on 2007-02-25
Hello,

I installed ubuntu about a week ago and the sound worked at first, lovely noise on startup.

Now I have no sound at all. Just stopped working.

My system is set use alsa, and my soundcard is "SBlive! platinum [ct4760p]. Changing to another driver (OSS etc.) does not help. I know that my headphones are working because when i move the fader in the audio mixer app, i can hear zipper noise, and so the card is clearly putting something out.

Can anyone offer any help, I'm thoroughly confused.

Cheers, pete.

---

### Post by kippertoffee on 2007-02-27
*bump*

---

### Post by Andrew Pape on 2007-03-01
Hi ubuntu gurus. 

I've almost got sound working fine with ubuntu. All the ubuntu sounds (clicking, logging in, logging out, etc) work fine, but my Java application doesn't play sound when it should. I have checked the case sensitivity of the ".wav" sounds that are meant to play, and checked that the files exist, but get no sound. The "wav" files themselves are playable from the ubuntu media player (whatever it's called). At this stage, it would appear that my problem is a programming problem, but twice the sounds have played from the app! In both cases, it was after I did a system change. The first time, the sound played after changing the screen resolution. In the second case, the sound played after changing the xconfig file. This is a weird problem, as it's intermittent. I think it'd make more sense if the sound never played, rather than sometimes! This is frustrating.

When selecting the sound settings in the Gnome preferences menu, I have found that the default sound card is always the Intel onboard card. When I bought my Sound Blaster Vibra 128, I had PC technicians disable the onboard sound card so that the Sound Blaster would take precedence. On ubuntu, the Sound Blaster card is listed as "AudioPCI", so I selected that. But whenever I go back to the sound settings, the default card is always set to the onboard card. I figure this could be part of the problem. I found another thread where someone said how to set a default sound card permanently, like this:

sudo asoundconf set-default-sound-card AudioPCI (after first listing the available sound cards as both the onboard Intel and the AudioPCI with: sudo asoundconf list).

Unfortunately, the command doesn't work on my system, even after rebooting. I'm still stuck with the onboard Intel as default. I also read that even if the onboard card is disabled, it is not necessarily ignored by Linux, which seems to be the case for me.

It seems that I have to somehow upset the Linux O/S settings in order to get sound out of my app, which is mighty strange. Any help would be greatly appreciated.

Thanks in advance,

Andrew.

PS. For those guys who have either never had sound, or else had it working and then lost the sound, I'm sorry I can't help. I'm pretty new to Linux too.

---

### Post by deadgobby on 2007-03-01
You may need to reload/install ALSA. All so my question are you running a sound card or built in sound on the mother board?
Gobby

---

### Post by Andrew Pape on 2007-03-01
Hi Gobby,

>You may need to reload/install ALSA. All so my question are you running a sound card or >built in sound on the mother board?

I'm running a sound card (Sound Blaster Vibra 128 rather than built in sound on the motherboard, although there is still a built in sound chip that was disabled by technicians when I got the sound card). 

Regarding ALSA, I tried it out on the preferences->sound menu, and found that the test sound worked when playing with ALSA. So it would seem that ALSA is already installed on my machine when I installed ubuntu. Ubuntu plays its sounds after I've changed to ALSA on the menu, but my app still makes no sound. I tried some of the ALSA utilities: first I tried "alsaconf" at the command line, but no program was found. I then tried "alsamixer", which said I had an AudioPCI, sound card, which seems to be Linux's new name for Sound Blaster cards. On the sound preferences->sound menu I tried other options, but had no luck. In particular, the OSS system prevented ubuntu from playing any sound at all, not just my app's sound. 

So, do I still need to install ALSA, or maybe the problem is due to the Intel onboard speaker being constantly detected as the default sound card?

Any help would be greatly appreciated. Thanks.

Regards,

Andrew.

---

### Post by Andrew Pape on 2007-03-02
Hi,

I seem to have solved the problem. I mentioned that I'd had technicians disable the onboard sound, but I actually went to verify this and found that the BIOS had the setting turned on, not off. Windows always worked with the sound card despite the setting, but it was problematic on Linux.

I followed a sound guide on the ubuntu forum:

[http://http://ubuntuforums.org/showthread.php?t=205449]("http://http://ubuntuforums.org/showthread.php?t=205449")

This at first did the trick, as x windows defaulted to my sound card instead of onboard chip. and my app's sound worked. But after a reboot, the onboard chip was the default again. I followed the instructions further, so that the sound card should be detected every boot, but that didn't seem to work. 

So, in the end, it was disabling the onboard chip with the BIOS that did the trick. Linux no longer detected the chip, and so couldn't default to it.

I hope that helps anyone else who has an onboard Intel chip and wants to get a Sound Blaster (or other sound card) to work.

Cheers,

Andrew.

---

