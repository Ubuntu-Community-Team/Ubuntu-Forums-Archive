---
title: "Wireless problems with Lenovo 3000 N100"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by primitivling on 2011-11-01
Hey everybody! I have a problem with the wireless on my Lenovo 3000  N100 (it doesn't even find any of the networks). It used to work fine and stopped working after I updated to Ubuntu 10.04. I fixed it back then (but unfortunately don't remember how). I recently kicked off everything and installed Ubuntu 10.10 and (I guess as could be expected) the wireless doesn't work once again. I am pretty bad with Ubuntu/ the terminal but managed to  type in these two commands that people requested for diagnosis in another thread:

                   lshw -C network
    *-network UNCLAIMED     
         description: Network controller
         product: BCM4311 802.11b/g WLAN
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:03:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:d0000000-d0003fff
    *-network
         description: Ethernet interface
         product: RTL-8139/8139C/8139C+
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 1
         bus info: pci@0000:05:01.0
         logical name: eth0
         version: 10
         serial: 00:1b:38:08:80:0b
         size: 10Mbit/s
         capacity: 100Mbit/s
         width: 32 bits
         clock: 33MHz
         capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
         configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64  mingnt=32 multicast=yes port=MII speed=10Mbit/s
         resources: irq:21 ioport:2000(size=256) memory:d0100000-d01000ff


lsmod|grep -i -e b43 -e b43legacy -e ssb -e b44 -e ndiswrapper   did not return anything but went straight to the next line..


Does anyone have an idea what the problem is/ how to fix it (in beginner language)? I'd be very grateful if you had some suggestions how to fix my wireless.

---

### Post by primitivling on 2011-11-01
Oh, also my ethernet outlet has been broken for a while (something mechanical, i think), so updating and stuff would be a little bit difficult. I have other computers around though and could download something that i could transfer with a usb.

---

### Post by wildmanne39 on 2011-11-01
Hi, if you have not installed any other driver this should work the first time, if you have we will have to do some ninja moves on it.

Download the b43 zip file to the flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/*  /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
one line at a time, and it should come on.
Thank you

---

### Post by primitivling on 2011-11-02
i have some trouble with the second line. It says cp: cannot stat `desktop/b43/*': no such file or directory.

was i supposed to fill something in for the *?

thanks and cheers (:

---

### Post by wildmanne39 on 2011-11-02
Hi, just copy and past the command one line at a time, do not type them.

Did you download the zip file and drag it and extract it to the desktop?
Thank you

---

### Post by primitivling on 2011-11-03
Thanks wildmanne! 

somehow i think the commands worked this time and immediately after typing in the last one the wireless networks appeared. There was however a Warning after typing the last command (see screenshot). 

It also doesn't seem like all problems have been resolved. One thing is that I can connect to my wireless but when I try to use this client of my college to connect with firefox it says that there is no configuration for my device (see screenshot). 

The second thing is that as soon as I restart my computer (or close the lid) the wireless stops working again. It works again if I reenter that last modprobe command (the warning appears again). is there no permanent fixup to this problem? I was thinking that maybe something didn't go right because I got that warning..

what do you think?

thanks and cheers (:

---

### Post by wildmanne39 on 2011-11-03
Hi, the first one I know nothing about it has to do with your college and they tend to try to force people to use windows.

To make it work at boot since it is not doing it already run this command and then reboot.
```
sudo su 
echo b43 >> /etc/modules 
exit
```
This is all one command.
Thank you

---

### Post by ememlulu on 2012-11-04
Hi, 
I installed XBMCUBUNTU and have the same problem - NO WIRELESS NETWORK (WIFI dont work...)
Can I do this fix by running the ubuntu desktop from a cd?
and if not, how can i fix it in an xbmcbuntu operatin system??
THANKS!!

---

### Post by wildmanne39 on 2012-11-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.
Thanks

---

### Post by ememlulu on 2012-11-07
Thanks, Will do!
(could "NetWorkManager PLUGIN installation help??)

---

### Post by ememlulu on 2012-11-07
OK I did what you wrote, but how do I get access to the file??
I dont find it in the SYSTEM--->FILE MANEGER

---

### Post by wildmanne39 on 2012-11-07
Hi, it creates a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security, then reply back and attach the netinfo.txt file.

---

### Post by ememlulu on 2012-11-07
there's a problrm uploading a file in the forum so i copied the txt file here:
#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

thanks again for your help!

---

### Post by wildmanne39 on 2012-11-07
Hi, this is the name of the file you need to attach.> netinfo.txt file
Thanks

---

### Post by ememlulu on 2012-11-08
OK I MADE IT!!
I looked through your previous notes  and now the wifi is working!!
HUGE THANKS WILD MAN!!

---

### Post by skellobissis on 2013-01-15
worked like a charm!

---

### Post by balu435 on 2013-01-24
the first time I switched to linux it took me 2 days to get the issues resolved...I installed ubuntu this time followed your instructions and it worked in minutes:) thanks!!

---

### Post by wildmanne39 on 2013-01-26
Your welcome!

---

