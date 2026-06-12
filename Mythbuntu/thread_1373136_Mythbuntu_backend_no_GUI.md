---
title: "Mythbuntu backend no GUI?"
date: 2010-01-05
forum: Mythbuntu
---

### Post by derelict888 on 2010-01-05
I already have a file server (Ubuntu 8.04 or 9.04 idr) that I want to add Mythbuntu backend to. My file server has no GUI and I'd prefer to keep it that way, but I don't know if Mythbackend requires a GUI or not. All the instructions I've seen for Mythbuntu make use of GDM. Can anyone help me out?

Also I just installed a cheap capture card I found on craigslist since I believe the backend requires a capture card. Here is what I see for the capture card;
```
root@media-server:~# dmesg | grep bttv
[   37.988707] bttv: driver version 0.9.17 loaded
[   37.988712] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   37.988784] bttv: Bt8xx card found (0).
[   37.988808] bttv0: Bt878 (rev 2) at 0000:05:00.0, irq: 16, latency: 16, mmio: 0xfd8ff000
[   37.996680] bttv0: detected: AVerMedia TVPhone98 [card=41], PCI subsystem ID is 1461:0001
[   37.996685] bttv0: using: AVerMedia TVPhone 98 [card=41,autodetected]
[   37.996713] bttv0: gpio: en=00000000, out=00000000 in=000477c3 [init]
[   38.029088] bttv0: Avermedia eeprom[0x4801]: tuner=2 radio:yes remote control:yes
[   38.029095] bttv0: tuner type=2
[   38.029099] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   38.029813] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.030435] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   38.488128] bttv0: registered device video0
[   38.488152] bttv0: registered device vbi0
[   38.488173] bttv0: registered device radio0
[   38.488197] bttv0: PLL: 28636363 => 35468950 .. ok
[   38.526406] input: bttv IR (card=41) as /devices/pci0000:00/0000:00:1e.0/0000:05:00.0/input/input5

```
To me that looks correct, but I'm not sure.

Any help is appreciated. I tried finding a guide or howto on doing a mythbackend with no GUI but found nothing. I'd prefer sticking with Mythbuntu but don't have to. Thanks

---

### Post by azmyth on 2010-01-05
No GUI for backend (BE). The GUI that connects to the BE is the frontend.

---

### Post by klc5555 on 2010-01-05
> **azmyth said:**
> No GUI for backend (BE). The GUI that connects to the BE is the frontend.

Still need a GUI to set up the backend (mythtv-setup). Might be able to do this from a remote machine with ssh -Y  All the dependent X libs, etc., would still be necessary, I think, GUI or not.

I've never tried to do anything quite like this, but it sounds like fun. The place to start would likely be to apt-get install the mythtv-common, mythtv-database, and mythtv-backend packages (and whatever dependencies they drag along with them) onto the server.

Then ssh -Y into the machine from somewhere and see if running (sudo) mythtv-setup is possible.

The remote frontend will eventually need mythtv-common and mythtv-frontend (plus dependent detritus), but only after the backend is actually up and running.

---

### Post by ian dobson on 2010-01-05
Hi,

The backend doesn't need x running for normal use. You only need X windows for running Myth-setup which you can run over a network connection.

Thats the way I run my backend, I use cgiwin/startX on my windows box to start an X-Window capable network session that I then use to start Myth-setup. It's not that quick but it's enough for what you need to do to setup mythTV.

Regards
Ian Dobson

---

### Post by derelict888 on 2010-01-05
Alright broke down and installed ubuntu-desktop, going to see if I can do everything I need using ssh -Y, otherwise I guess I'll setup remote desktop. Thanks for the help.

---

