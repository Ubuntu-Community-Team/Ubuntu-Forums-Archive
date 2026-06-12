---
title: "Trouble connecting to wifi using terminal"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by shaunybo on 2011-05-03
Hi, im using minimal ubuntu 10.04 and im having trouble connecting to wifi using the terminal. the wifi worked perfectly on the desktop version. 

i followed this guide [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo) and

'/etc/network/interfaces'

looks like 

[IMG]http://i51.tinypic.com/o6lff8.jpg[/IMG]

then i used '/etc/init.d/networking restart' and get this 

[IMG]http://i53.tinypic.com/2eporaq.jpg[/IMG]

now it seems ive disabled wlan0 as $ sudo lshw -C shows

[IMG]http://i52.tinypic.com/24b8buo.jpg[/IMG]

i tried to enable it again by using 'sudo ifup wlan0' but i get a few errors

[IMG]http://i54.tinypic.com/2nu3rkh.jpg[/IMG]

i think the 2nd errors may be because i tried to download another driver for the wireless using 'wget [https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)' and then 'dpkg -i rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb'

really unsure what to do now. any help is appreciated

---

### Post by chili555 on 2011-05-03
Your interface appears to be ra0, not wlan0. Why does it show as disabled? Is the wireless switch on?```
rfkill list all
```

---

### Post by shaunybo on 2011-05-03
oh didnt notice that. it was wlan0, the driver update must have changed it. im able to enable it using 'sudo ifconfig ra0 up' 

is 'rfkill list all' meant to show anything? 

Now i have the wireless enabled what should i be doing to create a connection? this below?

```
sudo nano -w /etc/network/interfaces

auto ra0
iface ra0 inet dhcp
wireless-essid   02wirelessD99D60
wireless-channel 10
wireless-mode    managed
```


i done that and then restarted using 
```
sudo /etc/init.d/networking restart
``` 

but i get the same errors about 'No dhcpoffers recieved' as in my first pic in the first post

---

### Post by josephmills on 2011-05-03
> **shaunybo said:**
> oh didnt notice that. it was wlan0, the driver update must have changed it. im able to enable it using 'sudo ifconfig ra0 up' 

is 'rfkill list all' meant to show anything? 

Now i have the wireless enabled what should i be doing to create a connection? this below?

```
sudo nano -w /etc/network/interfaces

auto ra0
iface ra0 inet dhcp
wireless-essid   02wirelessD99D60
wireless-channel 10
wireless-mode    managed
```


i done that and then restarted using 
```
sudo /etc/init.d/networking restart
``` 

but i get the same errors about 'No dhcpoffers recieved' as in my first pic in the first post
rfkill list all should show you some imporastant info just try ```
rfkill list
```
hows network manager doing?
```

nm-tool

```

---

### Post by shaunybo on 2011-05-03
> **josephmills said:**
> ```
rfkill list
```
doesnt respond at all. do i need to install something to be able to do this?
> **josephmills said:**
> 
hows network manager doing?
```

nm-tool

```

[IMG]http://i54.tinypic.com/v3op61.jpg[/IMG]

---

### Post by chili555 on 2011-05-03
> auto ra0
iface ra0 inet dhcp
wireless-essid   02wirelessD99D60
[COLOR="Red"]wireless-channel 10
wireless-mode    managed[/COLOR]I don't think you need the highlighted parts at all. Is there no encryption on your network? WPA, WEP, Klingon, etc.? You have to account for your key or password here.

---

### Post by shaunybo on 2011-05-04
> **chili555 said:**
> I don't think you need the highlighted parts at all. Is there no encryption on your network? WPA, WEP, Klingon, etc.? You have to account for your key or password here.

I tried it without those lines and it didn't change. No I turn the encryption off encased that was the problem. I turned the encryption back and had the line 'wireless-key s:XXXXXXXX'

---

### Post by shaunybo on 2011-05-04
i was thinking of just starting from scratch and reinstalling. is there anywhere i can find out which ubuntu version is comaptibale so wifi will work out of the box?

---

### Post by chili555 on 2011-05-04
As far as I can see, driver support is not an issue. Please let me see:```
lsmod | grep rt2
sudo ifdown ra0 && sudo ifup ra0
dmesg | grep ra0
```Thanks.

---

### Post by shaunybo on 2011-05-04
i have installed ubuntu minimal 10.10. i thought i might have made things worse by trying several 'fixes' from googling.


```
lsmod | grep rt2
```
[IMG]http://i54.tinypic.com/swbyps.jpg[/IMG]

