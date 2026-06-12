---
title: "install wimax usb modem &quot;huawei BM338&quot; driver on ubuntu 12.04"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by woxuxow on 2013-03-23
Is there a driver for  wimax usb modem "huawei BM338"
i use ubuntu 12.4 64bit

---

### Post by sanderj on 2013-03-23
> **MustafaJF said:**
> Is there a driver for  wimax usb modem "huawei BM338"
i use ubuntu 12.4 64bit

Have you got the USB modem? If so, did you plug it in?

---

### Post by woxuxow on 2013-03-23
Are you kidding me?
Of course 
it is a usb modem
it does not recognized by ubuntu

---

### Post by alexfish on 2013-03-23
Hi MustafaJF

No sure about wimax modems but at least can find out what state the device is in

Going to need Two test results from the terminal one , Device plugged before boot and on plugged after boot

Prior To
If have alternate connect for your Ubuntu version update the use ID's

From the terminal

```
sudo /usr/sbin/update-usbids
```

the code to execute for the results
```
usb-devices
```
look for the lines which indicate the device and post only those lines
but if both results are the same post only one result

BR

Alex

---

### Post by woxuxow on 2013-03-23
Hi alexfish
I have no access to my modem by monday 
i'll post the result and thanks for your post

---

### Post by sanderj on 2013-03-23
> **MustafaJF said:**
> Are you kidding me?

No.

Do this:

Open a terminal
Unplug the USB-modem, and type

```
lsusb
```

Plug in the USB-modem, and again type

```
lsusb
```

Then find the new line. Post that whole line here, and google USB-ID.

Furthermore, after plugging in the USB-modem, in the terminal type

```
dmesg
```

and copy-paste the screen in this thread

---

### Post by woxuxow on 2013-03-24
Dear sanderj

when modem is plugged following line appears (lsusb)
Bus 002 Device 004: ID 198f:0220 Beceem Communications Inc. BCSM250 WiMAX Adapter 

The result of "dmesg" is about 10 pages
8 last lines are

[  318.570161] InitAdapter:Initialising Adapter = ffff880041c00780 
[  318.570199] InitAdapter:Adapter initialised 
[  318.570204] usbbcm_device_probe:psIntfAdapter 0xffff88005e2b4000 
[  318.570349] usb 2-1.2: RDM Chip ID 0xbece3301 
[  318.597065] beceemUnable To Open File /lib/firmware/macxvi.cfg, err -2 
[  318.597071] bcm_parse_target_params:NOT ABLE TO OPEN THE /lib/firmware/macxvi.cfg FILE 
[  318.597076] beceemInitCardAndDownloadFirmware failed. 
[  318.597079] usbbcm_device_probe:File Not Found.  Use app to download.

---

### Post by sanderj on 2013-03-24
Install linux-firmware-nonfree

---

### Post by woxuxow on 2013-03-24
Dear alexfish

I think my modem is properly recognized but i can't get it in used

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=03.02 
S:  Manufacturer=Linux 3.2.0-27-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1a.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 6 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
P:  Vendor=8087 ProdID=0020 Rev=00.00 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=01 Lev=02 Prnt=02 Port=03 Cnt=01 Dev#=  3 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1 
P:  Vendor=0c45 ProdID=641d Rev=9a.07 
S:  Manufacturer=CN0FJT7K7248703K0167 
S:  Product=Laptop_Integrated_Webcam_1.3M 
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo 
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo 

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 3 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1 
P:  Vendor=1d6b ProdID=0002 Rev=03.02 
S:  Manufacturer=Linux 3.2.0-27-generic ehci_hcd 
S:  Product=EHCI Host Controller 
S:  SerialNumber=0000:00:1d.0 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 8 
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1 
P:  Vendor=8087 ProdID=0020 Rev=00.00 
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA 
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub 

T:  Bus=02 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 0 
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1 
P:  Vendor=198f ProdID=0220 Rev=00.01 
S:  Manufacturer=HUAWEI 
S:  Product=HUAWEI WiMAX USB Stick 
S:  SerialNumber=0 
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA 
I:  If#= 0 Alt= 0 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=usbbcm

---

### Post by alexfish on 2013-03-24
Hi  MustafaJF


Does not look correct , so did search

found a couple pointing in the same direction

this site here seems to be more help .
[http://minhazulhaque.blogspot.co.uk/2012/01/run-beceem-wimax-devices-on-linux-mint.html](http://minhazulhaque.blogspot.co.uk/2012/01/run-beceem-wimax-devices-on-linux-mint.html)



Possible need the xvfz Sprint4GDeveloperPack

Since you are on 12.04 then everything Kernel wise should be OK so if decide to try it , leave the Kernel related stuff as is
did a check on my system and everything that side looks OK.


Like I said , don't know about connecting Wimax , but have resonable Remberance they may need the stuff from Sprint.

So Pretty much on your own as to the decision.

HTH

BR Alex

---

### Post by woxuxow on 2013-03-25
Thanks alexfish
In fact wimax modem belong to my brother and he use windows beside ubuntu. wimax modem works good on windows.
what do you think about fresh installing of ubuntu 13.04 (next month). will anything go well (by installing newer version of ubuntu) ?

---

