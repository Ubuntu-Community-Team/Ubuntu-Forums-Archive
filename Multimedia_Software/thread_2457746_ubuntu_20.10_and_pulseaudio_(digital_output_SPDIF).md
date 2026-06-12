---
title: "ubuntu 20.10 and pulseaudio (digital output S/PDIF)"
date: 2021-02-08
forum: Multimedia Software
---

### Post by alain.roger on 2021-02-08
Hi,

i have since few days a weird behavior with audio. When i boot computer it automatically select "Digital Output (S/PDIF)" as default audio output. And i have no sound.
Till now it used analog audio and it worked great 6 years.

To for it to analog audio i must type in terminal:
```
pulseaudio -k
```

I thought that i could set default input/output in conf file '[COLOR=#242729][FONT=Arial]/etc/pulse/default.pa' by adding following 2 lines (but it does not work):
```
[/FONT][/COLOR][FONT=monospace][COLOR=#000000]### Make some devices default[/COLOR]
set-default-sink 'alsa_output.pci-0000_00_1b.0.analog-stereo'
set-default-source 'alsa_input.usb-041e_Live__Cam_Connect_HD_1080_VF0760-02.analog-stereo'[/FONT][COLOR=#242729][FONT=Arial]
```

What should be the other possibilities ? To modify '[/FONT][/COLOR][COLOR=#242729][FONT=Arial] [/FONT][/COLOR]**/etc/pulse/client.conf**[COLOR=#242729][FONT=Arial] ' file ?
thx[/FONT][/COLOR]

---

### Post by alain.roger on 2021-02-09
[COLOR=#242729][FONT=Arial]
Modify [/FONT][/COLOR]**/etc/pulse/client.conf**' file didn't help.

any idea ?

---

### Post by alain.roger on 2021-02-11
Today i removed folder /home/alain/.config/pulse typing: rm -rf /home/alain/.config/pulse and type again: pulseaudio -k
however, it did not help.

Problem still persists

---

### Post by alain.roger on 2021-02-16
The only walkaround i found till now, it's to add a session start command line (script) to run pulseaudio -k, once i logged in plasma

---