i then added 
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
```
to /etc/modprobe.d/blacklist.conf but it didnt make a change

```
sudo ifdown wlan0 && sudo ifup wlan0
```

```
dmesg | grep wlan0
```
this didnt work but 'dmesg' did i was able to see the end of it
[IMG]http://i56.tinypic.com/rjjf68.jpg[/IMG]

```
lspci
```
[IMG]http://oi56.tinypic.com/mbkguv.jpg[/IMG]

```
ifconfig
```
[IMG]http://i53.tinypic.com/2lwlj7m.jpg[/IMG]

```
iwconfig
```
[IMG]http://i55.tinypic.com/11cfi3b.jpg[/IMG]

```
lshw -C network
```
[IMG]http://i53.tinypic.com/34pc01x.jpg[/IMG]

```
sudo iwlist scan
```
[IMG]http://i55.tinypic.com/24fahcm.jpg[/IMG]

```
sudo iwconfig wlan0 essid O2wirelessD99D60
sudo iwconfig wlan0 key 554464C4F1
sudo dhclient wlan0
```
[IMG]http://i55.tinypic.com/ev2j2q.jpg[/IMG]
am i typing these in the correct format?



i have installed ubuntu minimal 10.10. i thought i might have made things worse by trying several 'fixes' from googling.

where should i have started to get the wifi working? i installed wireless-tools and network-manager then made sure wlan0 was switched on and then tried to connect to the network. is that right or should there be more steps?

---

### Post by chili555 on 2011-05-04
> where should i start to get the wifi working? I thought we were working on that right now. No?> do i will i need to install network-manager etc?No.> do you still want

Code:

lsmod | grep rt2
sudo ifdown ra0 && sudo ifup ra0
dmesg | grep ra0

Only if you want to try to fix it.

---

### Post by shaunybo on 2011-05-04
sorry i never noticed this reply. i updated my last post with some more information

---

### Post by chili555 on 2011-05-04
Your dmesg and lshw both still show the driver is rt2800pci. Please check your blacklist file and reboot. It ought to show rt2860sta.

Please do:```
sudo iwlist wlan0 scan
```Is the name of your network really 02wirelessD99D60? Please double-check that it's not 2wireD99D60 or some close variation.

Do you have encryption in place now? If so, your interfaces file should include:```
wireless-key 554464C4F1
```The s: is not required; it's not an ASCII key.

When you run:```
lspci -nn
```What is the pci.id for your Ralink device? It will be something like (18e4:23cb). You don't have to do a screenshot, just tell me what it is.

How did it change from ra0 to wlan0? Did you reinstall?

---

### Post by shaunybo on 2011-05-04
> **chili555 said:**
> Your dmesg and lshw both still show the driver is rt2800pci. Please check your blacklist file and reboot. It ought to show rt2860sta.

i didnt blacklist it correctly. its lshw is showing the driver as rt2860 now

> **chili555 said:**
> 
Please do:```
sudo iwlist wlan0 scan
```Is the name of your network really 02wirelessD99D60? Please double-check that it's not 2wireD99D60 or some close variation.


yes it is capital o not zero then 2wirelessD99D60, should i change it to something simpler?

> **chili555 said:**
> 
Do you have encryption in place now? If so, your interfaces file should include:```
wireless-key 554464C4F1
```The s: is not required; it's not an ASCII key.


yes i have that

> **chili555 said:**
> 
When you run:```
lspci -nn
```What is the pci.id for your Ralink device? It will be something like (18e4:23cb). You don't have to do a screenshot, just tell me what it is.


it is (1814:3090)

> **chili555 said:**
> 
How did it change from ra0 to wlan0? Did you reinstall?
yes install 10.10 instead of 10.04

---

### Post by chili555 on 2011-05-04
All sounds good. Now when you do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Does it connect or time out?

---

### Post by shaunybo on 2011-05-04
it still time outs

---

### Post by chili555 on 2011-05-04
And your interfaces file is:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid 02wirelessD99D60
wireless-key 554464C4F1
```Is that correct?

---

### Post by shaunybo on 2011-05-04
yep

---

### Post by chili555 on 2011-05-04
Are there any clues in:```
sudo cat /var/log/syslog | grep wlan
```Do you solemnly swear on Linus Torvalds' own copy of C++ programmer's bible, that the essid and WEP key are verified correct? It is 40/64-bit WEP, correct?

---

### Post by shaunybo on 2011-05-04
> **chili555 said:**
> Are there any clues in:```
sudo cat /var/log/syslog | grep wlan
```Do you solemnly swear on Linus Torvalds' own copy of C++ programmer's bible, that the essid and WEP key are verified correct? It is 40/64-bit WEP, correct?
i get loads of text on screen. i can only see the last page full and its just stuff about dhcpdiscover, no errors. is there a way to export that so i can get the whole of the text?

yes i swear :lol:

/edit

```
there is already a pid file /var/run/dhclient.wlan0.pid with pid 1780
```
is that a problem?

---

### Post by chili555 on 2011-05-04
Please try:```
sudo cat /var/log/syslog | grep wlan > syslog.txt
```In your user directory you will find a file called syslog.txt. Can you transfer it on a USB key?

---

### Post by shaunybo on 2011-05-04
i havent got a gui so can i copy it to the usb using the terminal?

did you see in my last post? 
```
there is already a pid file /var/run/dhclient.wlan0.pid with pid 1780
```
is comming up in the syslog

---

