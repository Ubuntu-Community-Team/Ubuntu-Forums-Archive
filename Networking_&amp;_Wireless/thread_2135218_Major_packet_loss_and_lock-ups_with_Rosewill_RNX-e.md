---
title: "Major packet loss and lock-ups with Rosewill RNX-easyN1"
date: 2013-04-13
forum: Networking &amp; Wireless
---

### Post by Gnobody on 2013-04-13
I'm running 64-bit 12.10 and I've followed older threads on turning off power saving on the rt2800usb driver, and I've followed guides to successfully compile the rt2870sta RAlink driver.  The rt2870sta driver will work but not scan, I can connect to my router for a few seconds or minutes without packet loss, but then I get a kernel panic.  The built in rt2800usb will scan and doesn't crash but instead multiple packets are dropped every second, no matter what iwconfig settings I give it.  Is there any upstream work still being done on the rt2x00 drivers?  Is there anyway that I can fix the packet loss?

---

### Post by chili555 on 2013-04-13
Let's have a look at:```
lsusb
lsmod | grep rt2
```Thanks.

---

### Post by Gnobody on 2013-04-13
```
j@jbox:~$ lsusbBus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 003: ID 04e8:6881 Samsung Electronics Co., Ltd 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 004 Device 004: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 004 Device 005: ID 0461:4d75 Primax Electronics, Ltd Rocketfish RF-FLBTAD Bluetooth Adapter
j@jbox:~$ lsmod | grep rt2
rt2800usb              26855  0 
rt2800lib              66367  1 rt2800usb
crc_ccitt              12708  1 rt2800lib
rt2x00usb              20636  1 rt2800usb
rt2x00lib              54827  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              596686  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              510892  2 rt2x00lib,mac80211
compat                 17867  10 rt2800usb,mac80211,cfg80211,rfcomm,bnep,rndis_host,cdc_ether,usbnet,btusb,bluetooth



```

---

### Post by chili555 on 2013-04-13
It doesn't look like you compiled rt2870sta successfully. It's not loaded. Let's try a few things:```
sudo apt-get install linux-backports-modules-quantal-generic
```Reboot and then show us, with the wireless only connected:```
ping -c5 8.8.8.8
```There may be a couple of other things we can try if that doesn't help.

---

### Post by Gnobody on 2013-04-13
Weird, I have the rt2870sta module blacklisted in /etc/modprobe.d/blacklist.conf, and it loads when I modprobe it.
I already have that package installed and earlier today I successfully compiled the latest tarball [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/)
With just wifi connected I ran the following ping for you:
```
ping -c5 8.8.8.8 PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=52 time=74.8 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=52 time=70.4 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=52 time=73.4 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=52 time=71.0 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=52 time=72.2 ms


--- 8.8.8.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 70.469/72.416/74.870/1.625 ms



```

The problem only presents itself with stalled uploads or in Xonotic or other online games, I know it has to be this adaptor or the drivers because my internet works fine when I tether my smartphone to my PC.

---

### Post by Gnobody on 2013-04-13
with larger packet sizes I get drops:
```

ping -s 1200 -c5 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 1200(1228) bytes of data.
72 bytes from 8.8.8.8: icmp_req=1 ttl=52 (truncated)
72 bytes from 8.8.8.8: icmp_req=2 ttl=52 (truncated)
72 bytes from 8.8.8.8: icmp_req=4 ttl=52 (truncated)
72 bytes from 8.8.8.8: icmp_req=5 ttl=52 (truncated)


--- 8.8.8.8 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4009ms
rtt min/avg/max/mdev = 74.854/75.292/75.896/0.505 ms

```

---

### Post by Gnobody on 2013-04-13
nohwcrypt is enabled and I usually test it after doing iwconfig wlan0 power off

---

### Post by chili555 on 2013-04-15
It doesn't help to go to all the trouble to compile the driver so that you can then:> Weird, I have the rt2870sta module **blacklisted** in /etc/modprobe.d/blacklist.conf, May I see:```
iwconfig
dmesg | grep rt2
```I am actually surprised you could get rt2870sta to build. I think the source code is quite old now.

Is your router set to use N speeds? I'd try without.

---

### Post by Gnobody on 2013-04-15
I blacklisted that module because of kernel panics but I assure you that it does load and I had to follow a few guides and change 2 supplicant options in the make file to compile it.   

```
iwconfigusb0      no wireless extensions.


eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"Boudreau"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 20:10:7A:92:7C:EA   
          Bit Rate=19.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:15  Invalid misc:33   Missed beacon:0



```

```
[19178.894438] phy0 -> rt2x00_set_chip: Info - Chipset detected - rt: 3070, rf: 0005, rev: 0201.[19178.923606] Registered led device: rt2800usb-phy0::radio
[19178.923658] Registered led device: rt2800usb-phy0::assoc
[19178.923711] Registered led device: rt2800usb-phy0::quality
[19178.923887] usbcore: registered new interface driver rt2800usb
[19178.957787] phy0 -> rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'.
[19178.964381] phy0 -> rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29.



```

My router is a N capable router however it's running in b/g mode.

---

### Post by chili555 on 2013-04-15
When you tried rt2870sta, did you have rt2800usb blacklisted? In your dmesg, we see no connection details, like this stuff from my machine:> [   42.802314] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   45.959510] wlan0: authenticate with xx:13:10:62:8d:22
[   45.998661] wlan0: send auth to xx:13:10:62:8d:22 (try 1/3)
[   46.001433] wlan0: authenticated
[   46.004734] wlan0: associate with xx:13:10:62:8d:22 (try 1/3)
[   46.007370] wlan0: RX AssocResp from xx:13:10:62:8d:22 (capab=0x411 status=0 aid=3)
[   46.015819] wlan0: associated
[   46.015875] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Perhaps it's because your machine has been up long enough that the log was archived and restarted. What about:```
dmesg | grep wlan
cat /var/log/dmesg.0 | grep wlan
```What about N?

---

### Post by Gnobody on 2013-04-15
> **chili555 said:**
> When you tried rt2870sta, did you have rt2800usb blacklisted? In your dmesg, we see no connection details, like this stuff from my machine:Perhaps it's because your machine has been up long enough that the log was archived and restarted. What about:```
dmesg | grep wlan
cat /var/log/dmesg.0 | grep wlan
```What about N?

No I didn't have the rt2800usb blacklisted at that time instead I removed it via modprobe -r rt2800usb before loading the rt2870sta module

N support is turned off.

```
[19179.349403] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready[19179.350384] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[19182.220467] wlan0: authenticate with 20:10:7a:92:7c:ea
[19182.263625] wlan0: send auth to 20:10:7a:92:7c:ea (try 1/3)
[19182.265207] wlan0: authenticated
[19182.266531] wlan0: associate with 20:10:7a:92:7c:ea (try 1/3)
[19182.271064] wlan0: RX AssocResp from 20:10:7a:92:7c:ea (capab=0x411 status=0 aid=4)
[19182.277627] wlan0: associated
[19182.277688] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[19439.737489] wlan0: deauthenticating from 20:10:7a:92:7c:ea by local choice (reason=3)
[20024.336468] wlan0: authenticate with 20:10:7a:92:7c:ea
[20024.365372] wlan0: send auth to 20:10:7a:92:7c:ea (try 1/3)
[20024.366967] wlan0: authenticated
[20024.371044] wlan0: associate with 20:10:7a:92:7c:ea (try 1/3)
[20024.380969] wlan0: RX AssocResp from 20:10:7a:92:7c:ea (capab=0x411 status=0 aid=4)
[20024.387866] wlan0: associated
[20233.671110] wlan0: deauthenticating from 20:10:7a:92:7c:ea by local choice (reason=3)
j@jbox:~$ cat /var/log/dmesg.0 | grep wlan
j@jbox:~$ 



```

---

### Post by RosewillEye on 2013-04-16
Hi, It looks as if you are following all the necessary steps, but if you reach a point where you need further assistance, or feel you might need to exchange the dongle, please don't hesitate to contact Rosewill support directly at (800) 575-9885 or email [email]techsupport@rosewill.com[/email]. Have a great day!

---

### Post by Gnobody on 2013-04-18
> **RosewillEye said:**
> Hi, It looks as if you are following all the necessary steps, but if you reach a point where you need further assistance, or feel you might need to exchange the dongle, please don't hesitate to contact Rosewill support directly at (800) 575-9885 or email [EMAIL="techsupport@rosewill.com"]techsupport@rosewill.com[/EMAIL]. Have a great day!

Awesome, I just shot off an e-mail to see if you guys could exchange it for another model that lists Linux support.

---

### Post by Gnobody on 2013-04-24
Rosewill will only offer me a Newegg.ca RMA, does anybody have an suggestions on how to get this adapter to work properly?

---

