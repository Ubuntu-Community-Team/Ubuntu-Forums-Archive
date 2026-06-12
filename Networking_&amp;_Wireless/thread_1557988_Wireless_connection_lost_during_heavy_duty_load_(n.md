---
title: "Wireless connection lost during heavy duty load (ndiswrapper)"
date: 2010-08-21
forum: Networking &amp; Wireless
---

### Post by KeyserSosa on 2010-08-21
I constantly loose my wireless internet connection when doing heavy duty networking, e.g. downloading torrents, transfer files with samba, etc. I have a Samsung Q320 laptop with Ubuntu 10.04 (32 bit) using ndiswrapper with the net819xp driver, which works perfectly when I browse webpages and other "simple" things, but as soon as I start downloading at max speed for few minutes (this varies) the connection is lost, even though network-manager still displays the "connected" symbol. At this time I cannot even access the router. Other computers running Windows on this network does not have any problems.

If I reboot or re-install the net819xp driver in ndiswrapper the connection is regained, but is lost again after a few minutes of downloading. This is very frustrating because both network-manager and ndiswrapper seem to think that the connection is actually working.

Is this a known bug? If not, then please help me debug this problem. Any help will be deeply appreciated!

```

$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net819xp : driver installed
    device (10EC:8192) present (alternate driver: r8192_pci)

``````

$ cat /etc/modprobe.d/blacklist.conf | grep r8192_pci
blacklist r8192_pci

``````

$ lspci | grep Realtek
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

``````

$ lsmod | grep ndiswrapper
ndiswrapper           184677  0 

``````

$ dmesg | grep ndiswrapper
[   15.613396] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   16.999523] ndiswrapper: driver net819xp (Realtek Semiconductor Corp.,07/09/2009,1677.1.0709.2009) loaded
[   16.999787] ndiswrapper 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.000201] ndiswrapper 0000:02:00.0: setting latency timer to 64
[   17.099922] ndiswrapper: using IRQ 16
[   17.752189] usbcore: registered new interface driver ndiswrapper
[   38.263477] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[  215.861686] ndiswrapper (iw_set_auth:1602): invalid cmd 12

```

---

### Post by Shmantiv_Radio on 2011-02-26
I'm having exactly the same problem :( 

Were you getting this error message in the log viewer?

```
ndiswrapper (iw_set_auth:1602): invalid cmd 12
```

---

### Post by Shmantiv_Radio on 2011-03-02
Bump

---

### Post by bkratz on 2011-03-02
I thought this all disappeared about a year ago, guess I was wrong!

[http://georgia.ubuntuforums.org/showthread.php?t=1343847](http://georgia.ubuntuforums.org/showthread.php?t=1343847)

---

### Post by mike1312 on 2011-06-28
I've got the same problem with 11.04 on asus k50in laptop, but none of lines in dmesg output like said in the thread from the previos post.

---

### Post by mike1312 on 2011-06-29
I used wpa_supplicant for the WPA2 encrypted connection and this helped. Now connection is stable. 
Instructions are [here]("http://www.pantz.org/software/wpa_supplicant/wirelesswpa2andlinux.html") on the internet.

Here is my version of how to do this.

First take off the wireless networks tick from your network manager applet.
Then output of this command
```
wpa_passphrase youressid yourpassword
```you should save in a file, for example in   /etc/wpa_supplicant/wpa_supplicant.conf .
Next you find which channel is used by your access point with
```
sudo iwlist scan
```In my case it's channel 1.
Now you should save this script
```
#!/bin/sh
pkill wpa_supplicant
ifconfig wlan0 down
ifconfig wlan0 up
echo "wlan up"
iwconfig wlan0 essid "pucca" channel 1
echo "essid"
wpa_supplicant -B -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
echo "wpa key"
dhclient wlan0
echo "dhcp"
```in a file, for example wireless__. 
Replace wlan0 with your wireless interface, pucca with your access point essid and the number of channel.
Connect with
```
sudo sh wireless__
```Well done :)

---

