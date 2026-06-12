---
title: "Realtek AC 97"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by Wilku on 2006-09-25
I am a new linux user. I installed ubuntu dapper drake and my sound was working, but it could run only one sound at a time. So I thought it is a driver problem, so I downloaded a driver for Realtek AC'97 and installed it. When I rebooted my computer the sound was gone. My friend explained me that 'the one sound at a time' problem was because of a mixer, but you know, because of the driver I have no sound at all. When I try to run volume control I get a pop-up that I have no sound regulation devices. So what can I do, is there a way to make ubuntu detect the device by itself and configure one more? I will be grateful for any help.

---

### Post by daschl on 2006-09-25
so at first you have to get your old settings back so that you have any sound at all. you can do this with re-installing alsa and its settings (you may use synaptic for these actions if you don't want to use the console)

when your sound is up again, play around with the "alsamixer"-tool and try to disable the gnome sound server..

---

### Post by Wilku on 2006-09-25
> **daschl said:**
> so at first you have to get your old settings back so that you have any sound at all. you can do this with re-installing alsa and its settings (you may use synaptic for these actions if you don't want to use the console)

when your sound is up again, play around with the "alsamixer"-tool and try to disable the gnome sound server..

Well I did what you said and I even tried to find my sound card by using alsactl. it doesn't detect any sound card and I have no idea why...

---

