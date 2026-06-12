---
title: "getting lirc working with Ricavision's transceiver?"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by Ninto on 2007-05-30
I'm having a problem, and maybe you can help...

I have the Ricavision eHome Infrared Transceiver which shows as:

```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=16 #Cfgs=  1
P:  Vendor=0768 ProdID=0023 Rev= 0.00
S:  Manufacturer=Ricavision
S:  Product=eHome Infrared Transceiver
S:  SerialNumber=RH00001E
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  16 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  16 Ivl=0ms

```

The default lirc_mceusb2.c file has a different Ricavision transceiver showing, with a different vendor and product ID, so I changed the entry to reflect what shows up in cat /proc/bus/usb/devices as per above, then: 

cd /usr/src/lirc-0.8.2pre2/
./config
make
make install
modprobe lirc_mceusb2
/etc/init.d/lircd restart
irw

Then irw seems to close immediately, and lircd stops.  /var/log/messages shows:

May 27 15:47:25 localhost lircd-0.8.2-CVS[3354]: lircd(userspace) ready
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: accepted new client on /dev/lircd
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: could not get file information for /dev/lirc
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: default_init(): No such file or directory 
May 27 15:47:29 localhost lircd-0.8.2-CVS[3354]: caught signal

/dev/lirc does exist.

cat /proc/bus/usb/devices shows the same problem as above, Driver=(none)

Thoughts?  I'm going insane with this, I've tried so many things so far, and nothing seems to work.

---

### Post by Ninto on 2007-06-05
Nobody?

---

