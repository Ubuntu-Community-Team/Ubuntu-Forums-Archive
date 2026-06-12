---
title: "HOW TO connect wireless NCI to AP via CLI"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by nakoruru on 2010-10-08
Hi, i use madwifi as the wireless NCI driver, and it works fine in UBUNTU, but i wanna know how to connect to a specific AP via wireless tools such as "iwconfig, iwlist" in CLI, so can someone provide the steps that i can follow step by step ? :lolflag:.

---

### Post by techdude3177 on 2010-10-08
It is actually very easy to connect to an access point from the command line.

First make sure that the interface for the wireless is up. (Assuming your interface is wlan0)

```
ifconfig wlan0 up
```

Now if you wish to scan for wireless access points.

```
sudo iwlist wlan0 scan
```

Once you found the essid name of the access point you wish to connect to, tell the interface to connect. (Assuming that you want to connect to essid with the name of "wireless")

```
iwconfig wlan0 essid "wireless"
```

If there is encryption then we need to give the key

```
iwconfig wlan0 key 1234-5678-9012-3456
```

Most people use dhcp when connecting to wireless so request dhcp

```
sudo dhclient wlan0
```

Then make sure everything is configured correctly!

```
ifconfig
```

CHEERS!

---

### Post by nakoruru on 2010-10-08
thank techdude3177 for your reply.
 
i type "iwconfig" then i see the infomations below.
 
lo        no wireless extensions.
eth0      no wireless extensions.
wifi0     no wireless extensions.
ath0      IEEE 802.11g  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:18 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:412246  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
so should i replace the "wlan0" in your reply with "ath0"?
 
and BTW,could you provide the way the disconnect the wireless , i am new, thanks so much^___^

---

### Post by nakoruru on 2010-10-08
More information, i 'm still unable to connect.
step1:ifconfig ath0 up
step2:iwconfig ath0 essid "wireless"
step3:dhclient ath0
(there is no encryption, so i didn't need to give key )
then i got the following trace.
==
There is already a pid file /var/run/dhclient.pid with pid 7734
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/d8:5d:4c:06:f9:9d
Sending on   LPF/ath0/d8:5d:4c:06:f9:9d
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
==
 
did i miss any key step? T____T

---

### Post by techdude3177 on 2010-10-09
As you guessed, you should use the interface marked ath0 for your setup.
Sorry I didnt explain something. You need to change "wireless" to whatever the essid name is of the access point you want to connect to. In this case I called it "wireless". So if your access point name is linksys the command should look like this:
```
iwconfig wlan0 essid linksys
```

I guess the easy way for a disconnect would be to just put the interface down.
```
ifconfig ath0 down
```

---

### Post by nakoruru on 2010-10-09
thanks techdude3177.:):):)
 
i did just as you said, the access point name i want to connect is "ljtplink2", so actually i type the command " iwconfig ath0 essid ljtplink2 ".
 
now the issue is why i got the following trace after i type "dhclient ath0".
 
==
There is already a pid file /var/run/dhclient.pid with pid 7734
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [[COLOR=#444444]https://www.isc.org/software/dhcp/[/COLOR]]("https://www.isc.org/software/dhcp/")
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/d8:5d:4c:06:f9:9d
Sending on LPF/ath0/d8:5d:4c:06:f9:9d
Sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
==
 
i have no idea what happens......
or if i need to do some configuration before performing the steps you provided?
 
it should not be the AP issue for that i can connect to the AP via GUI of UBUNTU, and the dhcp service has been open on this AP.

---

### Post by techdude3177 on 2010-10-09
According to the output your not getting any DHCP offers. What is the output of your ifconfig for ath0?

Also can I see the output for this command?
```
ps aux | grep -i Network
```

Thanks

---

### Post by nakoruru on 2010-10-09
hi,sorry for late reply.
the output of "ifconfig ath0" is:
 
ath0      Link encap:Ethernet  HWaddr d8:5d:4c:06:f9:9d  
          inet6 addr: fe80::da5d:4cff:fe06:f99d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7372 (7.3 KB)  TX bytes:7388 (7.3 KB)
 
and the output of "ps aux | grep -i Network" is:
 
root       861  0.0  0.4  19100  4268 ?        Ssl  Oct08   0:13 NetworkManager
root      8145  0.0  0.0   3532   912 pts/1    S+   14:45   0:00 grep --color=auto -i Network
 
 
thanks^_______^

---

### Post by techdude3177 on 2010-10-09
Yep... unfortunately the GUI NetworkManager is being dominate here, its actually trying to configure the interface instead of allowing the override of the manual config.  So you have to decided if you want to allow for NetworkManger to configure this or if you want to do it manually. 
If want to manually configure this then do the following:

You need to remove NetworkManger
```
sudo apt-get remove network-manager*
```

Then try using the commands I suggested before, unsure if that will work since I am not able to access my test machines where I am currently at. Please let me know if they do or not. If the commands do not work I know the following will.

Edit your interface config file
```
sudo gedit /etc/network/interfaces
```

And enter in the following code changing the information as needed, aka interface, essid, and key.
```
auto ath0
iface ath0 inet dhcp
wireless-essid "wireless"
wireless-key 1234567890123456
```
Save this file and reboot the machine. This also should connect on boot which can be beneficial. 

Post again if you need anything else.
CHEERS!:popcorn:

---

### Post by nakoruru on 2010-10-09
hi techdude3177:
    thank you for your kindly help, i remove the NetworkManger by using the command "apt-get remove network-manager*", and now i can connect to the ap.^___^
    it's really very kind of you, wish you have a good day:):):).

---

### Post by nakoruru on 2010-10-25
Hi,now i got a new problem,if the access point doesn't provide dhcp services, which means i can't use the command "dhclient ath0" to get ip address now:(,i have to specify the IP address, netmask,the gateway manually. but i have no idea how to config,could someone help? thanks:KS

---

