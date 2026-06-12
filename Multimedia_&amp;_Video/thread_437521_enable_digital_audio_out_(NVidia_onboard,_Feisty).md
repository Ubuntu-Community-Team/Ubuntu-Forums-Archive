---
title: "enable digital audio out (NVidia onboard, Feisty)"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by Finch75 on 2007-05-08
Hello everybody!

Last weekend, I decided to give Ubuntu a try and so far, I'm really thrilled ;-) In only two days (well, I did have to work as well...), I got so much more working than I had expected. So far, I have the following working: NVidia graphics drivers, Beryl ;-), Tomcat, Eclipse, OpenVPN, MySQL, Wine + 3 important Windows-applications, ivtv for my PVR-350, MPEG2-playback through PVR-350, simple command line capturing, MPlayer, VNC, VMPlayer, my scanner, ...  and this was the first time I ever installed Linux! Wow!

There are still a couple of "issues" on my list, but I had really expected more problems! This is great! I had planned on "playing" (i.e. experimenting) with Feisty Fawn now and then start "really using Linux" next year... However, if you guys can help me a little bit, I might be able to switch to Ubuntu as my "main OS" even with Feisty! ;-)

So here we go: I have an Asus M2NPV-VM board with an nForce 430 chipset. Uhh, actually, I'm not sure if the chipset delivers the onboad sound? Well anyway, it's this board:
[http://de.asus.com/products.aspx?l1=3&l2=101&l3=296&l4=0&model=1138&modelmenu=1](http://de.asus.com/products.aspx?l1=3&l2=101&l3=296&l4=0&model=1138&modelmenu=1)

I had no problems with the graphics (except when I tried to manually install the newest driver version *erm*) and the sound seems to be working as well.

However, the sound has two digital outputs (coax, S/PDIF) and I want to use them. For one thing, i want the best quality for my FLAC-files (any yes, I do have speakers that make you hear the difference...), but most of all, I will need this for playing DVDs with 5.1 sound, right?

Speaking of which: I need two things:
1) Play music (stereo) and system sounds though optical out
2) Pass the audio from DVDs to my receiver in best quality... AC-3 or whatever... 

Where can I configure that? I've had no luck with the menus so far and really don't know enough about Linux to start experimenting with the command line (I'm fully capable of copying commands and pasting the result, though *g*). Possibly, everything is installed and I just need to find the right switch? (i have lots of stuff listed in the mixer panel, e.g. Front, Surround, Center, LFE... However, afaik, all of that is also supported as analog out through three "stereo" connectors)

Thanks a lot for your help! ;-)

---

### Post by Verbatim9 on 2007-05-15
I haven't had much luck getting the digital part of the onboard sound to work so far under Edgy, though I'm no expert. I'm still using the analog sound myself...but I understand that support has improved significantly in newer versions of ALSA (pre-Edgy you had to compile a newer version of ALSA just to get analog audio working), so it could be working better under Feisty...There's [a post over at the KnoppMyth forums](http://mysettopbox.tv/phpBB2/viewtopic.php?t=14554) from someone saying they have PCM audio working under ALSA 1.0.13rc3 (not sure how that compares with the version in Feisty), using /dev/adsp as the output, but they were still having trouble getting passthrough audio to work.

---

### Post by Finch75 on 2007-05-20
still no luck :-(

Somebody suggested using Alsa mixer (shell program using "ASCII graphics" :-))

It seems to do a lot of things, but does NOT list my digital out (or at least I couldn't find it) :-(

I have not read the KnoppMyth forum because it wants to force me to register just to READ the thread. I hate forums like that... :-(

Does it say anything highly relevant that you could post here?

Thanks for the hints, I guess I'll have to keep looking and/or waiting :-(

---

### Post by Meir on 2007-05-28
Try going to System->Preferences->Sound and trying the different outputs. For me the digital is NVidia CK8S - IEC958. Good Luck.

---

### Post by Finch75 on 2007-05-30
Yes, I think I've tried that before... just to be sure, I tried it again and it didn't work :-(

I have the following choices:
[LIST]
[*]AutoDetect
[*]AD 198x Digital
[*]AD198 Analog
[*]ALSA
[*]ESD
[*]OSS
[/LIST]

Of course "AD198x Digital" looks promising, but if I choose it and press "Test", I get no sound at all. 
With ALL other choices, I get a sound :-(
(and yes, the digital out is properly connected and works in Windows)

Hmm, too bad :-( I *really* want the digital sound to work, especially for 5.1 sound, but also for the much better quality in general...

---

### Post by pierredeaustin on 2007-07-13
I also have a M2NPV-VM mobo with SPDIF out. I've been searching for the last few days and finally got digital out working by upgrading to the latest version of alsa (14rc4) and following the instructions at [http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut). Just needed to unmute the IEC958 channel and that was it. I'm not even sure if the alsa upgrade was necessary.

Note: At this point I am only getting the digital test tone. Amarok is still playing through analog and I haven't tried anything else.

---

### Post by hackmeister on 2007-07-17
> **pierredeaustin said:**
> Just needed to unmute the IEC958 channel and that was it. I'm not even sure if the alsa upgrade was necessary.


Upgrading was NOT NECESSARY. I simply unmuted IED958 in alsamixer and checked off pass through for digital signal in the MythTV setup screens. I can watch DVDs (with Dolby 5.1 and DTS) and listen my music collection through my receiver. The ASUS M2NPV-VM is a great board for a MythTV box. I love it.

---

### Post by 2WhEElTeRRoRisT on 2007-07-20
I was having some similar issues. This has helped me quite a bit, I have xmms, mplayer, and gxine playing sound. I have an issue where it won't play system sounds, like login, and it also won't play any sound when I am doing anything else. For example, any videos I watch off the internet with Firefox I can't hear anything. I went into the sound preferances and changed them all to the IED958 setting. The test noise works for all of them, but I don't hear anything anywhere else. Any ideas for how to fix this would be greatly appreciated

---

### Post by l0b0 on 2007-08-02
I'm also unable to get **digital** 5.1 audio working. In Feisty, enabling digital stereo audio out was just a matter of enabling the IEC958 channel and yanking up the volume. But no luck with the rest. I've got an ASUS P5K-E motherboard, which according to 'aplay -l' has an Intel AD198x audio chip. If anyone could post their working .asoundrc for 5.1 digital, or point to working instructions for how to achieve this, I'd be *very* grateful.

---

