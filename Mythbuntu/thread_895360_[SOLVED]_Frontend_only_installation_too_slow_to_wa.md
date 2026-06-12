---
title: "[SOLVED] Frontend only installation too slow to watch live tv from backend ?"
date: 2008-08-20
forum: Mythbuntu
---

### Post by Eldis on 2008-08-20
I have 1 frontend+backend installation with several tuners in the living room and a laptop with just frontend installed for watching stuff in the bedroom.

Problem is apparently my network connection is way too slow to watch tv from the frontend only machine or even recordings or videos. Avi files almost work but I can feel it struggling to keep up with the watching speed.

Backend is connected to my ADSL\router with usb wlan card:
```
Bus 003 Device 004: ID 0ace:1215 ZyDAS WLA-54L WiFi
```

Frontend has an internal wlan adapter that seems to work.

Question is why is the connection so slow ?

When I download stuff from let's say ubuntu repositories I get my full rate 800-900 KB/s but on my internal wlan network the connection speeds are really terrible arround 100-130 KB/s

Any way I could troubleshoot this a bit further to verify my lan speends and maybe ideas of what could be the root cause ?

Connections over samba shares also seem terrible but I haven't verified this yet since I lack the tools to do so.

Edit: B = bytes, b = bits

---

### Post by Eldis on 2008-08-20
I've tested downloading a file from my mythbuntu machine from my frontend using sftp and gotabout 1000 KB/s. That should be enough to watch recordings and live tv ?

I think somehow when I use the frontend to watch stuff from the remote backend the speeds have to be much slower for some reason. Any tool I could use to monitor network speed while trying to watch a recording for example ?

---

### Post by dannyboy79 on 2008-08-20
i can tell you that I tried the whole wireless thing, Wireless G at that, and it the video would still be buffering and pausing on the extra frontend I was trying to watch the video on. I am not sure why you get such good speeds when downloading from ubuntu repos but maybe it has something to do with DNS. do you use a wins server or dns server or do you use a hosts file? how fast are your pings to say goggle compared to your pings to your backend?

---

### Post by dannyboy79 on 2008-08-20
deleted

---

### Post by dannyboy79 on 2008-08-20
iftop will show you speeds betweeen connections. I use it all the time. first

sudo aptitude update

sudo aptitude install iftop

sudo iftop -i eth0

NOTE: eth0 needs to be whatever interface you want to monitor. Yours may be wlan0 or something similar depending on your wlan card in your laptop. You can lauch iftop in a terminal on the backend.

---

### Post by newlinux on 2008-08-20
What types of streams are you watching (HD, SD, mpeg-2 recordings, what types of AVI files, etc.) Do you mean 1000kbps (bits per second) or 1000KBps (bytes per second)? Both are slow for wireless G, and 1000kbps wouldn't be fast enough for most standard definition mpeg-2 encoded video (4-8Mbps), but 1000KBps (~7.8Mbps) should do if it is a consistent connection.

With my Wireless G connection I can watch SD video just fine, but HD sometimes struggles as I usually get 15-20Mbps from my wireless, and 20 is about what I need for reliable HD (mpeg-2).

---

### Post by volkswagner on 2008-08-20
This thread may offer some help to reduce the bandwidth and tools to monitor.

[http://ubuntuforums.org/showthread.php?t=851380]("http://ubuntuforums.org/showthread.php?t=851380")

---

### Post by Eldis on 2008-08-21
Thanks for so many replies, sorry I usually give network speeds the wrong way arround. So my frontends wlan is recognized as a 11b card at the moment and fails to go up to 11g so I have 10Mbps and my transfer speed using sftp to my backend is 1000 KBps ~ 8Mbps which is surprisingly good in fact it's too good dunno whats up with that. 

I can't watch SD MPEG2 streams at all because of constant buffering but a avi or xvid 40-60min video in 350MB is watchable but I can see it pausing once in a while to buffer. The SD MPEG2 streams are buffering and skipping constantly so no way to watch them. I don't watch or record in HD because my hardware is not up for the task also we don't have any free HD streams to record here on cable, one experimental one but I don't have it tuned atm.

I will try the networking tools mentioned here tonight when I get home.

---

### Post by Archmage on 2008-08-21
> **Eldis said:**
> I can't watch SD MPEG2 streams at all because of constant buffering but a avi or xvid 40-60min video in 350MB is watchable but I can see it pausing once in a while to buffer.

To avoid this, you could enter a buffer. I'm doing this with my videos, where I did use mplayer to play them. There I did enter the cache-option in the config to avoid any pausing. (Or better it will pause at the start to buffer and than run smothy.)

If someone had an option to fill the buffer of mplayer automatical when I'm pausing (so that it don't need to buffer at the start) or how to buffer the internal player of MythTV I would be greatful.

---

### Post by newlinux on 2008-08-21
> **Eldis said:**
> Thanks for so many replies, sorry I usually give network speeds the wrong way arround. So my frontends wlan is recognized as a 11b card at the moment and fails to go up to 11g so I have 10Mbps and my transfer speed using sftp to my backend is 1000 KBps ~ 8Mbps which is surprisingly good in fact it's too good dunno whats up with that. 

I can't watch SD MPEG2 streams at all because of constant buffering but a avi or xvid 40-60min video in 350MB is watchable but I can see it pausing once in a while to buffer. The SD MPEG2 streams are buffering and skipping constantly so no way to watch them. I don't watch or record in HD because my hardware is not up for the task also we don't have any free HD streams to record here on cable, one experimental one but I don't have it tuned atm.

I will try the networking tools mentioned here tonight when I get home.

Wireless B is probably going to be problematic. Even though you can get ~8Mbps the problem is that often wireless B can't maintain a *consistent* high enough transfer rate which video needs, but other types of transfers don't. For mythvideo, this can be helped by using the -cache option with mplayer as mentioned, but for using the internal player I'm not sure what you can do.

---

### Post by Eldis on 2008-08-21
Alright figured it out, thanks for all the help here :). So I took a usb wlan stick and hooked it up and tried again and everything worked fine. The usb wlan worked in 11g mode so that extra speed did the trick. Now I just need to figure out how to get the onboard wlan to go into g mode. Hopefully I can figure it out.

My backend was also in the wrong mode but now that both are using 11g it works.


So for anyone else who gets into trouble with this good signal quality g is enough to watch SD live tv, a and b aren't most likely n will be needed for watching HD.

---

### Post by Eldis on 2008-08-21
I thought I could report I also managed to get my internal wlan card working in g mode and everything works really nicely :).

I  removed ndiswrapper and tried one more time with the original p54common and p54pci modules.

Still not sure if the rate and mode will survive the boot but crossing my fingers and hoping for the best.

---

