---
title: "Bluetooth not working on Ubuntu 12.04 ralink rt3290"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by theperfectpunk on 2013-02-13
I have installed drivers for ralink rt3290 wifi/bluetooth in ubuntu  12.04. I can turn on bluetooth using hardware switch but it still shows  bluetooth is disabled.
any help?

---

### Post by praseodym on 2013-02-13
Please show:
```

rfkill list
```

---

### Post by theperfectpunk on 2013-02-13
```
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~$ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

---

### Post by praseodym on 2013-02-13
Did you blacklist the native driver rt2800pci?

```
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. Checked the BIOS settings?!

---

### Post by theperfectpunk on 2013-02-13
Blacklisted rt2800pcie still no difference :-(

bluetooth works fine in windows 7, there is no setting in bios for this

anymore suggestion?

---

### Post by praseodym on 2013-02-13
Which driver version did you try? Was it 2.6.0.0?

Here is a bluetooth driver:

[http://downloads.zotac.com/mediadrivers/mb/download/NB087_Ubuntu.zip](http://downloads.zotac.com/mediadrivers/mb/download/NB087_Ubuntu.zip)

---

### Post by theperfectpunk on 2013-02-13
yeah i have installed 2.6.0.0 :-)

i used sudo make to compile

that went fine

but sudo make install didn't work
```
mohit@mohit-HP-Pavilion-g6-Notebook-PC:~/Downloads/rtbth_v3.9.3/rtbth_v3.9.3$ sudo make install
make: *** No rule to make target `install'.  Stop.
```

---

### Post by praseodym on 2013-02-13
Did you read the instructions in there?

---

### Post by theperfectpunk on 2013-02-13
ok thank you got it to work finally!

but i have to run 

```
sudo insmod rtbth.ko
sudo mknod /dev/rtbth c 192 0
./rtbt.bin

```

 can these be set execute at boot somehow?

---

### Post by praseodym on 2013-02-13
Make a script out of it:

```
gksu gedit ~/bluetooth.sh
```
Insert:
```

#!/bin/bash

insmod rtbth.ko
mknod /dev/rtbth c 192 0
./[COLOR="Red"]path/to/the/file/[/COLOR]rtbt.bin

exit 0
```

Executable flag:
```

sudo chmod +x bluetooth.sh
```
And start it at boot-up by adding
```

sh /home/[COLOR="Red"]YourName[/COLOR]/bluetooth.sh
```
before "exit 0" in the **/etc/rc.local**
Do not remove the folders, or, adjust the paths.

---

### Post by diogogmiranda on 2013-03-28
When I try "sudo insmod rtbth.ko" it says "can't read 'rtbth.ko'" 
Where am I wrong here?

thanks

---

### Post by praseodym on 2013-03-29
Try "sudo modprobe -v rtbth"

---

### Post by serh on 2013-04-01
File **rtbth.ko** not exists in driver archive.

---

### Post by thekid90 on 2013-04-11
So I am new to Ubuntu and need some help. I am trying to follow along with the README file but a lot of it does not make sense to me. I have a HP Envy h8-1534 ([http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03639067&prodSeriesId=5330773](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?objectID=c03639067&prodSeriesId=5330773)) which according to lspci is 06:00.1 Bluetooth: Ralink corp. Device 3298 | lspci -n 06:00.1 0d11: 1814:3298. What do I need to make this work?

---

### Post by saimulhq on 2013-04-13
according to pdf after typing sudo modprobe bluetooth nd then typing sudo insmod rtbth.ko, it says "insmod: can't read 'rtbth.ko': No such file or directory", now what should i do please help............

---

### Post by praseodym on 2013-04-14
The original Reealtek driver does not support Bluetooth, try the attached one.[ATTACH]241318[/ATTACH]

Did you install the compilation tools?
```

sudo apt-get install linux-headers-$(uname -r) build-essential
```

---

### Post by serh on 2013-05-02
Some error. File **rtbth.ko** not exists in driver archive. Anybody knows how to install this driver?

---

### Post by 4rielo on 2013-07-31
Hi, i've recently bought a new HP laptop, that has the rt3290 Bluetooth chip. 

lspci command gives this data:
02:00.0 Network controller: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe
02:00.1 Bluetooth: Ralink corp. RT3290 Bluetooth

rfkill list gives only this:
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


So, i've downloaded the file linked above, read the instructions, but when i enter "[COLOR=#000000][FONT=Ubuntu Mono]sudo insmod rtbth.ko" the response i get is: 
[/FONT][/COLOR]"Error: could not load module rtbth.ko: No such file or directory"

Do you know what can I do to enable the Bluetooth? How do I install the bluetooth driver?

Thanks for any help you can provide :)


P.S.: Wireless LAN works perfectly fine from the moment i booted LiveCD to install Ubuntu.

---

### Post by josue-soto1 on 2013-09-23
I have exactly the same problem as 4rielo. WFI working. Bluetooth not detected.
Seems that there are no a fix or solution for this one.. see next bug for further information
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)
If someone else is following I will appreciate a notification once this issue is solved.

Regards
Josue Soto

---

### Post by webmaster2 on 2013-11-06
I have the very same problem. Did that driver thing work? Well, actually I have... 

Bus 003 Device 015: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

on a Dell Laptop

---

### Post by firesock on 2014-04-24
Please look at the last post at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)

It solved my problem with bluetooth

If there is a problem with wifi, look at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

Cheers!

---

### Post by firesock on 2014-04-24
Hi!!
If you want to solve the wifi problem, go to the last post at:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

For bluetooth go to:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1189721)

Cheers!!

---

