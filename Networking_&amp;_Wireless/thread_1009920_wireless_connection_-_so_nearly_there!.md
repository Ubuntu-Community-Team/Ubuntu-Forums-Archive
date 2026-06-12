---
title: "wireless connection - so nearly there!"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by mylesk on 2008-12-13
I have installed a USB Belkin f5d6050 on Ubuntu 8.10 and this seems to have installed and been understood
lsusb gives me
Bus 004 Device 003: ID 0d5c:a002 Belkin F5D6050 802.11b Adapter

so think it is recognised
iwconfig gives

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

so this looks good. Then I hit a wall
I have tried using system | preferences | network configuration to manually set up the network (using a 40bit WEP key) it seems to find it, but continually tries and never connects (yes - I have tried rekeying the WEP key 83 times!)
I also tried setting this up directly from IWCONFIG (to same channel, key and ESSID) but again no joy
In all the docs I have looked at it recommends using system | administration | network manager but I do not have this link
Can anyone help? I have been through every forum I can find

many thanks

---

### Post by iponeverything on 2008-12-13
Do you have the network manager applet on your toolbar?

If not:

System->Preferences->Sessions

Go to "+ Add"

The fill in the fields as follows:

Name: Network Manager
Command: nm-applet --sm-disable
Comment: Network Manager applet

And click "Save" 

Then logout and log back in to and see if you have applet no your tool bar.

If that does not work run "nm-applet" from the command line and post the output.

---

### Post by mylesk on 2008-12-13
I got 
 nm-applet

** (nm-applet:6166): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6166): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

but I suspect is this because it is there after all! see attachment screenshot

I can detect the network I want to attached to
iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:A9:C1:EE
                    ESSID:"leopold"
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Signal level=100/100  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s