### Post by chili555 on 2011-05-04
USB drives will usually mount in /media. In my case, ```
ls /media
```shows:```
cdrom NEFS
``````
ls /media/NEFS
``` shows an old iso I transferred. Then do:```
sudo cp syslog.txt /media/NEFS
```Of course, substitute your actual location; it's probably different from NEFS. Then unmount the drive:```
sudo umount /media/NEFS
```Now it's safe to remove the drive.

I am shutting down for tonight. See you tomorrow.

---

### Post by shaunybo on 2011-05-05
hi chilli thanks for your help btw. done that 
 
```
May  4 20:45:15 xbmc kernel: [  157.031353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:07:58 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:07:58 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:08:11 xbmc kernel: [  420.363331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:15:06 xbmc kernel: [  108.959340] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:15:06 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:15:06 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:15:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:15:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 22:15:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  4 22:15:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  4 22:15:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:19:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:19:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:19:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:19:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  4 22:19:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 22:20:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:20:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:20:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  4 22:20:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  4 22:20:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  4 22:21:20 xbmc kernel: [   10.102992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:21:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:21:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:21:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:21:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  4 22:21:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  4 22:21:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:21:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  4 22:21:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:22:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:23:06 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  4 22:25:55 xbmc kernel: [   98.443318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:26:37 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:26:37 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:40:47 xbmc kernel: [   51.674977] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:04:03 xbmc kernel: [  911.499343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:09:54 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:09:54 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:10:05 xbmc kernel: [   80.023325] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:36:55 xbmc init: network-interface (wlan0) pre-start process (897) terminated with status 1
May  4 23:36:55 xbmc init: network-interface (wlan0) post-stop process (902) terminated with status 1
May  4 23:38:12 xbmc kernel: [   85.543319] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:39:16 xbmc init: network-interface (wlan0) pre-start process (929) terminated with status 1
May  4 23:39:16 xbmc init: network-interface (wlan0) post-stop process (931) terminated with status 1
May  4 23:40:24 xbmc kernel: [   76.387320] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:45:34 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:45:34 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:45:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 23:45:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 23:45:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  4 23:46:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  4 23:46:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 23:48:20 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  4 23:51:20 xbmc kernel: [   80.891328] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:00:26 xbmc kernel: [  128.235334] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:01:09 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:01:09 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:02:56 xbmc kernel: [   61.326983] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:10:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:10:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:10:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 00:10:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 00:10:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 00:11:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 00:11:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 00:11:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 00:18:04 xbmc NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:18:04 xbmc NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): now managed
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): bringing up device.
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): preparing device.
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:18:05 xbmc kernel: [   18.291013] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:46:16 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:46:16 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): now managed
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): bringing up device.
May  5 00:46:18 xbmc kernel: [   14.714990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): preparing device.
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:46:18 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:46:18 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:49:21 xbmc NetworkManager[1000]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:49:21 xbmc NetworkManager[1000]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): now managed
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): bringing up device.
May  5 00:49:23 xbmc kernel: [   14.126979] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): preparing device.
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:56:28 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:56:28 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:56:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 00:56:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 00:56:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 00:56:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 00:56:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 00:57:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 00:57:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 00:58:26 xbmc kernel: [  556.640130] wlan0: authenticate with 00:1f:9f:ed:57:1f (try 1)
May  5 00:58:26 xbmc kernel: [  556.641973] wlan0: authenticated
May  5 00:58:26 xbmc kernel: [  556.656152] wlan0: associate with 00:1f:9f:ed:57:1f (try 1)
May  5 00:58:26 xbmc kernel: [  556.659538] wlan0: RX AssocResp from 00:1f:9f:ed:57:1f (capab=0x11 status=0 aid=1)
May  5 00:58:26 xbmc kernel: [  556.659548] wlan0: associated
May  5 00:58:26 xbmc kernel: [  556.660863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  5 00:58:26 xbmc kernel: [  556.662111] wlan0: deauthenticating from 00:1f:9f:ed:57:1f by local choice (reason=3)
May  5 00:58:36 xbmc kernel: [  567.160091] wlan0: no IPv6 routers present
May  5 01:01:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:01:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:01:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:01:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:01:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:01:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 01:02:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:02:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:02:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:02:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:02:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:02:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:03:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:03:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:03:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 01:03:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:07:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:07:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:07:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:07:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:08:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:08:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:08:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:15:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:15:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:15:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:15:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:15:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 01:16:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:21:34 xbmc kernel: [   12.075164] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): now managed
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): preparing device.
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:21:34 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:21:34 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:21:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:21:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:21:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:21:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:22:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:22:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:29:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:29:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:29:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 01:29:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:29:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:29:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:30:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:33:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:33:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:33:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:33:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:33:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 01:34:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:34:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:39:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:39:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:39:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:39:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:40:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:40:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:40:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:41:00 xbmc NetworkManager[995]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:41:01 xbmc NetworkManager[995]: <error> [1304556061.26917] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): now managed
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): preparing device.
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:41:01 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:41:01 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:41:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:41:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:41:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:41:11 xbmc kernel: [   22.608015] wlan0: no IPv6 routers present
May  5 01:41:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:41:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:41:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 01:45:47 xbmc NetworkManager[996]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:45:47 xbmc NetworkManager[996]: <error> [1304556347.115412] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): now managed
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): preparing device.
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:45:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:45:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:45:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:45:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:45:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 01:45:57 xbmc kernel: [   22.272092] wlan0: no IPv6 routers present
May  5 01:46:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 01:46:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 01:46:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:50:35 xbmc NetworkManager[983]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:50:35 xbmc NetworkManager[983]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:50:36 xbmc NetworkManager[983]: <error> [1304556636.4763] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): now managed
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): bringing up device.
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): preparing device.
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:50:46 xbmc kernel: [   22.736007] wlan0: no IPv6 routers present
May  5 01:53:32 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:53:32 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:53:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:53:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:53:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:53:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:54:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:54:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:58:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:58:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:58:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:58:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:58:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:58:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:58:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:59:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:59:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:01:05 xbmc NetworkManager[993]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 02:01:05 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:05 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:01:05 xbmc NetworkManager[993]: <error> [1304557265.166620] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): now managed
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): preparing device.
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): deactivating device (reason: 2).
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 02:01:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:01:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:15 xbmc kernel: [   22.288072] wlan0: no IPv6 routers present
May  5 02:01:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:01:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 02:01:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:01:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:01:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:01:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:58 xbmc kernel: [   65.192065] wlan0: no IPv6 routers present
May  5 02:02:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 02:02:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:02:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:02:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 02:03:50 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1668
May  5 02:03:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:03:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:03:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:04:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:04:00 xbmc kernel: [  187.784119] wlan0: no IPv6 routers present
May  5 02:04:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 02:04:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:04:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:05:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:05:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:05:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:06:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:06:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:06:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:09:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:09:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:09:49 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:09:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:10:12 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:10:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:13:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:13:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:13:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:13:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:13:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:13:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:13:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:14:20 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1740
May  5 02:14:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:14:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:14:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:14:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:14:31 xbmc kernel: [  818.544102] wlan0: no IPv6 routers present
May  5 02:14:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:14:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:14:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:15:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 02:15:54 xbmc NetworkManager[1037]: <error> [1304558154.240050] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): now managed
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): preparing device.
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): deactivating device (reason: 2).
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 02:15:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:16:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:16:04 xbmc kernel: [   22.064073] wlan0: no IPv6 routers present
May  5 02:16:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:16:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:16:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:16:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:16:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:16:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:16:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:17:01 xbmc kernel: [   79.248090] wlan0: no IPv6 routers present
May  5 02:17:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:17:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:17:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 02:17:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:24:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:24:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:24:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:24:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:24:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:24:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:24:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:24:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:24:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:24:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:25:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:25:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:28:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:28:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:28:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:28:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:28:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 02:28:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:29:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:29:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:29:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:29:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:29:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:29:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:29:44 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1685
May  5 02:29:44 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:29:44 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:29:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:29:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:29:54 xbmc kernel: [  852.608095] wlan0: no IPv6 routers present
May  5 02:29:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:30:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:30:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:30:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:32:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:32:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:32:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:32:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:33:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:33:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:33:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:33:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:33:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:34:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:34:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:34:30 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1780
May  5 02:34:30 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:34:30 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:34:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:34:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:34:41 xbmc kernel: [ 1139.264099] wlan0: no IPv6 routers present
May  5 02:34:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:35:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:35:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:35:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:38:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:38:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:38:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:38:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:38:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:38:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:39:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:39:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:39:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 02:40:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:40:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:40:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:40:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:40:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:40:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:41:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:43:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:43:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:43:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:44:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:44:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:44:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:45:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:45:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:45:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:45:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:45:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:46:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:46:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:46:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  5 02:46:23 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1858
May  5 02:46:23 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:46:23 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:46:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:46:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:46:34 xbmc kernel: [ 1852.048092] wlan0: no IPv6 routers present
May  5 02:46:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:47:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 02:47:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 23:18:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:18:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:18:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:18:50 xbmc NetworkManager[986]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 23:18:50 xbmc NetworkManager[986]: <error> [1304633930.295417] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): now managed
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): preparing device.
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): deactivating device (reason: 2).
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 23:18:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:18:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:19:00 xbmc kernel: [   22.112005] wlan0: no IPv6 routers present
May  5 23:19:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 23:19:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:19:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 23:19:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 23:19:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1

