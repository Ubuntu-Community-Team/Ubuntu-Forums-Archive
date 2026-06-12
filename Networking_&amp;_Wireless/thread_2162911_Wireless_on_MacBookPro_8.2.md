---
title: "Wireless on MacBookPro 8.2"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by Lars Noodén on 2013-07-16
I'd like to start using the wireless card in my MacBookPro 8.2 with (k)ubuntu 13.04.  The card is not showing up in the graphical Configure->Network Connections nor is it found by ifconfig.  Where do I start?

---

### Post by Hadaka on 2013-07-16
Hi, here is your wirless card..
BCM4331 802.11a/b/g/n
give this a try..if it doesnt fire up we'll find out why.
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by Lars Noodén on 2013-07-16
Thanks. After installing the linux-firmware-nonfree and rebooting, *sudo modprobe b43* produces no output.  At least nothing is coming over stdout.

---

### Post by Hadaka on 2013-07-16
Please post the output of..
```
rfkill list all
ifconfig
lsmod
lspci -nn | egrep '0200|0280'
cat /etc/network/interfaces
```
thanks.

---

### Post by Lars Noodén on 2013-07-16
ifconfig is finding wlan0

For the output of the programs, see the attachment.

---

### Post by Hadaka on 2013-07-16
thanks, is your "enable wireless" checked?
please post
```
sudo modprobe -rf b43
sudo modprobe -v b43
dmesg | egrep 'b43|wlan'
```
thanks.

---

### Post by Lars Noodén on 2013-07-16
The menu System Settings-> Network Connections appears to be finding the wireless network interface now, but cannot find the network with its scan.

---

### Post by Hadaka on 2013-07-16
ok,please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo iwlist wlan0 scan
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
```
BOOT
if it still fails...try a power reset.
computer and router..
everything is there...it should be working.
thanks.

---

### Post by Lars Noodén on 2013-07-16
Ok.  Done, the linux-headers-generic were already there and the latest version.  

*sudo iwlist wlan0 scan* produced no results.  After rebooting, the results are the same.

---

### Post by Hadaka on 2013-07-16
interesting...have you tried disconnecting the
ethernet cable..and booting?  Give that a go.
im researching..

---

### Post by Lars Noodén on 2013-07-16
Disconnecting the ethernet cable only cuts off the current connection.  I'm still not able to connect or even scan wlan0

---

### Post by Hadaka on 2013-07-16
does the aapl have a wireless on/off switch?
rfkill shows good...but..
also please go into network settings and
set IPv6 to IGNORE
while in there...check your IPv4 and security settings.
and..did you recently install this card?..the system see's it,
the driver loads,yet it has zero rx and tx packets....odd
still searching..

---

### Post by Hadaka on 2013-07-16
ok,try this..
```
sudo su
echo 'b43' >> /etc/modules
exit 0
```
BOOT
Now is it working??

---

### Post by Lars Noodén on 2013-07-16
Thanks for looking into this.  Adding /etc/modules with the content 'b43' still had no effect.  The iwlist scan shows nothing.

---

### Post by Hadaka on 2013-07-16
please check that your router wireless is activated, your ifconfig
is reflecting it doesnt even see the router.
thanks.

---

### Post by Lars Noodén on 2013-07-16
Thanks. That was the first thing I checked once wlan0 started to show up.  Wireless is up and running and I can connect to it using OS X but not Kubuntu 13.04.  The machine is dual boot and I can get rid of OS X as soon as (k)ubuntu works with the wireless.

---

### Post by Hadaka on 2013-07-16
ok, please do..
```
sudo modprobe -rf b43
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo modprobe -v b43
```
then do..and post
```
dmesg | grep -e b43 -e bcma
```
thanks.
I will be gone for the rest of the afternoon and
have asked the good Dr chili555 to please take a look
at this.

---

### Post by Lars Noodén on 2013-07-16
Ok.  Thanks.  Here is the excerpt from dmesg in the attachment.

---

### Post by Hadaka on 2013-07-16
Hi, let's try bouncing the driver..
please do..
```
sudo apt-get remove --purge linux-firmware-nonfree
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe b43
```
thanks.

---

### Post by varunendra on 2013-07-17
Hello Lars, Hadaka, hope I'm not trespassing a "no entry" zone :P

@ Lars,
You may generate a summarized detail of the wireless setup by using wireless_script, following the "Wireless Script" link in my signature.

Also, it seems that your device can work with only b/g channels with b43 driver ([http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)). So if you have other modes enabled in the router/access point, try changing it to b/g only. Refer to your router's manual to see how to do that.

---

### Post by Lars Noodén on 2013-07-17
Thanks.  I guess that's a shortcoming in the driver, because the hardware itself supports 11a.  I'm currently using 11a from the base station because that has much better range than 11g on the card it has.

---

### Post by varunendra on 2013-07-17
Yes, the card even supports n channel as per lshw output. Disabling the additional channels is not always necessary, but sometimes it may confuse the driver due to overlapping bandwidth of adjacent channels.

The wireless_script I proposed may give us a clearer picture and maybe we can find some obvious culprit to fix it without working on guesses. :)

---

### Post by chili555 on 2013-07-17
>  I'm currently using 11a from the base station because that has much better range than 11g on the card it has. However...> it seems that your device can work with only b/g channels with b43 driverBINGO!

Please change the router to B and G and we suspect you will be all set.

---

### Post by varunendra on 2013-07-17
> **chili555 said:**
> ...BINGO!

...because there is ONLY 11a, no adjacent (b/g) channels at all ! Why couldn't I catch such a simple hint ? :(

---

### Post by Lars Noodén on 2013-07-17
Thanks for all the tips, I'm going to need to play around a bit more to get it to work.  The 11g vs 11a lead seems promising.  I seem to have my base station now reconfigured to transmit in 11g now, but not able to connect yet using Kubuntu.  On the same hardware, using OS X, I can connect.  On different hardware using OpenBSD, I cannot connect, though I can see the network if I scan.

---

