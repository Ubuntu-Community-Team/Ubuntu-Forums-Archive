---
title: "pulseaudio: split 5.1 into hdmi and spdif"
date: 2018-06-29
forum: Multimedia Software
---

### Post by martin30002 on 2018-06-29
[COLOR=#111111][FONT=Ubuntu]I'm using ubuntu on an Intel NUC and a monitor for watching TV, and a dolby 5.1 receiver for the sound, connected via spdif. Pulseaudio runs with module a52 in dolby 5.1 mode (so the receiver is always in 5.1 mode). This works fine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Now I wanted to reconfigure the system and send the center channel via hdmi to the speakers in the monitor. The other 4.1 channels should go thru SPDIF to the receiver.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In [https://wiki.archlinux.org/index.php/PulseAudio/Examples](https://wiki.archlinux.org/index.php/PulseAudio/Examples) there are quite good examples. I think I have to use module-combine-sink and module-remap-sink.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Do I first have to use module-combine-sink and then remap it?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/) does not clarify this.[/FONT][/COLOR]

---

