---
title: "Compaq Mini 311c No Wifi (First day of ubuntu)"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by fr33ka on 2013-04-24
Hi y'all


Great forum and thanks to all that have contributed thus far as it has helped me make the move from MS to here.


I have a question and this is going to sound incredibly simple and that is because I am totally new to ubuntu and anything non-MS based.

I have a compaq mini 311c 1020SA and the wireless driver is not installed I believe because the hard switch on my netbook is no longer functioning.

I have gotten as far as confirm that the internet is available via a wired ethernet connection and I have also managed to work out the terminal commands to get the details on the hardware: [COLOR=#333333] broadcom bcm4312 rev.1



However this is where I get stuck. I have tried different solutions presented on the net to solve this problem but the simple fact of the matter is that the instructions are too high-level for me as I have NO knowledge of linux/ubuntu prior to yesterday.

For example, solutions have reached dead ends such as privilege issues, rpm package not existing issues, not knowing how to install drivers etc etc.

Basically, I am after a kind soul to really hold my hand through this. Once I am online via Wifi and I am not sat in the hallway next to my router then I can trawl through the forums and really get the hand of this transition away from MS. However, until then I could do with some help!

Many thanks in advance.



Adi[/COLOR]

---

### Post by chili555 on 2013-04-24
I would love to help and I think this will be pretty easy. We are going to use the terminal Ctrl + Alt + t because we can gather information easily and quickly. Please open the terminal and run this command and give us just a bit more information about your wireless card:```
lspci -nn -d 14e4:
```I would also like more information about your wireless switch:```
rfkill list all
```Post those results and we'll continue.

---

### Post by fr33ka on 2013-04-24
Hi there


Thanks for helping. Here is the info you requested:

```
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

and


```
hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: no

1:hp-bluetooth: Bluetooth
Soft blocked: no
Hard blocked: no

2:hci0: Bluetooth
Soft blocked: no
Hard blocked: no

```


Hope that helps, look forward to the next step....

---

### Post by chili555 on 2013-04-24
It helps. There is controversy as to the best way to get the famous 14e4:4315 going. Let's try my favorite way first. With a temporary wired ethernet connection, please do::```
sudo apt-get install linux-firmware-nonfree
sudo modprobe -r b43 && sudo modprobe b43
sudo iwlist wlan0 scan
```If you get scan results, it ought to be fixed. You should then click the Network Manager icon at the top right, see your network and connect. If not, post back and we'll try again.

Your wireless switch seems in order. The reason it couldn't turn the wireless on and off is because until the driver is working, there is no wireless to turn on!

---

### Post by fr33ka on 2013-04-24
Hi there

Thanks for the response. I am unsure, but I think I fell over at the first hurdle:
```

adi@adi-Compaq:~$ sudo apt-get install linux-firmware-nonfree
[sudo] password for adi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
adi@adi-Compaq:~$ sudo modprobe -r b43 && sudo modprobe b43
adi@adi-Compaq:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
```


Look forward to the next step...

---

### Post by fr33ka on 2013-04-24
Hi there


Just to update, I tried doing an update of the Ubuntu software via:

```

$ sudo apt-get update

$ sudo apt-get upgrade

```


I then followed your instructions again and it worked a charm!

Thankyou for your help!



Adi

---

