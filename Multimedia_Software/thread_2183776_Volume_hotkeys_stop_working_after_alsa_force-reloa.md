---
title: "Volume hotkeys stop working after alsa force-reload"
date: 2013-10-26
forum: Multimedia Software
---

### Post by adityap174 on 2013-10-26
I recently upgraded my Xubuntu to 13.10 . My bluetooth headset used to work properly before the upgrade. After the upgrade, even after getting connected using the blueman applet as headset service, pulseaudio fails to recognize my device. 

I had to issue the commands :

```
pulseaudio -k
sudo alsa force-reload

```

to make the headset appear in the pavucontrol configuration tab. The problem which i face now is that after the pulseaudio daemon is restarted, my volume hotkeys on the keyboard stop functioning. :(

I even tried to bind them using keyboard shortcuts to the commands :
```

amixer set Master 4%- -q unmute
amixer set Master 4%+ -q unmute

```

But even this fails. These commands work properly when bound with any other key combination like <Ctrl><Shift><Up> etc., but not with volume hotkeys.

Can anyone please explain me how the volume hotkeys are bound to the pulseaudio daemon and how their functionality can be restored after restarting the daemon ? Of coarse it would be even better if someone can get help me get alsa to recognize new devices without force-reload. Any help will be appreciated. 

Is there any alternative to pulseaudio which can connect the input stream to the bluetooth headset ? I tried jack and xfce4-mixer but they weren't that helpful.

---

### Post by adityap174 on 2013-10-26
I also tried adding :

```

pcm.bluetooth {
    type bluetooth
    device "XX:XX:XX:XX:XX:XX"
    profile "auto"
}
```

to a file .asoundrc in my home directory but even that doesn't make any difference.

---

### Post by adityap174 on 2013-11-22
Okay I found the problem. 
Using command 
```
pactl list | grep -i module-bluetooth-discover
```
I found out that the bluetooth discover module was not loaded. 

But my default.pa file in /etc/pulse contains the lines 

```
.ifexists module-bluetooth-discover.so
load-module module-bluetooth-discover
.endif

```

So why does the module not load on pulseaudio startup ?

After issuing the command 
```
sudo pactl load-module module-bluetooth-discove
```

The bluetooth headset works properly and is detected automatically, without killing and restarting alsa.

---

