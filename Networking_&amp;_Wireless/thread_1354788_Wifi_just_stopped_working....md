---
title: "Wifi just stopped working...?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by aspasia82 on 2009-12-14
It seems my laptop no longer recognizes available wireless networks.  Pretty inconvienient timing for me because I am traveling for the next 6 weeks and only able to connect at starbucks/mcdonalds, etc.  I never had a problem before...

I have a Dell 1420, running Hardy, pro/wireless 3945abg.
When I ran iwconfig it said:
lo       no wireless extensions
eth0     no wireless extensions

Someone please help!  I'm mostly a GUI only girl, so please take it easy on me!  :)

---

### Post by chili555 on 2009-12-14
Please open a terminal (Applications -> Accessories -> Terminal) and type:```
dmesg | grep rfkill
```Does it say the kill switch must be turned off for the wireless to operate? If so, move that little switch on the left front of your laptop.

If not, let's reload the driver and see if it comes to life:```
sudo modprobe iwl3945
iwconfig
```Did your wireless reappear? If not, please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```You will find a file called *dmesg.zip* in your Home directory that you can transfer on a USB key or otherwise and attach it to your reply.

---

### Post by aspasia82 on 2009-12-17
Sorry it took me so long to reply.  I'm borrowing a friend's computer.
It seems to say the kill switch is on whether it is on or not... But it was definitely off when all this started, and off now, despite what it says. 
Here's the file you asked for.

---

### Post by aspasia82 on 2009-12-17
Also, thanks Chili for your help!  : D

---

### Post by chili555 on 2009-12-17
Let's create a new file to tell your wireless card to wake up and act right. Please do:```
sudo gedit /etc/modprobe.d/iwl3945.conf
```Your text editor will pop up and say it's a new file. Add two lines:```
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
```Proofread twice, save and close gedit. If you don't have gedit, use kate, nano or even vim. The same process applies in any case: proofread twice, save and close.

Next take that laptop over to the router or modem and hook up an ethernet cable and do:```
sudo apt-get install linux-backports-modules-karmic-generic
```May I assume you are running Karmic, the latest release? Find out with:```
lsb_release -c
```Install *backports* for whatever version you are running. Disconnect the ethernet cable and reboot. Now do you have correctly operating wireless?

---

