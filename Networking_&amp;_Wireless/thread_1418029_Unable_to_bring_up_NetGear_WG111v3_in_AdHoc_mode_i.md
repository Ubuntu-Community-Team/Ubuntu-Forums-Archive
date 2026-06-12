---
title: "Unable to bring up NetGear WG111v3 in AdHoc mode in ubuntu"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by avi@nitc on 2010-02-28
Hi All,

I am using Ubuntu 9.04 on Linux 2.6.28-18-generic. 
I have a WiFi USB Card from NetGear WG111v3 [rtl8187 driver]. It worked out of box, in Managed[infrastructure] mode.

But, when I change the mode to Ad-hoc, the I am unable to bring up the device. Here is what I am doing

$ sudo iwconfig wlan0 mode ad-hoc
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy.
$ sudo ifconfig wlan0 down
$ sudo iwconfig wlan0 mode ad-hoc
$ sudo iwconfig wlan0 essid UbuntuAdhoc
$ **iwconfig wlan0**
wlan0     IEEE 802.11bg  ESSID:"UbuntuAdhoc"  
          **Mode:Ad-Hoc**  Frequency:2.412 GHz  Cell: FA:26:32:28:E2:6A   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[B]sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported[/B]

I tried fixing the IP add, Netmask and gateway, through ifconfig, and the tried ifconfig up, but still unable to bring up the ad-Hoc network.

[B]But I am able to bring up sucessfully on the managed mode,  
As do iwlist wlan0 scan, to find the networks in range.[/B]


**Please suggest and clarify the following:**


[LIST=1]
[*]Does WG111v3 work in Adhoc mode on Linux [it works in windows] ?  I got this doubt as i could not find any success story online.
[*]If yes please suggest some procedure, what do i need to do?
[*]If no I came to know D Link DWA110 [RT73 driver basded] works well in AdHoc mode on Linux. Do I need to go for change of Adapter.
[/LIST]
Regards 
Avinash

---

### Post by morphium on 2010-03-11
Well, I've faced the same problem, trying to solve it for last week.

I am using Ubuntu 9.10 on Linux 2.6.31-20-generic on Laptop Toshiba A300D with Realtek  RTL8187B Wireless Adapter.

I cannot say I have solved this problem, but I moved a bit further in my researches. 

> 
[B]sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not supported[/B]To solve this problem I suggest you to install ndiswrapper driver.


After this I am able to up my wireless ad-hoc network and even let two my devices (HTC hero and ASUS p535) connect to it and ping each other. But when I'm trying to connect to this network my laptop itself connection lost after a minute or less. I'm still working on it.

---

### Post by morphium on 2010-03-11
Finally it worked for me with ndiswrapper driver.

But without authentication.  I gotta use MAC authecation then.

---

