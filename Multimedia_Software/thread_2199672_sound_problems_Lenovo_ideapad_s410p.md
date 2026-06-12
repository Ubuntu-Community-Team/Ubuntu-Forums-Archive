---
title: "sound problems Lenovo ideapad s410p"
date: 2014-01-15
forum: Multimedia Software
---

### Post by jav.cuesta on 2014-01-15
Hi all,
I bought a new **Lenovo ideapad S410p** with windows8. I erased windows8 and made a new partition table where I installed Ubuntu 12.04lts. Everything is working except the sound. 
I've installed GNOME ALSA MIXER where I can see **Intel Haswel HDMI (IEC958) and Realtek ID 233**. I have typed 
***sudo nano /etc/modprobe.d/alsa-base*** and change the document (which for me is actually empty!) by typing
***options snd-hda-intel model=lenovo ***but after rebooting it does still not work. 
I tried also ***options snd-hda-intel model=ideapad*,** and** *options snd-hda-intel model=generic***.

Then I have used the following script to update ALSA with no luck [http://www.stchman.com/alsa_update.html](http://www.stchman.com/alsa_update.html).

I'd really appreciate your help! 
[COLOR=#333333][FONT=monospace]

[/FONT][/COLOR]

---

### Post by trivietnam on 2014-07-07
i also have s410p
i do not upgrade alsa, just select the 2nd sound card as the default one:

~/.asoundrc

```

## The default, digital card (HDMI, Intel) does not work
## So, I chose the secondary, analogue card PCH (Realtek ALC233)
## http://alsa.opensrc.org/MultipleCards
## https://wiki.archlinux.org/index.php/Allow_multiple_programs_to_play_sound_at_once
## Run "aplay -l" to see the list

defaults.pcm.card 1
defaults.ctl.card 1

```

---

