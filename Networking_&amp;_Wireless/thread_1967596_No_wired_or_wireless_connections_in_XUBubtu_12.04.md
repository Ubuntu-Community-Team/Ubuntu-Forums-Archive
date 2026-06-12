---
title: "No wired or wireless connections in XUBubtu 12.04"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by jmahun on 2012-04-28
I have an older eMachines m5312 laptop on which I've been running XUbuntu 11.xx. It has both wireless and wired connections. Both operated fine until I just upgraded to XUbuntu 12.04. Even though my wireless setting were preserved in the upgrade (SSID, security password), the laptop won't connect to wireless (I've two different wireless networks, either which worked OK before, neither of which connect now). On top of that, my wired connection doesn't work either.
What happened?

My computer uses a Broadcomm BCM 4306 (rev 2) wireless and Broadcomm BCM 4401 wired.

On my Windows machine, my connection dialog allows me to try to initiate a connection - can this be done in XUbuntu? All I can see is a disconnect option.
Any ideas would be appreciated.

---

### Post by chili555 on 2012-04-28
Please open a terminal and run and post:```
lspci -nn | grep -e 0280 -e 0200
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by jmahun on 2012-04-28
lspci -nn | grep -e 0280 -e 0200

00:00c.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)

00:0e.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)


rfkill list all
nothing displays

---

### Post by chili555 on 2012-04-28
The wireless will be easy to fix if we have wired. Hook up the ethernet cable and do:```
sudo modprobe b44
```Does wired come to life? If so, please do:```
sudo su
echo b44 >> /etc/modules
echo b43 >> /etc/modules
apt-get install linux-firmware-nonfree
exit
```Now both should be working.

---

### Post by jmahun on 2012-04-28
> **chili555 said:**
> The wireless will be easy to fix if we have wired. Hook up the ethernet cable and do:```
sudo modprobe b44
```Does wired come to life? If so, please do:```
sudo su
echo b44 >> /etc/modules
echo b43 >> /etc/modules
apt-get install linux-firmware-nonfree
exit
```Now both should be working.

The first command did get my wired network connected.

The second set of commands installed software but my wireless would still not connect. I rebooted to check, but still no wireless connection.

---

### Post by chili555 on 2012-04-28
Let's see why:```
dmesg | grep b43
ls /lib/firmware/b43
```I don't need the output from the last command; either it says no such file or it says about a zillion files. Which is it?

---

### Post by jmahun on 2012-04-28
> **chili555 said:**
> Let's see why:```
dmesg | grep b43
ls /lib/firmware/b43
```I don't need the output from the last command; either it says no such file or it says about a zillion files. Which is it?

It shows a zillion files.

---

### Post by chili555 on 2012-04-28
And what about this?```
dmesg | grep b43
```

---

### Post by jmahun on 2012-04-28
> **chili555 said:**
> And what about this?```
dmesg | grep b43
```

It responds with:
[    28.3750001] b43-pci-bridge 0000:00:0c.0: PCI INT A -> Link[LNK2] -> GSI 10 (level, low)-> IRQ 10

---

### Post by chili555 on 2012-04-28
Something funny is going on here. I'd like to look at your entire kernel messages file. Please reboot so we have a clean slate and do:```
dmesg > jmahun.txt
lsmod >> jmahun.txt
sudo cat /var/log/syslog | grep 00.0e >> jmahun.txt
zip jmahum.zip jmahum.txt
```In your home directory, you will find a file called jmahum.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

I love a mystery!

---

### Post by jmahun on 2012-04-28
> **chili555 said:**
> Something funny is going on here. I'd like to look at your entire kernel messages file. Please reboot so we have a clean slate and do:```
dmesg > jmahun.txt
lsmod >> jmahun.txt
sudo cat /var/log/syslog | grep 00.0e >> jmahun.txt
zip jmahum.zip jmahum.txt
```In your home directory, you will find a file called jmahum.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

I love a mystery!

Zip file is attached.
I'm a casual linux user so am at a total loss as to what's going on here. I really appreciate the time & effort you're putting into this.

---

### Post by chili555 on 2012-04-28
From your *lsmod*:> b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
[COLOR="Red"]bcma[/COLOR]                   25651  1 b43
b44                    31412  0 
ssb                    50691  2 b43,b44I have no idea why bcma should load. Please do:```
sudo gedit /etc/modules
```If bcma is in there, remove it. Proofread, save and close gedit. Now do:```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have a report.

---

### Post by jmahun on 2012-04-28
> **chili555 said:**
> From your *lsmod*:I have no idea why bcma should load. Please do:```
sudo gedit /etc/modules
```If bcma is in there, remove it. Proofread, save and close gedit. Now do:```
sudo su
echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have a report.


I get "sudo: gedit: command not found" when I type in the first command.

---

### Post by chili555 on 2012-04-28
Oops! Sorry, in xubuntu, the text editor is Leafpad. Please revise my instructions:```
sudo leafpad /etc/modules
```

---

### Post by jmahun on 2012-04-28
OK, did so. Have attached a new zip file.

---

### Post by chili555 on 2012-04-28
Your lsmod says:> 43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
[COLOR="Red"]bcma[/COLOR]                   25651  1 b43
mac_hid                13077  0 
b44                    31412  0 
ssb                    50691  2 b43,b44 Please show me:```
cat /etc/modules
ls /etc/modprobe.d
cat /etc/modprobe.d/blacklist.conf
```Your blacklist was evidently ineffective.

I see lots of this in *dmesg*:> reserve_ram_pages_type failed 0x1cd84000-0x1cd85000, track 0x10, req 0x10I am not sure if it's significant or not. You might Google it and ask over on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I don't imagine a RAM problem, if that's what it is, can be good.

---

### Post by jmahun on 2012-04-28
I give up - am going back to XUbuntu 11.xx.
Thanks for all your help.

---

### Post by chili555 on 2012-04-28
Sorry I couldn't be of more help. I'm still more than anxious to help you if you want to try.

---

