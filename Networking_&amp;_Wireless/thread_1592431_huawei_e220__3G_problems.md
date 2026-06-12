---
title: "huawei e220  3G problems"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by iamnotthemessiah on 2010-10-10
hi

im struggling badly to get this dongle working in maverick (worked fine in lucid and karmic). if i unplug it and plug it in again 30 times it sometimes works, also deleting a connection in thenetwork manager and making a new one sometimes works after about 10 attempts. sometimes it works if i leave the computer for 10 mins and then suddenly its connected. seems to me its some kind of usb problem cos lsusb takes 10 minutes to finish as well

the lsusb output is Bus 003 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

the sakis3g thing mentioned in another thread also works sometimes and once it works with sakis3g it also works with the network manager applet. seems like theres a problem initializing the dongle?

any help would be very welcome

is there any more info i should provide? oh this is maverick 64bit

---

### Post by alexfish on 2010-10-10
hi

before starting sakis3g try this

open system monitor select modem-manager and end the process 

then when in sakis3g select More Options then select Prepare Modem register network and update Hal

or Set-up Modem (switch + load module + set-up tty)

see what happens

---

### Post by alexfish on 2010-10-11
Hi

from the terminal try

Code:
[COLOR=Blue]
sudo modprobe option[/COLOR]

---

### Post by Stearns on 2010-11-07
I'm actually experiencing the exact same issue, and as I use my laptop quite a bit away from home this is a massive hindrance. Any help at all would be appreciated.

Funny thing is it worked flawlessly until a couple of weeks ago. I unplugged the dongle without safely removing it first and after that this whole mess started. I run Ubuntu 10.04 LTS (Lucid Lynx) 64-bit on a Compaq Presario CQ60 system.

I'm quite acquainted with Ubuntu but far from experienced, so consider me a beginner if anyone replies to this. 

[quote=alexfish]Hi

from the terminal try

Code:
[COLOR=Blue]
sudo modprobe option
[/COLOR][/quote][COLOR=Blue]

[/COLOR]This doesn't amount to anything in the terminal, no response. Or am I looking for some other result?

---

### Post by alexfish on 2010-11-07
Hi Stearns

can you post results of this command from the terminal

Code:

usb-devices

locate the lines which indicate the device and post only those lines

does anything show in the boot screen when booting with the device connected

---

### Post by Stearns on 2010-11-10
Morning alexfish.

Well, this is a bit embarrassing. After submitting my first post, I took the liberty of going haywire on my laptop. I first removed the mobile connection from the connection manager, then I safely removed the dongle and reinserted it. I did this about ten times or so until I let it be for about half an hour and as usual it recognized the dongle as a mobile broadband device after that. I configured it but afterwards deleted it, then safely removed and reinserted it a couple of times again. The laptop didn't recognize it as a mobile device even once during this. But I then rebooted my laptop after a final attempt to safely remove the dongle. And funny thing is, now it works perfectly. Each and every time I connect it it instantly acknowledges the dongle as a mobile device and I can connect to the Internet.

It's been a couple of days since I did this, and it's been working flawlessly ever since. I have no idea what actually did the trick and something tells me my method was far from orthodox, but at least it's working.

I'll get back to you if the problem appears again, but at least for now I don't have to worry about that. 

Cheers for the quick reply, I appreciate it. All the best.

---

### Post by brunolabs on 2010-11-21
> **iamnotthemessiah said:**
> hi

im struggling badly to get this dongle working in maverick (worked fine in lucid and karmic). if i unplug it and plug it in again 30 times it sometimes works, also deleting a connection in thenetwork manager and making a new one sometimes works after about 10 attempts. sometimes it works if i leave the computer for 10 mins and then suddenly its connected. seems to me its some kind of usb problem cos lsusb takes 10 minutes to finish as well

the lsusb output is Bus 003 Device 003: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

the sakis3g thing mentioned in another thread also works sometimes and once it works with sakis3g it also works with the network manager applet. seems like theres a problem initializing the dongle?

any help would be very welcome

is there any more info i should provide? oh this is maverick 64bit


I have exactly the same problem. 
Sometimes works fine, sometimes needs several attempts.

In response to alexfish command:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev=00.00
S:  Manufacturer=HUAWEI Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```


How can I solve this?

Thanks in advance.

---

### Post by alexfish on 2010-11-21
> **brunolabs said:**
> I have exactly the same problem. 
Sometimes works fine, sometimes needs several attempts.

In response to alexfish command:

```
T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev=00.00
S:  Manufacturer=HUAWEI Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 3 Cfg#= 1 Atr=a0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
```
How can I solve this?

Thanks in advance.

from the info shown the device should be ready to connect

Will it connect


ALSO
this is a post from
**Re: Known Maverick Meerkat issues/bugs  with workarounds**
**3g broadband  dongles**:


some of these devices are been reported : "[COLOR=Blue]not recognized on the system[/COLOR]" or "[COLOR=Blue]will not configure[/COLOR]"

this is due to the option  driver module not loading

as a workaround the option driver can  be loaded from the terminal


[**How to check for the option drive****r and  modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")

**Update :** Mon Oct 25 :  2010

**ZTE** devices not switching : above link updated with  fix

these problem usually disappears by keep the system updated

**Update:**  Sat Oct 23 : 2010

There have been reports of devices Freezing (  under use ) hence can no longer connect : the above link has been  updated (Don,t moan it is NOT A FIX ) as each device is different
However  I have tested one such device and have used Sakis3g to reconfigure a  ZTE 626 {successful} : may also help with preparing Some CDMA devices

alexfish

---

### Post by brunolabs on 2010-11-25
> **alexfish said:**
> 
[**How to check for the option drive****r and  modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")


Thanks! That works!

;)

---

### Post by brunolabs on 2011-01-09
Is this bug solved in 10.10? Or will it be in 11.04?

---

