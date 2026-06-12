---
title: "Alsa problems with Dell (no Sound output at headphone jack)"
date: 2010-11-04
forum: Multimedia Software
---

### Post by Tand on 2010-11-04
[COLOR=#000000][SIZE=2]Hello,
I bought a new laptop (dell Precision M4500) and installed Ubuntu on it. But as mentioned above I can't get the sound to work properly.
In the german Wiki ([http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no](http://wiki.ubuntuusers.de/Soundkarten_konfigurieren/HDA?redirect=no)) it says to look up my codec in ALSA-Configuration.txt or HD-Audio-Models.txt but I can't find it there.
I have tried different entries ([/SIZE][/COLOR]snd-hda-intel model=xxx)[COLOR=#000000][SIZE=2] for various dell laptops in the alsa-base.conf but none of them seem to work.

[/SIZE][/COLOR]cat /proc/asound/cards ```


[COLOR=#000000][SIZE=2]0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xe9660000 irq 48
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xe3080000 irq 16

[/SIZE][/COLOR]
```head -n 1 /proc/asound/card0/codec* 
```
[B][COLOR=#000000][SIZE=2]
[/SIZE][/COLOR][/B][COLOR=#000000][SIZE=2]
Codec: IDT 92HD81B1C5[/SIZE][/COLOR]
```It would be really nice if somebody could help me with this because I don't know what else to try and I can't use Ubuntu like this.

---

### Post by Tand on 2010-11-05
/sbin/alsa reload responds with
```

/sbin/alsa: Warning: Processes using sound devices: 1808(pulseaudio). 
mkdir: kann Verzeichnis „/var/run/alsa“ nicht anlegen: Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-hda-codec-nvhdmi snd-hda-codec-idt snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
mkdir: kann Verzeichnis „/var/run/alsa“ nicht anlegen: Permission denied
Loading ALSA sound driver modules: (none to reload).
```

---