but despite putting this info (ssid, key etc) it does not connect

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:55:5b:ee:39  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:55ff:fe5b:ee39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2440449 (2.4 MB)  TX bytes:2373612 (2.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:30:bd:64:99:81  
          inet6 addr: fe80::230:bdff:fe64:9981/64 Scope:Link
          UP BROADCAST  MTU:1500  Metric:1
          RX packets:223 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67080 (67.0 KB)  TX bytes:6282 (6.2 KB)

---

### Post by iponeverything on 2008-12-13
yep that is it. So, I take it that it is not connecting with nm-applet. Why don't give wicd a try.. Trying wicd should not to hard, if you use the deb to install it should disable network manager and if you uninstall wicd network manager should be re-enabled again.

---

### Post by mylesk on 2008-12-13
thanks iponeverything - wicd gives me more, but underlying problem is the same. I enable wep hex, and put in the key it does not obtain an IP. I have several other (windows) devices that connect wirelessly to the access point

---

### Post by mylesk on 2008-12-13
btw I tried setting the AP to unencrypted and same problem, so i cannot help but think it is a problem with the driver or the setup...

---

### Post by iponeverything on 2008-12-13
add the network monitor applet to the tool bar. does the status bar go green while it is trying to connect?

If it does, try might just be that your not picking up a dhcp address.
If that is the case try the manual settings in network manager or wicd to configure it with a static IP.

I saw this issue recently..

---

### Post by mylesk on 2008-12-14
no, the status bar stays amber. I tried static IP - no joy (would not connect / could not ping) I also tried connecting a separate access point (unencrypted) to the network. This also cannot connect with the same symptoms, so the problem is a the ubuntu end...
Is there any way to check this from the command line?
many thanks

---

### Post by iponeverything on 2008-12-14
yes. First set your access point to unencrypted.

from the command line:

```
sudo -i
/etc/init.d/NetworkManager stop
killall -v nm-applet

ifconfig wlan0 up
iwconfig wlan0 essid leopold


```

at this point do a:

iwconfig

and see if see the mac address of your access point

```
 Access Point: xx:xx:xx:xx:xx:xx

```
if you  see it then you have successfully associated. If not 
do a "iwlist wlan0 scan" and note the channel of the access point and try

iwconfig wlan0 channel <chan>

where <chan> is your channel - now see if you associated.

You should be in "Managed" mode. If you are not do:

```
iwconfig wlan0 mode managed
```

if at any point you managed to associate do:

ifconfig wlan0 192.168.0.3 netmask 255.255.255.0
route add default gw 192.168.0.1

where the ip address are correct for your configuration.

try to ping the access point.

---

### Post by mylesk on 2008-12-14
Afraid not - tried this on unencrypted, and encrypted wireless network - same result. Can assign an IP to the interface, but the access point cannot pick up the connection / cannot connect to internet etc

root@kids-desktop:~# ifconfig wlan0 up
root@kids-desktop:~# iwconfig wlan0 key [1] 3638a6f376
root@kids-desktop:~# iwconfig wlan0 essid leopold
root@kids-desktop:~# iwconfig wlan0 channel 11
root@kids-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"leopold"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:A9:C1:EE   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Encryption key:3638-A6F3-76   Security mode:open
          Power Management:off
          Link Quality=100/100  Signal level=100/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
root@kids-desktop:~# ifconfig wlan0 192.168.1.1 netmask 255.255.255.0
root@kids-desktop:~# route add default gw 192.168.1.1
root@kids-desktop:~# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:30:bd:64:99:81  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe64:9981/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25010 (25.0 KB)  TX bytes:398 (398.0 B)

but pinging any device on network fails could it be driver problem?

---

### Post by iponeverything on 2008-12-14
```
root@kids-desktop:~# ifconfig wlan0 [COLOR="Red"]192.168.1.1[/COLOR] netmask 255.255.255.0
root@kids-desktop:~# route add default gw [COLOR="Red"]192.168.1.1[/COLOR]
root@kids-desktop:~# ifconfig wlan0
wlan0 Link encap:Ethernet HWaddr 00:30:bd:64:99:81
inet addr:192.168.1.1 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::230:bdff:fe64:9981/64 Scope:Link
UP BROADCAST RUNNING MTU:1500 Metric:1
[COLOR="Red"]RX packets:64 [/COLOR]errors:0 dropped:0 overruns:0 frame:0
[COLOR="Red"]TX packets:11[/COLOR] errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:25010 (25.0 KB) TX bytes:398 (398.0 B)

```

If your router is 192.168.1.1 give the desktop a different last octet - one that is not already used. Say.. .4 or something.. Your IP addresses have to be unique!

```
ifconfig wlan0 [COLOR="Red"]192.168.1.4[/COLOR] netmask 255.255.255.0
route del default
route add default 192.168.1.1



```

---

### Post by mylesk on 2008-12-15
I do this and I can ping the interface (192.168.1.4) but not the DG or beyond (192.168.1.1) and the wireless access point still does not recognise that the ubuntu PC has connected. I suspect all that has happened is an IP address has been assigned to the interface, but network connection not made.

---

### Post by mylesk on 2008-12-15
see below...

root@kids-desktop:~# iwconfig wlan0 
wlan0     IEEE 802.11b  ESSID:"leopold"  Nickname:"" 
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:B5:A9:C1:EE   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Encryption key:3638-A6F3-76   Security mode:open 
          Power Management:off 
          Link Quality=100/100  Signal level=100/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

root@kids-desktop:~# ifconfig wlan0 
wlan0     Link encap:Ethernet  HWaddr 00:30:bd:64:99:81  
          inet addr:192.168.1.54  Bcast:192.168.1.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING  MTU:1500  Metric:1 
          RX packets:81 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:19415 (19.4 KB)  TX bytes:252 (252.0 B) 

root@kids-desktop:~# ping 192.168.1.1 
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. 
From 192.168.1.54 icmp_seq=1 Destination Host Unreachable 
From 192.168.1.54 icmp_seq=2 Destination Host Unreachable 
From 192.168.1.54 icmp_seq=3 Destination Host Unreachable 
^C 
--- 192.168.1.1 ping statistics --- 
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4017ms 
, pipe 3 
root@kids-desktop:~# ping 192.168.1.54 
PING 192.168.1.54 (192.168.1.54) 56(84) bytes of data. 
64 bytes from 192.168.1.54: icmp_seq=1 ttl=64 time=0.253 ms 
64 bytes from 192.168.1.54: icmp_seq=2 ttl=64 time=0.094 ms 
^C 
--- 192.168.1.54 ping statistics --- 
2 packets transmitted, 2 received, 0% packet loss, time 999ms 
rtt min/avg/max/mdev = 0.094/0.173/0.253/0.080 ms

---

### Post by iponeverything on 2008-12-15
looking at the tx and rx, it is working somewhat. 

not sure what is going on. What is the ip address on the wireless router?

put the opendns servers in your /etc/resolv.conf, in case the your wireless route is configured not answer pings.

---

### Post by gordintoronto on 2008-12-18
> **mylesk said:**
> I do this and I can ping the interface (192.168.1.4) but not the DG or beyond (192.168.1.1) and the wireless access point still does not recognise that the ubuntu PC has connected. I suspect all that has happened is an IP address has been assigned to the interface, but network connection not made.

This is a long shot...

Is it possible the router has been configured to only allow specified MAC addresses?  (Like mine!)

---

### Post by mylesk on 2008-12-19
thanks for this, but no, the router does not have MAC level restriction. I also set up a completely separate unsecured wireless router and this had the same problem (and I have tested the F5D6050 on windows), so the problem is definitely with Ubuntu I am afraid. Was hoping to build this for my boy for Christmas, but not much point with no network :-(

---

### Post by dave100 on 2009-01-15
> **mylesk said:**
> thanks for this, but no, the router does not have MAC level restriction. I also set up a completely separate unsecured wireless router and this had the same problem (and I have tested the F5D6050 on windows), so the problem is definitely with Ubuntu I am afraid. Was hoping to build this for my boy for Christmas, but not much point with no network :-(

I also spent many nights with the sama device and 8.10. It managed to make an association with the wlan router. Router listed my MAC, but IP was "unknown". I forced IP, everything looks ok, but ping says "Host unreachable".

I finally gave up. Just ordered A-link WL54H which SHOULD work out of the box...

---

### Post by mylesk on 2009-01-15
sad to say, so did I. I got another wireless usb card (hand to reinstall Ubuntu from scratch).
if anyone wants the challenge of installing the belkin F5D5060 let me know!

---

### Post by bedake on 2009-01-28
Unfortunately I am using a broadcom f5d6050 and am unable to acquire an IP address using NM or wicd.  Do I need to resign myself to buying a new wireless adapter?  

This is a little funny to me because I started using ubuntu all the way back during 6.06 Dapper for the first time and I somehow managed to get this very same adapter to work perfectly.  Strange...

---

