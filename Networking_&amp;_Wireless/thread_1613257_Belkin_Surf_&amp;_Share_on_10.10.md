---
title: "Belkin Surf &amp; Share on 10.10"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by dforthman on 2010-11-04
I've read every post I could come across about getting the Surf & Share wireless adapter working, but no luck.

It worked in 10.04 using ndiswrapper, but the connection was very weak (In Windows, it works perfectly). I blame ndiswrapper and the windows driver for the connection issues.

In 10.10 x64, using ndiswrapper does not work. It says hardware present, but iwconfig shows no wlan0 adapter. I downloaded the driver from RealTek's website (rtl8192su) and compiled it. It gave a lot of warnings about integers being out of range, but I ignored them and went on anyway. If you want the exact warnings, I can put them on a pastebin and post the link tonight when I get home from work.

After doing a make install, I plugged in my adapter. As soon as it kicked on, the light on the adapter would blink and the screen would go black with a lone cursor in the top left corner of the screen. The drivers are obviously suspect, since I can make uninstall, plug in the adapter, and continue on with no network.

Has anyone gotten this adapter/other adapters with the rtl8192su firmware working in 10.10 using a stock x64 install? It has to be stock or using packages available on the disk since without using the adapter, I have no internet.

Maybe I'll try the drivers on 10.04 and see if they're just not compatible with 10.10.

---

### Post by dforthman on 2010-11-04
Update:
Installed 32-bit 10.10, compiled same drivers (on a windows partition), and it works.

just:
cd /path/to/drivers
sudo su
make
make install
exit

So I'll call this done.

---

