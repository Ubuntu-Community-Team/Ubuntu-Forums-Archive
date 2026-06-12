---
title: "Cheap USB sound adapters"
date: 2006-01-19
forum: Multimedia &amp; Video
---

### Post by FarEast on 2006-01-19
Hi;) ,

There are some sound chips which can be hardly configured.
And their capability on Linux may be far from our expectation.

I think that a cheap USB sound adapter may be a good solution
for those who own PCs with such sound chips.

[http://www.usbmax.com/Category_USB_Sound.cfm](http://www.usbmax.com/Category_USB_Sound.cfm)

How about sharing information of them?
(I have not tried one, though:razz: )

Note:
I did not mean 'cheap and nasty' by the word 'cheap', of course.
I would like to find good items that we can obtain at a reasonable
price to enjoy sound on Linux.

---

### Post by FarEast on 2006-01-19
I have found an informative site;) .
[http://www.qbik.ch/usb/devices/showdevcat.php?id=7](http://www.qbik.ch/usb/devices/showdevcat.php?id=7)

------

PS
Here is my trial report(successful!).

I bought the following.  
[http://www.owltech.co.jp/products/speaker/SPADP/spadp_usb.html](http://www.owltech.co.jp/products/speaker/SPADP/spadp_usb.html)
Price: ~$[COLOR="Red"]22[/COLOR] (today's rate)

It was recognized properly and I could listen to ogg/mp3 files with XMMS.
Below is the information I got from **/proc/bus/usb/devices** .

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  **Vendor=0d8c ProdID=0001 Rev= 0.10**
S:  **Manufacturer=C-Media INC.**
S:  Product=USB Audio
C:* #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 0 Cls=01(audio) Sub=01 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 0 #EPs= 0 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
I:  If#= 1 Alt= 1 #EPs= 1 Cls=01(audio) Sub=02 Prot=00 Driver=snd-usb-audio
E:  Ad=06(O) Atr=09(Isoc) MxPS= 192 Ivl=1ms

---

