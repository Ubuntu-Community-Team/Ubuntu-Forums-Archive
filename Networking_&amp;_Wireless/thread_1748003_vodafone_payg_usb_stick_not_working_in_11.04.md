---
title: "vodafone payg usb stick not working in 11.04"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by clivewilliamson on 2011-05-03
I have a Vodafone (UK) PAYG USB stick (Huawei K3565 v2) which worked perfectly out of the box in 10.10. I also installed Betavine Connection Manager but never actually needed it.

Since upgrading to 11.04 the stick won't connect. When I plug it in I get a green flashing light then a blue one but it never registers with Connection Manager. Nothing I can do tweaking the settings seems to make it work either. BCM doesn't work at all though I  appreciate that's another issue).

Can anyone give me any pointers please, and I should mention that I'm an almost complete novice with Ubuntu.

Thanks

---

### Post by alexfish on 2011-05-03
Hi

BCM will replace modem-manger with its own version (wadercore)

may not be compatible with 11.04.

for now will have to see device is recognised 

open up a terminal and post the results of
```
usb-devices
```

also suggest downloading sakis3g . it does a lot more than just connect

[*Sakis3G* - All-in-one script]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CB4QFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g&ei=vRzATYvsHcfX8gPx1Pi3BQ&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")

alexfish

---

### Post by clivewilliamson on 2011-05-03
Thanks for the reply Alex. When putting in the usb-devices I got the answer as follows (actually there were several others but this seemed the relevant one):


T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  8 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1003 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 4 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


I'll give Sakis 3G a try too.

---

### Post by alexfish on 2011-05-03
Hi

think sakis3g will be a good idea , just been giving 11.04 a whirl 

to see where the bits are etc, but met with problem , can connect with NM , but then 

the browser sometimes will not connect , this makes life difficult if trying to help debug , since most of require files are on separate os , and will be transferring over next few days

So. as you can see from the 

> I: If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I: If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I: If#= 3 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storageeverything looks OK , so not sure if problem with NM modem-manager or ppp, 

now need to see if devs are in place + nodes
from the terminal
```
ls -al /dev/serial/by-id
```and post the the results

This is one area Sakis3g can help . it will do most of what I would post or suggest

if downloaded have a look at the menu option ,there are two set "check more options" also can run sakis3g from the terminal in debug mode
```
sakis3g debug
```

alexfish

---

### Post by clivewilliamson on 2011-05-03
Well the first answer is:


total 0
drwxr-xr-x 2 root root 80 2011-05-03 20:52 .
drwxr-xr-x 4 root root 80 2011-05-03 20:52 ..
lrwxrwxrwx 1 root root 13 2011-05-03 20:52 usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-05-03 20:52 usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1


The second is:Command not found. I thought I'd managed to install it so I'm a bit puzzled.

---

### Post by alexfish on 2011-05-03
Hi
> lrwxrwxrwx 1 root root 13 2011-05-03 20:52 usb-HUAWEI_Technology_HUAWEI_Mobile-if00-port0 -> ../../ttyUSB0
lrwxrwxrwx 1 root root 13 2011-05-03 20:52 usb-HUAWEI_Technology_HUAWEI_Mobile-if01-port0 -> ../../ttyUSB1All the bits are in place 

If you just done straight download of sakis3g then there will be a tarfile in the download directory
can unzip from there or copy to home directory or desktop , there should be a  folder " src " , should see file sakis3g , should be able to run it from there , double click it

to run from terminal need to install as mentioned in post at

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

alexfish

---

### Post by clivewilliamson on 2011-05-03
Well I managed to get it working thanks to your instructions but it won't connect me.

Next step?

---

### Post by alexfish on 2011-05-04
When you say It won't connect

do you mean the browser will not work

alexfish

---

### Post by clivewilliamson on 2011-05-04
Sorry, my previous reply was rather unhelpful (in a hurry but that's no excuse!).

Saki's script ran when I plugged the stick in and gave me the range of options for Vodafone. I selected the right one and tried to connect. The script tried twice but couldn't actually connect at all. 

Looking at another board I have seen that it can work to use the stick to connect on a Windows machine, and that the next time it's connected on Linux it will work. It can't hurt to try I guess though I'm not going to be able to try this until tomorrow now.

Your help and interest is greatly appreciated!

---

### Post by tanzantj on 2011-05-04
I had the same problem and was pulling my hair out to get my Voda dongle to work on 11.04.  Finally I was able to use the network manager by uninstalling (apt-get remove) all components left by Betavine connection manager (or Vodafone Connection Manager). This included:
usb-switchmode
usb-switchmode-data
ozerocdoff
vodafone-mobile-connect
bcm
wadercore
python-messaging

After removing all of those I reinstalled modemmanger (sudo apt-get install modemmanger) and this reinstalled usb-switchmode as a dependency (Voda uses an older package).

Then I plugged in my dongle and Network Manager was able to recognize my dongle (after about 45 seconds) and connect.

I've been using ubuntu for almost 8 months now so I'm by no means an expert and this is my first post on the forums so be gentle if I have broken any posting morays.  I'm constantly looking through these forums for help and decided i should start sharing what i've found. Good luck.

UPDATE:
After seeing the post about Sakis3g I decided to give it a try.  It works like a charm and now has become the default connection manager for me.  If you are struggling with using BCM, Vodafone Connection Manger or Ubuntu's Network-Manger you should really give this a try.  Props to Sakis for their awesome script.

---

