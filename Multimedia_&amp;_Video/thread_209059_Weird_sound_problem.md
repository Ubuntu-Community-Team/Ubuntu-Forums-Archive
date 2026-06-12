---
title: "Weird sound problem"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by BuffaloX on 2006-07-04
Hi
I have an M-Audio revolution 7.1 with the VIA envy 24 HT soundchip.
When I start ubuntu, I only have sound in left channel.
But if I adjust the volume, no matter if I adjust up or down, and it's just a minimal adjustment, I get sound in both channels.

If I then reboot, it's back to only sound in left channel.
Has anyone got experience with this?

PS
Cabling has been checked, and is A OK.

---

### Post by LordRaiden on 2006-07-04
I have the answer to in my guide in my signature. First, set your sound settings as you want them in alsamixer. Then, just do ```
sudo alsactl store 0
```

Your settings should restore to what you set them on reboot.

---

### Post by BuffaloX on 2006-07-04
Thanx
Very nice guide. ;) 

I checked the driver, and it seems OK.
Correct driver, active and working.
Ran ALSA mixer, The Mixer showed left and right channel at same level.
made the tiny twitch on the vol, to get both channels playing.

When I use the Vol control, only right channel reacts, which is the one not playing on startup.

I saved according to your guide.
Rebooted system...
No sound in right channel...

Maybe I try to see if a new driver is available tomorrow, and use your guide to install new driver.

---

### Post by LordRaiden on 2006-07-04
How many soundcards do you have? I'm assuming 1 but I am not all familiar with your card.

---

### Post by BuffaloX on 2006-07-04
I have only one soundcard.
Onboard is disabled, and no driver is present for that, so that should be OK.
Also I checked that my driver was the correct one.
It is ICE1724 Which should work for M-Audio Revolution 7.1 and other cards with same sound chip Envy24HT.

---

### Post by LordRaiden on 2006-07-05
Your module is snd-ice1724.


[http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix]("http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-MAudio#matrix")

---

### Post by BuffaloX on 2006-07-05
Thanx, it is the driver I'm using, but I can't see any version number?

How can I see the driver version?
No need to install, if the driver is same version I guess.

---

### Post by LordRaiden on 2006-07-05
cat /proc/asound/version I think

---

### Post by BuffaloX on 2006-07-05
Yes that shows me this:

Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).

So it's relatively new, and rc3 sounds OK.
Maybe it's not a driver problem.

But the volume applet, seems to misinterpret something, since it only works on right channel, and it's the channel that the volume applet works on that is muted on startup. Can I configure that, or maybe I should just uninstall it?

---

### Post by LordRaiden on 2006-07-05
If the volume applet is giving you trouble, then try using alsamixer and not the applet.  Save the settings to what you like then use the alsactl method.  Avoid using the sound applet for now (maybe disable it). If that does not solve your problem, then it could actually be a driver setting/problem.

---

### Post by BuffaloX on 2006-07-05
I used the terminal alsamixer, and saved the settings.
Using your guide.
Still only sound in left channel.
I tried saving with other settings, just to see if the saving worked.
The settings are saved, and restored on next boot, it's just that right channel is "muted", until i make an adjustment to it, then it comes through clear as a bell.
On my soundcard all channels can be muted seperately.

---

### Post by LordRaiden on 2006-07-05
So even by unmuting the right channel in alsamixer then using alsactl to store the settings, the right channel still shows up muted on boot?

That is definitely a bug of some kind. The settings should be saved. Go to [https://bugtrack.alsa-project.org]("https://bugtrack.alsa-project.org") and file a bug on it. Put down the full name of your sound card along with the module name snd-ice1724. Someone slightly more knowledgeable will other guide you better (maybe a more nitty gritty setting that I don't know about) or agree with me that its a bug and make a patch.

---

### Post by BuffaloX on 2006-07-05
OK Thanx very much anyway.

Luckily it's not a bad error, and I'm very optimistic about having GREAT sound in Ubuntu. ( you should see what my whife can do with jack )
Thats actually what got us started with Linux/Ubuntu in the first place. :p 

If nescessary I might just enable the onboard sound.

---

