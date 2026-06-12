---
title: "Huawei E355"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by barunjit on 2013-04-19
Hi,

I have recently bought a Huawei E355 Wifidongle/datacard. The problem is that when i connect it to my machine (OS:ubuntu 11.10) even though wifi is detected properly and i am able to connect to internet through wifi, i am not able to do so through 3g. in short, even though i am able to use it as a wifi hot spot, i am not able to use it as a 3g usb.

i have already installed the huawei driver for linux OS but after doing so the network manager shows the connection as a wired connection which is disconnected. when i try to create a mobile broadband connection by clicking on edit connections->mobilebroadband->add i am not able to choose the huawei device. effectively,i am not even able to create a mobile broadband connection as the device is not shown there. i have attached the relevant screen shots. Experts please help.


Thanks,
Barun

---

### Post by mörgæs on 2013-04-20
First you should do a fresh install of 12.10, both because 11.10 is running out of support in a few weeks and because software supporting USB dongles has evolved in the meantime.

---

### Post by barunjit on 2013-04-20
Hi Morgaes,

Thanks for the reply. i had the same problem with 11.04 and hence i upgraded to 11.10. Now the problem is that i don't see an upgrade option in 11.10 update manager,so how i am supposed to upgrade to 12.10? kindly suggest.

Thanks,
Barun

---

### Post by mörgæs on 2013-04-20
My advice was a fresh install, not an upgrade.

---

### Post by barunjit on 2013-04-21
Hi Guys,

Sorry but i am facing the same problem even after moving to ubuntu 12.10 LTS. Please Help.



Thanks,
Barun

---

### Post by barunjit on 2013-04-21
Sorry,the version i have upgraded to is 12.04 LTS and not 12.10

---

### Post by mörgæs on 2013-04-22
Good, with 12.04 this should do the trick:
[http://blog.schnattern.at/huawei-e355-unter-ubuntu-1204](http://blog.schnattern.at/huawei-e355-unter-ubuntu-1204)

---

### Post by barunjit on 2013-04-22
Hi,

I installed the Huawei linux driver but that didn't seem to have helped. The driver seem to have installed successfully but i am still not able to connect to internet through 3g USB modem.

After installing the driver i can see some like this **Wired Network (Huawei Mobile) disconnected** ,under the network manager but this is not enabled. The system tries to connect to this 

wired connection periodically and fails to do so. Please Help. i am pasting the output of **usb-devices** before and after installing the Huawei Linux driver.

**Before installing the driver**

T:  Bus=01 Lev=02 Prnt=02 Port=00Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c1e Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 1 Cls=02(commc)Sub=0d Prot=00 Driver=(none)
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage 


**After installing the driver**

T:  Bus=01 Lev=02 Prnt=02 Port=00Cnt=01 Dev#=  6 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1c1e Rev=01.02
S:  Manufacturer=HUAWEI
S:  Product=HUAWEI Mobile
C:  #Ifs= 5 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 1 #EPs= 3 Cls=02(commc)Sub=0d Prot=00 Driver=huawei_ether
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage


Thanks,
Barun

---

### Post by mörgæs on 2013-04-22
Then I'm out of ideas, sorry.

---

### Post by alexfish on 2013-04-24
hi barunjit


the details show that in first instance the standard OPTION driver has attached to the device
> I: If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option < [COLOR=#0000ff]should connect on this port ttyUSB0[/COLOR]
I: If#= 1 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage
I: If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.)Sub=ff Prot=ff Driver=option
I: If#= 3 Alt= 0 #EPs= 1 Cls=02(commc)Sub=0d Prot=00 Driver=(none)
I: If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.)Sub=06 Prot=50 Driver=usb-storage 
if the correct details are entered in Network Manager then the device should connect

the second shows the Huawei drivers attaching as huawie_ether
when using this driver Network Manager may not see the device ,
but can use ppp direct .
to configure ppp

```
sudo pppconfig
```

enter the correct details , use port 'ttyUSB0' I think on last page , may need to set your user permissions

so the device should connect with ethier driver. using ppp

to call ppp

```
pon  <your provider>
```

where <your provider> is the name of the connection made in ppp.

the Huawie driver will probably get over written on updates to the Kernel.

HTH

Alex

---

