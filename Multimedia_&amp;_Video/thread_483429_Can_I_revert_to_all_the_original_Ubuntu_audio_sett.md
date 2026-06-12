---
title: "Can I revert to all the original Ubuntu audio settings?"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by samuraiCat on 2007-06-24
I hate to double-post, but I think this subforum might be able to help me.

Hi, everyone. Thanks in advance.

Okay, I installed Ubuntu, and I got my Lexmark Z517 printer and nVidia GeForce FX5200 video card working great. 

But I completely screwed up my audio stuff. 

See, I physically installed a M-Audio Revolution 5.1 card, and then immediately installed the OSS drivers that M-Audio linked to via 4-Front technologies. Then I read about ALSA, and I tried to follow the instructions on the following thread unsuccessfully: M-audio Revolution and upgrade Alsa ([http://ubuntuforums.org/showthread.php?t=400268](http://ubuntuforums.org/showthread.php?t=400268))

The instructions did not work for me, especially at the end: 

> If you have any other cards (like an onboard card), you can add it to --with-cards seperated by commas. After the installation is finished, do a complete reboot. Then run
Code:

cat /proc/asound/version

to check if you successfully upgraded Alsa. The first time you reboot after upgrading Alsa or installing a new system, you must increase the volume of all channels in alsamixer.

After all that, there was no such directory as "/proc/asound/version".

Then I tried to use Hydrogen and Alsamixer, and neither of them would load! Alsamixer gave this weird warning: "alsamixer: function snd_ctl_open failed for default: Nos such device"

I uninstalled all my audio programs and drivers, reinstalled, and still nothing. 

So then I went into User Panic: I downloaded everything related to ALSA via Synaptic. I made countless tweaks to various files. I don't even know what I did.

Nothing changed. I can play movies and music with the media players, but none of the other stuff works (Hydrogen, the mixers, JACKlab, etc).

So, now I want to go back to the original and start again, as if I had just put my card into the slot. Is there a way to do this? Thanks.

---

