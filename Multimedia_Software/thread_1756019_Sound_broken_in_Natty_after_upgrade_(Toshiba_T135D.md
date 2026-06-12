---
title: "Sound broken in Natty after upgrade (Toshiba T135D)"
date: 2011-05-11
forum: Multimedia Software
---

### Post by clanmackay on 2011-05-11
In Maverick, I had sound working through a USB sound card and through my laptop internal speakers.  The built-in headphone jack did not work.  After upgrade to Natty, only the internal speakers work, so I have no way of playing through external speakers or headphones.

My ALSA debug output is here: [http://www.alsa-project.org/db/?f=9b1ee4ce380be0e100aa9ee32560219df7211323]("http://www.alsa-project.org/db/?f=9b1ee4ce380be0e100aa9ee32560219df7211323")

I have been using pavucontrol for mixing and output selection, and nothing is muted.

Sound works through internal speakers, built-in analog output, and USB sound card in Windows, so there is no hardware problem.

Getting *either* working would be fine.  I may be failing to understand fundamental things.  Can anyone help?

Thanks!

---

### Post by lidex on 2011-05-11
I see you have a /etc/asound.conf file - what is that for?

Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=olpc-xo-1_5" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by clanmackay on 2011-05-11
> **lidex said:**
> 
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=olpc-xo-1_5" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

Thank you.  That got the built-in headphones jack working.  Brilliant.  I'm marking as solved, but if someone wants to add the USB audio fix (for posterity) please feel free.

[SIZE="1"]> **lidex said:**
> I see you have a /etc/asound.conf file - what is that for?

I have no idea.[/SIZE]

---

### Post by lidex on 2011-05-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by clanmackay on 2011-05-12
> **lidex said:**
> Use the alsa-info-script to provide detailed information.

"Again", you mean, now that I've made your change?  I gave a link, of course, in my original question.

---

### Post by lidex on 2011-05-12
> **clanmackay said:**
> "Again", you mean, now that I've made your change?  I gave a link, of course, in my original question.

I wanted to see if any changes but now I don't think it matters.
Looks like your mixer levels are down for the usb device:
```
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 38
  Mono:
  Front Left: [COLOR="Red"]Playback 0 [0%][/COLOR] [-28.37dB] [on]
  Front Right: [COLOR="Red"]Playback 0 [0%][/COLOR] [-28.37dB] [on]
```

---

