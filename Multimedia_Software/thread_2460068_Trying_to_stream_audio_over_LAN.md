---
title: "Trying to stream audio over LAN"
date: 2021-04-01
forum: Multimedia Software
---

### Post by jessica43928 on 2021-04-01
I'm trying to stream audio from my desktop to a raspberry pi over my LAN wifi using pulseaudio.  The only thing that has worked at all is to use the paprefs on the server, and select multicast RTP, which then I can select on the PI under playback devices.  However, the audio only comes through in bursts, like every couple of seconds or so, I get a blast of staticy sound that, after a few minutes, I start to recognize is indeed the music that I have playing on the server.  Any suggestions as to why it's not playing smoothly?  I have tried streaming to both a PI 3 and a Pi Zero W, and I get the same result both times, so I think the problem is probably with the server setup?

---

### Post by ajgreeny on 2021-04-01
I can't help with streaming audio over pulseaudio (I didn't even realise it was a possibility) but I do use minidlna which will stream media files very easily and effectively.

Try that and I suspect you may find it is simple and will stream not only to a dlna client on the Pi vlc perhaps, but to other clients as well, eg, smartTV if you use such things in your home.

---

### Post by yetimon_64 on 2021-04-02
> **jessica43928 said:**
> I'm trying to stream audio from my desktop to a raspberry pi over my LAN wifi using pulseaudio.  The only thing that has worked at all is to use the paprefs on the server, and select multicast RTP, which then I can select on the PI under playback devices.  However, the audio only comes through in bursts, like every couple of seconds or so, I get a blast of staticy sound that, after a few minutes, I start to recognize is indeed the music that I have playing on the server.  Any suggestions as to why it's not playing smoothly?  I have tried streaming to both a PI 3 and a Pi Zero W, and I get the same result both times, so I think the problem is probably with the server setup?
I have done exactly that but over a wired LAN network; streaming audio over RTP with pulseaudio. I had good results on pi 3b+ and pi 4b units; no pausing at all. My slowest pi unit, LAN wise, is a pi 3b (2016 hardware release, 100 Mb/s connection), it worked but performance was occasionally a bit patchy but with only occasional audio pauses. Nowhere near as bad as what you are reporting though.

Wifi speeds are generally much slower than a wired ethernet network.  I suspect your issues are related to using older pi models and combining that with wifi usage. Even on the older units, particularly the pi 3b, it would be worth trying a wired ethernet LAN set up. I've never owned or tried a pi zero but from what I've read it doesn't have an ethernet port but can get connected to a wired LAN with a USB to ethernet adapter.

To my reading of your opening post it sounds as if the server is working, or trying to work, but being on a slow wifi network on older pi units is causing issues. Pi hardware can often be a bit under-powered/slow for some tasks, particularly with the older models.

My hardware and network setup was streaming from a HP "Envy 17" laptop to a wired LAN through an 8 port (originally a 5 port) network switch (1Gb/s full duplex capability for both switches) to three pi 3 units (1 pi 3b and 2 pi 3b+) and 2 pi 4b units. All worked flawlessly but for the slower pi 3b (100 Mb/s LAN) unit which had only very occasional pausing (still good enough to use). From my experience with file transfers over pi wifi connections I wouldn't even consider streaming pulseaudio audio, far too slow for my liking.

If you don't want to set up or test a wired network and want to stay on wifi I'd suggest you give ajgreeny's advice, of using a minidlna server, a try out. It may possibly perform a bit better than pulseaudio and RTP streaming on your network.

Regards, yeti.

---

