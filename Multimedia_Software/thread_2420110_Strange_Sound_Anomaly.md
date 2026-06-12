---
title: "Strange Sound Anomaly"
date: 2019-05-30
forum: Multimedia Software
---

### Post by speartip on 2019-05-30
Xubuntu 18.04 HWE Fully updated.
This is something that I've only just noticed, so may well be a recent update.
When playing Aisleriot Solitaire, (sad I know) but I enjoy the game sounds. (Popping as cards are moved, Clapping at the end etc...)
But now the sounds only play, when I play music through either Rhythmbox, VLC or other media players. The minute I close the media player the sounds stop in Aisleriot as well.
Could someone please check if it's the same for them, or any other suggestions?

---

### Post by Autodave on 2019-05-30
Xubuntu 18.04 here.  Just tried Solitaire and there are no sounds.  In fact, I don't ever remember there being sound on the game and I have been using it for about 10 years now.

Tried with VLC open, no sound.

---

### Post by speartip on 2019-05-30
Hi Autodave. Do you have "sound" ticked under control in the menubar?
I have always had sound until recently, & I have also tried on Linux Mint XFCE, & the sound works perfectly there, which is strange as it's based on Xubuntu 18.04.

---

### Post by Autodave on 2019-05-30
I am on Xubuntu 18.04 and there is nowhere to tick or untick for the sound.  

Just checked wifey's machine: Xubuntu 16.04 and there is no sound there or place to turn it on or off.  Is Ubuntu different than Xubuntu?

---

### Post by Autodave on 2019-05-30
Checked a Xubuntu 14.04 machine: same thing.

---

### Post by speartip on 2019-05-30
> **Autodave said:**
> I am on Xubuntu 18.04 and there is nowhere to tick or untick for the sound.  

Just checked wifey's machine: Xubuntu 16.04 and there is no sound there or place to turn it on or off.  Is Ubuntu different than Xubuntu?

How weird. I've always been able to get sound. As you can see per Screenshot:
[ATTACH=CONFIG]283341[/ATTACH]
It's only recently though that it only works, when I'm playing a media player.

---

### Post by Autodave on 2019-05-30
Just checked all 3 machines again: none of them have that option under Control.

---

### Post by speartip on 2019-05-31
> **Autodave said:**
> Just checked all 3 machines again: none of them have that option under Control.

How odd. Maybe it's hardware specific. Anyway still got the original problem in Xubuntu 18.04, but not in Mint XFCE 19.1.

---

### Post by echotech2 on 2019-05-31
Ubuntu 18.04.02 - I have a "Sound" selection on the "Control" menu.  Checking is there is no sound.

---

### Post by speartip on 2019-05-31
Hi echotech2.
Try playing some Music through a media player, while playing Aisleriot. See if you now have sound as I do.

---

### Post by echotech2 on 2019-06-01
I either don't have any Solitaire sound using SMPlayer+MP3 or it's too low to hear.

---

### Post by Yellow Pasque on 2019-06-01
> **Autodave said:**
> I am on Xubuntu 18.04 and there is nowhere to tick or untick for the sound.

Do you have event sounds enabled on your system(s)? If you don't, the Sound option won't appear in Aisleriot:
xfce has it in a strange place: Settings -> Appearance -> Settings tab

---

### Post by Autodave on 2019-06-01
I did not have it enabled.....didn't even know it was there!  Thanks!  I now have sound on Aisleriot.  However, it is *extremely* soft....sound is cranked up to about 80% just to hear something.

---

### Post by speartip on 2019-06-02
> **Autodave said:**
> I did not have it enabled.....didn't even know it was there!  Thanks!  I now have sound on Aisleriot.  However, it is *extremely* soft....sound is cranked up to about 80% just to hear something.

Ok. So now try playing some Music on a media player, while playing Aisleriot. Are the game sounds now significantly increased & audible?

---

### Post by Autodave on 2019-06-02
Just tried it with VLC open, but no difference in sound level.

---

### Post by speartip on 2019-11-03
I know that this is 5 months late, but I have just today solved this issue.
It is the package, libcanberra-pulse, that needs installing to allow system sounds.

---

### Post by Yellow Pasque on 2019-11-03
> **speartip said:**
> I know that this is 5 months late, but I have just today solved this issue.
It is the package, libcanberra-pulse, that needs installing to allow system sounds.

It really should work with libcanberra's alsa/asound backend, because pulseaudio has a wrapper to make that work (and it did work when you had other programs running.) It seems like a bug to me, which could be further investigated. On the other hand, now that Xubuntu is committed to pulseaudio, they probably should include libcanberra-pulse in the ISO to eliminate an unnecessary API wrapper when using libcanberra.

---

### Post by called2voyage on 2020-09-11
Thanks for sharing this even though it was months late! I'm on Ubuntu 18.04 LTS, and for me it was just the click.ogg sound that stopped working for some reason. But it was still fixed by installing libcanberra-pulse.

---