```

---

### Post by shaunybo on 2011-05-06
just tried 11.04 live and the wifi worked when using that. would it be worth trying 11.04 minimal? if the wifi is working using the live version should i expect it to work using the minimal version

---

### Post by chili555 on 2011-05-06
> [COLOR="Red"]NetworkManager[/COLOR][1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)I thought you were running minimal without Network Manager.

Manual methods, that is /etc/network/interfaces and NM conflict and fight each other. Please pick one or the other; not both.

---

### Post by shaunybo on 2011-05-07
oh right. i thought i needed that. removed network manager and still getting the same

---

### Post by chili555 on 2011-05-07
> **shaunybo said:**
> oh right. i thought i needed that. removed network manager and still getting the sameDid you reboot after you removed NM? What does syslog look like now?

---

### Post by shaunybo on 2011-05-07
yea i rebooted. syslog is below

```
May  4 20:45:15 xbmc kernel: [  157.031353] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:07:58 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:07:58 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:08:11 xbmc kernel: [  420.363331] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:15:06 xbmc kernel: [  108.959340] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:15:06 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:15:06 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:15:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:15:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 22:15:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  4 22:15:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  4 22:15:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:19:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:19:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:19:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:19:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  4 22:19:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 22:20:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:20:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:20:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  4 22:20:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  4 22:20:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  4 22:21:20 xbmc kernel: [   10.102992] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:21:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:21:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:21:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 22:21:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  4 22:21:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  4 22:21:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 22:21:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  4 22:21:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:22:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  4 22:23:06 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  4 22:25:55 xbmc kernel: [   98.443318] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 22:26:37 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:26:37 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 22:40:47 xbmc kernel: [   51.674977] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:04:03 xbmc kernel: [  911.499343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:09:54 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:09:54 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:10:05 xbmc kernel: [   80.023325] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:36:55 xbmc init: network-interface (wlan0) pre-start process (897) terminated with status 1
May  4 23:36:55 xbmc init: network-interface (wlan0) post-stop process (902) terminated with status 1
May  4 23:38:12 xbmc kernel: [   85.543319] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:39:16 xbmc init: network-interface (wlan0) pre-start process (929) terminated with status 1
May  4 23:39:16 xbmc init: network-interface (wlan0) post-stop process (931) terminated with status 1
May  4 23:40:24 xbmc kernel: [   76.387320] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  4 23:45:34 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:45:34 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  4 23:45:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  4 23:45:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  4 23:45:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  4 23:46:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  4 23:46:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  4 23:48:20 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  4 23:51:20 xbmc kernel: [   80.891328] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:00:26 xbmc kernel: [  128.235334] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:01:09 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:01:09 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:02:56 xbmc kernel: [   61.326983] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:10:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:10:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:10:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 00:10:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 00:10:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 00:11:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 00:11:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 00:11:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 00:18:04 xbmc NetworkManager[1069]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:18:04 xbmc NetworkManager[1069]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): now managed
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:18:04 xbmc NetworkManager[1069]: <info> (wlan0): bringing up device.
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): preparing device.
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:18:05 xbmc kernel: [   18.291013] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:18:05 xbmc NetworkManager[1069]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:46:16 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:46:16 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): now managed
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:46:16 xbmc NetworkManager[976]: <info> (wlan0): bringing up device.
May  5 00:46:18 xbmc kernel: [   14.714990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): preparing device.
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:46:18 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:46:18 xbmc NetworkManager[976]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:46:18 xbmc NetworkManager[976]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:49:21 xbmc NetworkManager[1000]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 00:49:21 xbmc NetworkManager[1000]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): now managed
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 00:49:21 xbmc NetworkManager[1000]: <info> (wlan0): bringing up device.
May  5 00:49:23 xbmc kernel: [   14.126979] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): preparing device.
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): deactivating device (reason: 2).
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 00:49:23 xbmc NetworkManager[1000]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 00:56:28 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:56:28 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 00:56:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 00:56:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 00:56:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 00:56:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 00:56:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 00:57:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 00:57:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 00:58:26 xbmc kernel: [  556.640130] wlan0: authenticate with 00:1f:9f:ed:57:1f (try 1)
May  5 00:58:26 xbmc kernel: [  556.641973] wlan0: authenticated
May  5 00:58:26 xbmc kernel: [  556.656152] wlan0: associate with 00:1f:9f:ed:57:1f (try 1)
May  5 00:58:26 xbmc kernel: [  556.659538] wlan0: RX AssocResp from 00:1f:9f:ed:57:1f (capab=0x11 status=0 aid=1)
May  5 00:58:26 xbmc kernel: [  556.659548] wlan0: associated
May  5 00:58:26 xbmc kernel: [  556.660863] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  5 00:58:26 xbmc kernel: [  556.662111] wlan0: deauthenticating from 00:1f:9f:ed:57:1f by local choice (reason=3)
May  5 00:58:36 xbmc kernel: [  567.160091] wlan0: no IPv6 routers present
May  5 01:01:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:01:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:01:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:01:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:01:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:01:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 01:02:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:02:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:02:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:02:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:02:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:02:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:03:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:03:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:03:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 01:03:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:07:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:07:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:07:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:07:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:08:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:08:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:08:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:15:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:15:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:15:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:15:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:15:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 01:16:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:21:34 xbmc kernel: [   12.075164] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:21:34 xbmc NetworkManager[1020]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2800pci' ifindex: 3)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): now managed
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): preparing device.
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:21:34 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:21:34 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:21:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:21:34 xbmc NetworkManager[1020]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:21:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:21:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:21:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:22:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:22:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:29:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:29:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:29:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 01:29:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:29:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:29:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:30:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:33:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:33:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:33:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:33:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:33:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 01:34:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:34:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:39:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:39:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:39:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:39:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:40:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 01:40:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:40:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:41:00 xbmc NetworkManager[995]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:41:00 xbmc NetworkManager[995]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:41:01 xbmc NetworkManager[995]: <error> [1304556061.26917] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): now managed
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): preparing device.
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:41:01 xbmc NetworkManager[995]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:41:01 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:41:01 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:41:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:41:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 01:41:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:41:11 xbmc kernel: [   22.608015] wlan0: no IPv6 routers present
May  5 01:41:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:41:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:41:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 01:45:47 xbmc NetworkManager[996]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:45:47 xbmc NetworkManager[996]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:45:47 xbmc NetworkManager[996]: <error> [1304556347.115412] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): now managed
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): preparing device.
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:45:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:45:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:45:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:45:47 xbmc NetworkManager[996]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:45:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:45:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 01:45:57 xbmc kernel: [   22.272092] wlan0: no IPv6 routers present
May  5 01:46:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 01:46:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 01:46:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 01:50:35 xbmc NetworkManager[983]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 01:50:35 xbmc NetworkManager[983]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 01:50:36 xbmc NetworkManager[983]: <error> [1304556636.4763] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): now managed
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): bringing up device.
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): preparing device.
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): deactivating device (reason: 2).
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 01:50:36 xbmc NetworkManager[983]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 01:50:46 xbmc kernel: [   22.736007] wlan0: no IPv6 routers present
May  5 01:53:32 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:53:32 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 01:53:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:53:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:53:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:53:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 01:54:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 01:54:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 01:58:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:58:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 01:58:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 01:58:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:58:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 01:58:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 01:58:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 01:59:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 01:59:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:01:05 xbmc NetworkManager[993]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 02:01:05 xbmc NetworkManager[993]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 02:01:05 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:05 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:01:05 xbmc NetworkManager[993]: <error> [1304557265.166620] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): now managed
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): preparing device.
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): deactivating device (reason: 2).
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 02:01:05 xbmc NetworkManager[993]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 02:01:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:01:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:15 xbmc kernel: [   22.288072] wlan0: no IPv6 routers present
May  5 02:01:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:01:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 02:01:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:01:47 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:01:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:01:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:01:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:01:58 xbmc kernel: [   65.192065] wlan0: no IPv6 routers present
May  5 02:02:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 02:02:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:02:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:02:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 02:03:50 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1668
May  5 02:03:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:03:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:03:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:03:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:04:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:04:00 xbmc kernel: [  187.784119] wlan0: no IPv6 routers present
May  5 02:04:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 02:04:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:04:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:05:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:05:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:05:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:06:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:06:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:06:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:09:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:09:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:09:49 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:09:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:10:12 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:10:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:13:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:13:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:13:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:13:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:13:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:13:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:13:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:14:20 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1740
May  5 02:14:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:14:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:14:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:14:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:14:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:14:31 xbmc kernel: [  818.544102] wlan0: no IPv6 routers present
May  5 02:14:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:14:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:14:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:15:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 02:15:54 xbmc NetworkManager[1037]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 02:15:54 xbmc NetworkManager[1037]: <error> [1304558154.240050] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): now managed
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): preparing device.
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): deactivating device (reason: 2).
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 02:15:54 xbmc NetworkManager[1037]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 02:15:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:16:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:16:04 xbmc kernel: [   22.064073] wlan0: no IPv6 routers present
May  5 02:16:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:16:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:16:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:16:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:16:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:16:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:16:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:16:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:17:01 xbmc kernel: [   79.248090] wlan0: no IPv6 routers present
May  5 02:17:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:17:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:17:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  5 02:17:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:24:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:24:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:24:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:24:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:24:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:24:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:24:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:24:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:24:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:24:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:24:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:25:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:25:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:28:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:28:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:28:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:28:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:28:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  5 02:28:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:29:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:29:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:29:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:29:16 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:29:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:29:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:29:44 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1685
May  5 02:29:44 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:29:44 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:29:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:29:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:29:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:29:54 xbmc kernel: [  852.608095] wlan0: no IPv6 routers present
May  5 02:29:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:30:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:30:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 02:30:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:32:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:32:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:32:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:32:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:33:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:33:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:33:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:33:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:33:41 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:33:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:34:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:34:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:34:30 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1780
May  5 02:34:30 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:34:30 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:34:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:34:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:34:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:34:41 xbmc kernel: [ 1139.264099] wlan0: no IPv6 routers present
May  5 02:34:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 02:35:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:35:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:35:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 02:38:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:38:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 02:38:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:38:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:38:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:38:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:39:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 02:39:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 02:39:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  5 02:40:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:40:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:40:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:40:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:40:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:40:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:41:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:43:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:43:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:43:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:44:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 02:44:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:44:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 02:45:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:45:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 02:45:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  5 02:45:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 02:45:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:46:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 02:46:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:46:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  5 02:46:23 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1858
May  5 02:46:23 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  5 02:46:23 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 02:46:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 02:46:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 02:46:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 02:46:34 xbmc kernel: [ 1852.048092] wlan0: no IPv6 routers present
May  5 02:46:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 02:47:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 02:47:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  5 23:18:50 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:18:50 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:18:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:18:50 xbmc NetworkManager[986]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 23:18:50 xbmc NetworkManager[986]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 23:18:50 xbmc NetworkManager[986]: <error> [1304633930.295417] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): now managed
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): preparing device.
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): deactivating device (reason: 2).
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 23:18:50 xbmc NetworkManager[986]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 23:18:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:18:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:19:00 xbmc kernel: [   22.112005] wlan0: no IPv6 routers present
May  5 23:19:05 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 23:19:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:19:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  5 23:19:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 23:19:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  5 23:23:43 xbmc NetworkManager[1015]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 23:23:44 xbmc NetworkManager[1015]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 23:23:44 xbmc NetworkManager[1015]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 23:23:44 xbmc NetworkManager[1015]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 23:23:44 xbmc NetworkManager[1015]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 23:23:44 xbmc NetworkManager[1015]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 23:23:44 xbmc NetworkManager[1015]: <error> [1304634224.59434] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): now managed
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): preparing device.
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): deactivating device (reason: 2).
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 23:23:44 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:23:44 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:23:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:23:44 xbmc NetworkManager[1015]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 23:23:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:23:54 xbmc kernel: [   22.112131] wlan0: no IPv6 routers present
May  5 23:23:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:24:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 23:24:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  5 23:24:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  5 23:29:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:29:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:29:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 23:29:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:29:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 23:29:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:30:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:35:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:35:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:35:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  5 23:35:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 23:36:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 23:36:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 23:36:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:36:37 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  5 23:38:45 xbmc NetworkManager[1041]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  5 23:38:45 xbmc NetworkManager[1041]: <error> [1304635125.57666] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): now managed
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): preparing device.
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): deactivating device (reason: 2).
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): supplicant manager state:  down -> idle
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  5 23:38:45 xbmc NetworkManager[1041]: <info> (wlan0): supplicant interface state:  starting -> ready
May  5 23:38:55 xbmc kernel: [   22.216021] wlan0: no IPv6 routers present
May  5 23:41:32 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:41:32 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:41:32 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:41:32 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  5 23:41:32 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:41:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:41:42 xbmc kernel: [  189.280099] wlan0: no IPv6 routers present
May  5 23:41:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 23:41:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:42:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  5 23:42:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 23:49:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:49:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  5 23:49:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  5 23:49:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  5 23:49:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  5 23:49:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  5 23:49:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:57:08 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  5 23:57:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  5 23:57:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  5 23:57:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  5 23:57:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  5 23:57:59 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:01:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:01:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 00:01:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 00:01:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  6 00:02:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  6 00:02:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:08:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:08:55 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:09:02 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:09:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
May  6 00:09:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 00:09:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 00:14:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:14:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 00:14:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  6 00:15:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:15:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  6 00:15:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  6 00:15:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  6 00:21:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:21:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 00:21:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:21:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  6 00:21:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:21:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 00:22:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
May  6 00:28:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:28:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 00:28:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 00:28:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  6 00:29:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:29:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 00:29:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  6 00:36:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:36:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 00:36:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  6 00:36:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 00:37:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 00:37:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  6 00:37:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 00:41:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:41:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 00:41:12 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 00:41:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 00:41:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 00:41:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 00:48:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:48:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:48:28 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  6 00:48:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  6 00:48:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  6 00:49:12 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:53:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:53:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:53:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 00:54:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 00:54:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 00:54:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 00:58:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 00:58:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 00:58:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 00:58:31 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  6 00:58:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  6 01:01:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 01:01:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 01:01:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 01:02:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 01:02:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 01:02:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 01:02:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 01:02:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  6 01:07:44 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 01:07:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 01:07:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 01:08:00 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 01:08:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  6 01:08:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 01:08:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 01:08:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 01:13:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 01:14:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 01:14:06 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 01:14:19 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 01:14:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  6 01:14:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 20:26:14 xbmc NetworkManager[991]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  6 20:26:14 xbmc NetworkManager[991]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  6 20:26:14 xbmc NetworkManager[991]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  6 20:26:14 xbmc NetworkManager[991]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  6 20:26:14 xbmc NetworkManager[991]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  6 20:26:14 xbmc NetworkManager[991]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  6 20:26:14 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:26:14 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:26:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 20:26:14 xbmc NetworkManager[991]: <error> [1304709974.81045] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): now managed
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): preparing device.
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): deactivating device (reason: 2).
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): supplicant manager state:  down -> idle
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  6 20:26:14 xbmc NetworkManager[991]: <info> (wlan0): supplicant interface state:  starting -> ready
May  6 20:26:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 20:26:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 20:26:24 xbmc kernel: [   22.528308] wlan0: no IPv6 routers present
May  6 20:26:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  6 20:26:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 20:26:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
May  6 20:27:07 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:27:07 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:27:07 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  6 20:27:07 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:27:07 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  6 20:27:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 20:27:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 20:27:15 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 20:27:17 xbmc kernel: [   75.936107] wlan0: no IPv6 routers present
May  6 20:27:22 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 20:27:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  6 20:27:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  6 23:11:04 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  6 23:11:04 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  6 23:11:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPluginIfupdown: guessed connection type (wlan0) = 802-11-wireless
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPlugin-Ifupdown: update_connection_setting_from_if_block: name:wlan0, type:802-11-wireless, id:Ifupdown (wlan0), uuid: 5391eba4-6426-faca-338e-5828034ff9d1
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPlugin-Ifupdown: update wireless settings (wlan0).
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPlugin-Ifupdown: update wireless security settings (wlan0).
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  6 23:11:04 xbmc NetworkManager[1002]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  6 23:11:04 xbmc NetworkManager[1002]: <error> [1304719864.399285] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): now managed
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): preparing device.
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): deactivating device (reason: 2).
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): supplicant manager state:  down -> idle
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  6 23:11:04 xbmc NetworkManager[1002]: <info> (wlan0): supplicant interface state:  starting -> ready
May  6 23:11:07 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:11:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:11:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 23:11:14 xbmc kernel: [   22.224007] wlan0: no IPv6 routers present
May  6 23:11:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
May  6 23:11:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  6 23:11:47 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 23:12:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 23:14:14 xbmc NetworkManager[985]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  6 23:14:14 xbmc NetworkManager[985]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  6 23:14:15 xbmc NetworkManager[985]: <error> [1304720055.3317] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): now managed
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): bringing up device.
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): preparing device.
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): deactivating device (reason: 2).
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): supplicant manager state:  down -> idle
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  6 23:14:15 xbmc NetworkManager[985]: <info> (wlan0): supplicant interface state:  starting -> ready
May  6 23:14:25 xbmc kernel: [   22.688029] wlan0: no IPv6 routers present
May  6 23:22:43 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  6 23:22:43 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  6 23:22:43 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:22:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 23:22:50 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 23:23:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  6 23:23:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  6 23:23:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 23:23:40 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 23:28:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:28:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 23:28:56 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  6 23:29:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 23:29:17 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
May  6 23:29:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  6 23:36:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:36:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 23:36:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  6 23:36:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  6 23:37:01 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  6 23:37:13 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  6 23:37:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  6 23:41:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  6 23:41:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  6 23:41:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
May  6 23:42:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  6 23:42:09 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  6 23:42:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  6 23:42:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  7 14:08:57 xbmc NetworkManager[990]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0)
May  7 14:08:57 xbmc NetworkManager[990]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May  7 14:08:57 xbmc NetworkManager[990]: <error> [1304773737.369475] [nm-device-wifi.c:3095] real_update_permanent_hw_address(): (wlan0): unable to read permanent MAC address (error 95)
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): new 802.11 WiFi device (driver: 'rt2860' ifindex: 3)
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): now managed
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): bringing up device.
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): preparing device.
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): deactivating device (reason: 2).
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): reset MAC address to 00:00:00:00:00:00
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): supplicant manager state:  down -> idle
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): device state change: 2 -> 3 (reason 0)
May  7 14:08:57 xbmc NetworkManager[990]: <info> (wlan0): supplicant interface state:  starting -> ready
May  7 14:09:08 xbmc kernel: [   23.096035] wlan0: no IPv6 routers present
May  7 14:12:33 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:12:33 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:12:33 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 14:12:36 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 14:12:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 14:12:41 xbmc kernel: [   21.768012] wlan0: no IPv6 routers present
May  7 14:12:46 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  7 14:12:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 14:13:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  7 14:13:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
May  7 14:13:30 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  7 14:13:54 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1557
May  7 14:13:54 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:13:54 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:13:54 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:13:54 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:13:54 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 14:13:57 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  7 14:14:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 14:14:04 xbmc kernel: [  104.864099] wlan0: no IPv6 routers present
May  7 14:14:11 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  7 14:14:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  7 14:14:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
May  7 14:14:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  7 14:15:18 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1628
May  7 14:15:18 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:15:18 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:15:18 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:15:18 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:15:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 14:15:21 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
May  7 14:15:25 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 14:58:20 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:58:20 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 14:58:20 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 14:58:23 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
May  7 14:58:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  7 14:58:31 xbmc kernel: [   21.976026] wlan0: no IPv6 routers present
May  7 14:58:39 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
May  7 14:58:53 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  7 14:59:04 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
May  7 14:59:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 15:05:24 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 15:05:27 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 15:05:35 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  7 15:05:48 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  7 15:06:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
May  7 15:06:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 15:07:23 xbmc dhclient: receive_packet failed on wlan0: Network is down
May  7 15:07:42 xbmc dhclient: There is already a pid file /var/run/dhclient.wlan0.pid with pid 1557
May  7 15:07:42 xbmc dhclient: Listening on LPF/wlan0/1c:65:9d:2c:d0:04
May  7 15:07:42 xbmc dhclient: Sending on   LPF/wlan0/1c:65:9d:2c:d0:04
May  7 15:07:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
May  7 15:07:45 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 15:07:52 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  7 15:07:53 xbmc kernel: [  583.952092] wlan0: no IPv6 routers present
May  7 15:08:03 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  7 15:08:14 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
May  7 15:08:26 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 15:08:34 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 15:08:42 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
May  7 15:13:10 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
May  7 15:13:17 xbmc kernel: [   21.848044] wlan0: no IPv6 routers present
May  7 15:13:18 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
May  7 15:13:29 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
May  7 15:13:38 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
May  7 15:13:51 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
May  7 15:13:58 xbmc dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8

