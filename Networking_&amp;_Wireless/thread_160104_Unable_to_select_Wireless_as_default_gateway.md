---
title: "Unable to select Wireless as default gateway"
date: 2006-04-14
forum: Networking &amp; Wireless
---

### Post by mengqing on 2006-04-14
I think my Wireless is correctly set up.. and it appeared in the Network settings as Active, however I can not select it as my default gateway, after I select and click OK, and opens Network settings again, the default gateway will become something else..


from iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"mengqing"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:13:49:6C:D3:B6
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key:4D65-6E67-5169-6E67-5A68-616E-67   Security mode:open
          Power Management:off
          Link Quality=57/100  Signal level=-46 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:37


from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:D8:8B:D6:7E
          inet addr:192.168.1.34  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe8b:d67e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1077 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1061507 (1.0 MiB)  TX bytes:164827 (160.9 KiB)
          Interrupt:21 Base address:0xd800

eth1      Link encap:Ethernet  HWaddr 00:0E:35:EF:06:F0
          inet6 addr: fe80::20e:35ff:feef:6f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:53 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3787 (3.6 KiB)  TX bytes:8300 (8.1 KiB)
          Interrupt:17 Base address:0xe000 Memory:fe8ff000-fe8fffff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5092 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5092 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:481913 (470.6 KiB)  TX bytes:481913 (470.6 KiB)


In the router, it showed that my notebook is connected, however I can not ping anything on my notebook.. can somebody help me?? I m really desprate at getting wireless to work..

---

### Post by Ensnared on 2006-04-14
Apparently your wireless interface (eth1) is not receiving an IP-address from your DHCP (if you have a DHCP that is). What you can try is to give it a static IP to see if that works, and also disable eth0 at the same time so you know that  the traffic is going through eth1.

To turn off eth0:
```
sudo ifdown eth0
```

To give eth1 a static address:
```
sudo ifconfig eth1 192.168.1.35 netmask 255.255.255.0
```

If your interface is working properly you should then be able to ping your router, provided that it's got an IP in the 192.168.1.1 - 192.168.1.254 range (I'm assuming it does since your eth0 interface has the 192.168.1.34 address).

If this works, then chances are your wireless adapter is either not set up to receive a dynamic IP (seems unlikely), or there's a configuration problem on your router. To make sure it's set up with a dynamic IP, look for the following line in /etc/network/interfaces:
```
iface eth1 inet dhcp
```

If there's a line beginning with 'iface eth1' that looks different, change it to the one above (you can comment out the existing one by adding a # in front of it, then add the line above). After that, do the following to bring the device down and then back up:
```
sudo ifdown eth1
sudo ifup eth1
```

If it's still not getting an IP then - provided it worked giving it a static IP above - the error is most likely somewhere in your router. It may be a compatibility problem between the router and your card, in which case it would likely be solved by performing a firmware upgrade. Check your routers manufacturers website to see if there is one available.

---

### Post by mengqing on 2006-04-14
Hi, I've tried setting the wireless static as well as DHCP..but none of them worked..

The ethernet worked under static and also DHCP so i dont think it's my router's problem..I tried my notebook under windows and it worked...

After I disabled the eth0, I was able to select eth1 as my dafult gateway.. however still no traffic between my notebook and the router..


Could it be the driver problem??? I installed the latest ipw2200 driver.. 1.1.2, and it seems to be running ok...

is there anything else that is causing this problem??

thx for the help :)

---

### Post by Ensnared on 2006-04-14
Yes, this sounds like a driver problem.

I've had some issues with the latest ipw2200-drivers myself, so what you can try is the same as I did.

Download ieee80211-1.1.13 from sourceforge [link](http://ieee80211.sourceforge.net).
Download ipw2200 v1.1.0 and the ipw2200-firmware v2.4 from sourceforge [link](http://ipw2200.sourceforge.net).
Download the remove_old script attached to this post.

Run the remove_old script as root:
```
sudo sh ./remove_old
```
Untar the ieee80211-1.1.13 and the ipw2200-1.1.0 files.
Enter the ieee80211-1.1.13 directory and run the remove_old script located there as well.
Enter the ipw2200-1.1.0 directory and run the remove_old script located there also.
Go back to the ieee80211-1.1.13 directory and run the following:
```
make && sudo make install
```
When it completes (hopefully without errors), go to the ipw2200-1.1.0 directory and run the same commands.
Untar the ipw2200-fw-2.4 file and put all the .fw-files from it into your /usr/lib/hotplug/firmware/ directory.
Issue the following commands to shut off eth1 and unload the modues:
```
sudo ifdown eth1
sudo rmmod ipw2200
sudo rmmod ieee80211
sudo rmmod ieee80211_crypt
```
Load the modules you just built to replace them:
```
sudo modprobe ipw2200
```

Issue the command "dmesg" right after you load the modules to see if there's any errors there.

Basically, this is exactly what I've done to get my card working.

If the modules seem to load properly and it's still not working, make sure your WEP-key is correctly set up. What I have for this is the following two lines in /etc/network/interfaces, right under the iface eth1-line from earlier:
```
wireless-essid MYNET
wireless-key MYWEPKEY
```

You could try rebooting after all this is done just to make sure everything is reset (it shouldn't be necessary, but it can't hurt).

Try this, and post the output you get from the commands above if something looks wrong.

EDIT: Forgot the attachment :P I had ro rename it to remove_old.txt to upload it, but you can still run it as normal.

---

