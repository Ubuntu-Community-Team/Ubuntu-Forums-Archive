---
title: "Volume too low on Ubuntu 17.10"
date: 2018-03-01
forum: Multimedia Software
---

### Post by overflow404 on 2018-03-01
[COLOR=#111111][FONT=Ubuntu]I've a 2.1 sound system and on a Windows pc it works very well. On Ubuntu 17.10(but also in Kubuntu 16.04) the volume is lower than Windows also at 100%. I've already tryed looking alsamixer and it's ok, all at 100%, if I increase max volume over 100% it's sounds very bad. I've also tryed to reinstall alsamixer and pulseaudio but nothing to do.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the output of:
```
[FONT=Consolas]cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; ls -l /usr/share/pulseaudio/alsa-mixer/paths/; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd; find /lib/modules/`uname -r` | grep snd ;cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound[/FONT]
```

Output:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://text-share.com/view/f388c12d](https://text-share.com/view/f388c12d)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What can I do?[/FONT][/COLOR]

---

### Post by Autodave on 2018-03-01
Did you check inputs and outputs?  Have you installed *pavucontrol*?

---