```

---

### Post by chili555 on 2011-05-07
> new 802.11 WiFi device (driver: '[COLOR="Red"]rt2800pci[/COLOR]' ifindex: 3)I do not like this at all.

Please post:```
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by shaunybo on 2011-05-07
```
rt2860sta             504366  1
crc_ccitt               1351  1  rt2860sta
```

---

### Post by chili555 on 2011-05-07
> **shaunybo said:**
> ```
rt2860sta             504366  1
crc_ccitt               1351  1  rt2860sta
```Ahh! Perfect.

Please post:```
sudo iwlist wlan0 scan
```Thanks.

---

### Post by shaunybo on 2011-05-07
```

wlan0   scan completed :
        Cell 01 - Address: 00:1F:9F:ED:57:1F
                  Protocol:802.11b/g
                  ESSID:"wireless"
                  Mode:Managed
                  Channel:9
                  Quality 90/100 signal level:-55dBm Noise level:- 83 dBm
Encryption key:on
bit Rates:54 Mb/s
```

---

### Post by chili555 on 2011-05-07
> Cell 01 - Address: 00:1F:9F:ED:57:1F
                  Protocol:802.11b/g
                  ESSID:"[COLOR="Red"]wireless[/COLOR]"
                  Mode:Managed
                  Channel:9
                  Quality 90/100 signal level:-55dBm Noise level:- 83 dBm
