---
title: "Sound Driver keeps switching on boot"
date: 2006-12-09
forum: Multimedia &amp; Video
---

### Post by Jose Catre-Vandis on 2006-12-09
This is on an uptodate Dapper.

Alsa is set as the main sound driver system

Every now and then, perhaps on every 1 in ten boots, alsa goes for a walk, and i have to switch to oss to get sound (xmms), then switch back to alsa (xmms) and then reboot to get alsa back (which is needed for mplayer too)

Anyway to stop this happening?

---

### Post by Luciano on 2006-12-09
I had the same problem and i've tried the "howto configure your sound card correctly" in the big Ubuntu Guide: [http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME]("http://ubuntuguide.org/wiki/Dapper#How_to_configure_sound_to_work_properly_in_GNOME")

But this didn't change much for me. I have just tried the following and it seemed to work...:confused: 

Find availiable Cards: 
```
 sudo asoundconf list
```

I had 'Camera' & 'Intel' in the list.

Next I set the default card, obviously change "Intel" to your default card:
```
sudo asoundconf set-default-card Intel
```

You can restart alsa with:
```
sudo /etc/init.d/alsa-utils restart
```

I still had to change the applications to the correct card(Intel)so a reboot of the machine is probably best.

Hope that helps! :)

---

### Post by Jose Catre-Vandis on 2006-12-09
Thanks, will give it a try. will probably have to post back in two or three weeks to see if it works!

---

### Post by Luciano on 2006-12-10
Just to let you know that my sound card driver still switches randomly so the above doesn't work, sorry :)

But i have found the following site:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem]("http://ubuntuforums.org/showthread.php?t=205449&highlight=2+sound+card+ubuntu+problem")
From this i picked out the following steps:

1. Find the Drivers used:
```
cat /proc/asound/modules
```
Ouput:
```
0 snd_usb_audio
1 snd_hda_intel
```

2. Edit file /etc/modprobe.d/alsa-base:
```
sudo gedit /etc/modprobe.d/alsa-base
```

3. Add the folowing at the bottom of the file:
```
#My Mod - Set Default sound card
options snd_usb_audio index=1
options snd_hda_intel index=0
```

Good Luck!

---

### Post by Jose Catre-Vandis on 2006-12-10
Good find my friend.

This is my cat output

```
0 snd_intel8x0
1 saa7134_alsa
```

and this is what my edited alsa-base file looks like at the bottom:

```
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd_intel8x0 index=0
options saa7134_alsa index=1
```

On reboot I have sound :) , now time will tell :)

FWIW the intel is the onboard sound, the saa7134 is on my TV card.

---

### Post by Luciano on 2006-12-19
Well its been a long time since doing the above fix and i haven't had anymore problems :D

Swish! ;)

---

