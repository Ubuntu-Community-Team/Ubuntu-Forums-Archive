---
title: "No Sound in Edgy - I now have 2 sound cards!"
date: 2006-11-19
forum: Multimedia &amp; Video
---

### Post by Manc on 2006-11-19
I upgraded to edgy yesterday and as yet I'm still to get the sound working.

Having looked at the forum I can see a number of users are having a few issues with sound in Edgy, however I feel my problem may differ slightly. According to my system I now have 2 sound devices. a VIA on-board device and my trusty Soundblaster 5.1, what stumps me a little is that the on-board sound has been disabled in the BIOS for the last 18 months! In all other flavors of Ubuntu and Windows it's been fine, however in 6.10 its just not 'playing ball' (even in Live CD mode). Yet when i go into Windows or any other live distro it works like clockwork!

Kaffeine is also being a bit problematic as well, I can select to play an mp3 in the application, it will try to load then disappear. However with no sound this is a secondary issue ;) I've tried a few solutions posted on here with regards to no sound with no success :(

any help appreciated :)

---

### Post by juano on 2006-11-20
I'm with the same situation. I upgraded my Ubuntu-Linux to Edgy and my sound card Sound Blaster 5.1 doesn't sound at all. It's quite strange, doesn't it!!!!!!!!!!!!!

Someone knows something about it?
Please answer....

Thanks

---

### Post by zgornel on 2006-11-20
Are the modules for the SBLive! loaded ? Recheck bios settings. Try selecting in Gnome/KDE the drivers you want to use for sounds. As a last resort, try commenting the lines refering to the via onboard card in /etc/mdules.conf

---

### Post by juano on 2006-11-20
About the modules I don't know, I'm newbie and I don't know where I should look for. About my soundcard onboard I didn't touch anything and in my Ubuntu dappers I didn't have any problem. I have selected my sound card SBLive as default.The curious thing is that all this stuff don't occurs always. I have to reboot my computer until my sound works, and beteween reboots I don't do anything.....

Please,help....
Thanks

---

### Post by joegiampaoli on 2006-11-23
Go to this guide, it helped me set up 2 audio devices in Edgy.

Cheers. ;)

[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by ThArGos on 2006-11-24
I had quite the same problem I think.
Edgy found my Sound Blaster + the Intel thing.
The problem was that Edgy put the Intel thing as the default card.

To solve this, I used "alsasound" or "alsaconf" (don't remember the exact command), to set up my sound blaster as the default card.

I don't really remember the commands I've typed but I can find them back if you need.

Well to sum up you can list the sound cards and then set up the default one.

hope it helps...

---

### Post by ThArGos on 2006-11-25
ok I checked the commands and this is what I've done:

> thargos@thargos-desktop:~$ asoundconf list
Names of available sound cards:
ICH5
Live
thargos@thargos-desktop:~$ asoundconf set-default-card Live


and it's done =)

Well for me it worked!

---

### Post by boxb on 2006-12-10
I get no sound with a SoundBlaster 5.1 (SB0680). Edgy sees it as a Dell Sounblaster Live! The driver loaded is emu10k1. Alsamixer looks OK. The number written on the chip is CA0103-DBQ. This is not a chip listed at [www.alsa-project.org](www.alsa-project.org) The box the soundcard came in does not have the word "live!" written anywhere. Any suggestions?

I might ditch this card in favour of a card that is known to work well. Any suggestions for this? I can get an Audigy Value very easily locally. I just want stereo sound for internet surfing.

---

