---
title: "ralink 802.11 n WLAN adaptor help"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by andyn11 on 2013-03-13
after figuring that my internal wifi card is useless i went and got a ralink 802.11 n WLAN usb antena ... got it in the post today and plugged it in exspecting it to work (iam not a mega linux user and everything has worked for me on default in the past ... most of the time) but i cant get it working 

got a driver CD with it but as iam no mega linux user it all looks mumble jumble to me 

on my connections tab it detects it but all is dull and it says it is disabled by hardware switch 

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

the usb is phy1 and has no actual buttons on the usb antena ... just a small light 

nothing happens with rfkill unblock all and thats about as far as i can get by myself 

:mad::mad:

---

### Post by chili555 on 2013-03-13
> after figuring that my internal wifi card is uselessWhy is that?> 0: phy0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]
1: phy1: Wireless LAN
Soft blocked: no
Hard blocked: no
Many laptops, including my Lenovo, are built to disallow wireless networking if the wireless switch is off. I'd turn it on and try again. If your internal really is useless, which I doubt, I'd blacklist its driver. If its driver loads and interferes with the USB, then maybe it isn't useless.

---

### Post by andyn11 on 2013-03-13
its useless coz no matter if i try win xp or ubuntu it doesnt work 

phy0: is the internal that doesnt turn on with wifi button on the laptop 

phy1: is the new usb wifi antena i bought that aparently works with linux (got the drivers on mini CD but dont know wut to do with em

---

### Post by andyn11 on 2013-03-13
im using the laptop now running ubuntu and using my mobiles USB tethering to supply it with net

---

### Post by chili555 on 2013-03-13
What does this tell us with the Ralink inserted?```
lspci -nn | grep 0280
lsusb
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by andyn11 on 2013-03-13
andy@andy-330:~$ lspci -nn | grep 0280
00:05.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
andy@andy-330:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 004: ID 0fce:7169 Sony Ericsson Mobile Communications AB 
andy@andy-330:~$

---

### Post by chili555 on 2013-03-13
I would blacklist the driver for the internal, just in case:```
sudo su
echo "blacklist ipw2200" >> /etc/modprobe.d/blacklist.conf
modprobe -r ipw2200
```And add the driver for the USB so it loads automatically:```
echo rt2800usb >> /etc/modules
```And load it:```
modprobe rt2800usb
exit
```Did a wireless interface get created, ideally wlan0?```
iwconfig
```How recent is your Ubuntu version?```
lsb_release -d
```I ask because 148f:5370 is a relatively recent device and won't be covered, for example, in 10.04.

---

### Post by andyn11 on 2013-03-13
andy@andy-330:~$ sudo su
[sudo] password for andy: 
root@andy-330:/home/andy# echo "blacklist ipw2200" >> /etc/modprobe.d/blacklist.conf
root@andy-330:/home/andy# modprobe -r ipw2200
root@andy-330:/home/andy# echo rt2800usb >> /etc/modules
root@andy-330:/home/andy# modprobe rt2800usb
root@andy-330:/home/andy# exit
exit
andy@andy-330:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

andy@andy-330:~$ lsb_release -d
Description:    Ubuntu 12.04.2 LTS

---

### Post by andyn11 on 2013-03-13
wut ever you told me to type worked :-) thanks a million :-) been trying to get the wireless working in some way on this laptop and you solved it in no time lol great !

---

### Post by chili555 on 2013-03-13
Glad it's working! It's a wonder what a few thousand posts worth of experience can do!

Please edit the title of your thread to add [SOLVED]. Thanks.

---

### Post by kurt18947 on 2013-03-13
I've been following this thread seeing if the O.P.s 148f:5370 device would behave.  I just got one and feel it's a very good choice for plug 'n' play wifi adapter for portables.   Mine works with no issues on 12.04 and later and cost me $6 delivered from an Ebay vendor,  I don't have an earlier distro installed to try.

---

### Post by Ron O on 2013-04-22
Your March 13th post worked GREAT on an old laptop with a fresh install of Xubuntu 12.04. It was an older Centrino processor with a possible burned out wifi section and a locked (proprietary) bios preventing redirection via the bios. I used a Ralink usb/wifi dongle as a substitute for the internal hardware. I think blacklisting the driver to the internal wifi was key. I did a lot of research on this, and your solution was the only one that worked- connected at full speed with a strong signal immediately. Thanks.

---

