---
title: "IOGEAR USB speakerphone support"
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by paklonder on 2006-12-28
Hello,

I am just starting to get comfortable after switching from Windows to Ubuntu Edgy. Something came up today for what I have found no clear way to solve it. Up to yesterday, I had a Philips Vesta webcam that I was able to use as a spekerphone for Skype and other apps. It showed as a 2nd device in the ALSA mixer and worked very well.

I felt encouraged for this support of USB devices and purchased an inexpensive USB speakerphone. It shows us (I guess it is recognized by the OS) in the Device Manager applet as "FM1083" USB Audio Interface by FORTEMEDIA. I don't know how to dump this information to attach it to my post, so please provide some help so I can give you all the information you may need to help me trace the problem and use this spekaerphone.

Thanks in advance,

Paco

PS - Of course, I have tried the main FAQs and reinstalled the ALSA support utils and drivers.

---

### Post by paklonder on 2006-12-28
I found a way to share some information about my configuration; I jst included the speakerphone entry in the list:

cat /proc/bus/usb/devices
pacoc@pacoc-ubuntu:~$ cat /proc/bus/usb/devices

............

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=138c ProdID=0001 Rev= 0.01
S:  Manufacturer=FORTEMEDIA
S:  Product=FM1083
C:* #Ifs= 3 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=(none)
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=81(I) Atr=05(Isoc) MxPS=  16 Ivl=1ms
I:  If#= 2 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 2 Alt= 1 #EPs= 2 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=02(O) Atr=05(Isoc) MxPS=  16 Ivl=1ms
E:  Ad=83(I) Atr=0d(Isoc) MxPS=   8 Ivl=1ms

---

