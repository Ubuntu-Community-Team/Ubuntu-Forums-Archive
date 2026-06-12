---
title: "Avermedia Avertv usb 2.0 kubuntu driver"
date: 2006-01-18
forum: Multimedia &amp; Video
---

### Post by abbaskaz on 2006-01-18
I have bought a "Avermedia Avertv usb 2.0" TV card 3 days ago . I could'nt manage to use it on [SIZE="4"]kubuntu [/SIZE].  I searched all the web sources  as I can  .
Anyone who can solve this problem  please help me ...
thank you ......

:razz: :razz: :razz:

---

### Post by FarEast on 2006-01-21
Hi;) ,

I have never tried TV cards...
Anyway, please paste the output from the command below.

$ cat /proc/bus/usb/devices

If there is information of the chip on the card, it will be an
important clue.

regards

---

### Post by tioneb on 2006-06-20
go to linuxtv.org
dowload the firmware for avermedia and place it in /lib/firmware/
plug the usb box
check it with 'dmesg'
download dvb-utils (synaptic)
learn how to scan on tvlinux
scan your channels
mplayer dvb://CHANNELNAME
I'v seen that kafeine could do it but I use mplayer

for the remote controller I'm on ....

---

### Post by Ellarco on 2006-07-01
I have a piece of crap "AVerMedia AVerTV USB 2.0 Plus" which I have been trying to get going on my office Kubuntu (Breezy), that I might catch the World Cup. kdetv and xawtv fail to detect it.

I followed your instructions up to the "learn how to scan on tvlinux" step, then I got confused. Im trying to pick up a terrestrial signal (RTE, Ireland) with a little aerial ... do your steps apply?

Anyone able to help? Quarter Finals are upon us ...

```

$  cat /proc/bus/usb/devices
[snip]
T:  Bus=04 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=07ca ProdID=0036 Rev= 0.01
S:  Manufacturer=AVerMedia
S:  Product=AVerTV USB 2.0 Plus
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   0 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS=   0 Ivl=125us
I:  If#= 0 Alt= 1 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS= 512 Ivl=125us
I:  If#= 0 Alt= 2 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS=1020 Ivl=125us
I:  If#= 0 Alt= 3 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS=1024 Ivl=125us
I:  If#= 0 Alt= 4 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS=2048 Ivl=125us
I:  If#= 0 Alt= 5 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=2ms
E:  Ad=82(I) Atr=01(Isoc) MxPS=3072 Ivl=125us
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 0 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=84(I) Atr=01(Isoc) MxPS=   0 Ivl=125us
I:  If#= 2 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=84(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms
[snip]

```

---