Encryption key:on
bit Rates:54 Mb/sIt looks like your ESSID is wireless, and not 02wirelessD99D60. Would you change your interfaces file and try again?```
sudo ifdown wlan0 && sudo ifup wlan0
```Also, originally in the interfaces file, you specified channel 10, this appears to be on channel 9.

---

### Post by shaunybo on 2011-05-07
> **chili555 said:**
> It looks like your ESSID is wireless, and not 02wirelessD99D60. Would you change your interfaces file and try again?```
sudo ifdown wlan0 && sudo ifup wlan0
```Also, originally in the interfaces file, you specified channel 10, this appears to be on channel 9.

oh yes, i changed them and changed the interfaces file aswell. should have stated that.

---

### Post by chili555 on 2011-05-07
Please show me:```
cat /etc/network/interfaces
```

---

### Post by shaunybo on 2011-05-07
```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid wireless
wireless-key 1234567890
```

i also changed the WEP key to something easier to input
Are wireless-mode and wireless-channel important?

---

### Post by chili555 on 2011-05-07
> Are wireless-mode and wireless-channel important?Not really. If your card starts out in the Managed mode, the card and the router should negotiate everything between themselves. Please run:```
sudo ifdown wlan0 && sudo ifup wlan0
```Does it connect or time out?

Many routers can do WEP encryption in either Open mode or Shared Key. Are you certain yours is set to Open?

---

### Post by shaunybo on 2011-05-07
times out still.

Not sure is this on the router settings? or something on the computer

---

### Post by chili555 on 2011-05-07
If the router's WEP setting is Open, your interfaces file is correct. If it is set to Shared Key, the interfaces file should be:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wireless-essid wireless
wireless-key 1234567890 restricted
```Please check the router.

---

### Post by shaunybo on 2011-05-07
ah you genius. its now working \\:D/ 

Thank you so much chili and sorry for wasting your time for such a small error.

---

### Post by chili555 on 2011-05-07
No problems; I'm just glad it's working. Happy to help.

---

