---
title: "Running NetworkManager [or similar] without X"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by bivab on 2009-10-25
Currently, the only way I've been able to connect to my wireless network is with the NetworkManager app. I've tried all sorts of CLI voodoo to connect my card manually, but in the end the only way I can get connected is to start the NetworkManager. Unfortunately, this applet requires X to run. Is there a way to somehow run it (or something very similar that would also work) without X running?

---

### Post by lswb on 2009-10-25
From a vt, you can try a variation of this command line:
```

sudo ifconfig eth1 down # This line often not necessary
sudo iwconfig eth1 mode managed essid "networkname" key aabbccddee
sudo ifconfig eth1 up # again, this line often not needed, depending on card/driver
sudo dhclient eth1

```

This line assumes:

* eth1 is your wireless interface 
* Your wifi net is running on a wireless router or access point in typical "managed" or infrastructure mode
* "networkname" is the quoted name (essid) of your wireless network
* Your wifi network is WEP or WPA protected using a hex key of aabbccddee. If you are using an ascii text string rather than a hex string, use s:asciistring instead of aabbccddee, i.e. "s:" immediately followed by the ascii text string.
* Your router is handling dhcp or passing dhcp requests to some other working host on the network.

Note that "ifconfig" is not the same as "iwconfig", that is not a typo. Again, the lines beginning with ifconfig (in my experience) are not usually necessary. 

Usually it is not necessary to specify a channel, but if needed, append "channel x" to the iwconfig line, where x is the channel number being used. You can find this from the setup screen of your router.

---

### Post by bivab on 2009-10-25
lswb, thanks for the quick reply. I've actually tried that before, here's the output I get:

```
[FONT=monospace]
[/FONT]root@bivab-server:~# ifconfig wlan0 down
root@bivab-server:~# iwconfig wlan0 mode managed essid "Topeka" key [MYKEY] channel 6
root@bivab-server:~# ifconfig wlan0 up
root@bivab-server:~# dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:11:50:01:a3:34
Sending on   LPF/wlan0/00:11:50:01:a3:34
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.103 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
Trying recorded lease 192.168.1.103
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```I double checked my router, and it is indeed running a DHCP server. I also made sure to specify the channel. Also, it disturbed me that pinging my router returned an error, so I tried it myself, and got the message "Destination Host Unreachable". 

All of which makes me wonder, what does the NetworkManager applet know that I don't? :P

EDIT: By the way, here's the info on my wifi card (when it's connected):
```

bivab@bivab-server:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Topeka"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:FD:7F:52
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level=-64 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

bivab@bivab-server:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:11:50:01:a3:34
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe01:a334/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23765244 (23.7 MB)  TX bytes:1310145 (1.3 MB)

```

---

### Post by lswb on 2009-10-25
The problem may be with Network Manager itself rather than something special about the applet. (nm-applet is a separate program from Network Manager) I sometimes get interference from NM when working at the command line and have to shut it down to get things working the way I want.

In Jaunty the command to stop NM is
```

sudo /etc/init.d/NetworkManager stop

```

In hardy use
```

/etc/dbus-1/event.d/25NetworkManager stop
/etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

Sorry but I don't remember which verse worked in intrepid.

To restart NM, use the same commands but replace "stop" with "start"

---

### Post by bivab on 2009-10-25
Hmm, that was a good idea. I'm using Jaunty, by the way. Unfortunately it didn't work--I still get "No DHCP offers received" when I run dhclient. :/

---

### Post by lswb on 2009-10-25
Well, I'm out of ideas, those steps usually work for me. There is a good sticky/howto thread in the forums for connecting from the cli at 
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
but it is really too long now to read through :(

One observation I have made is that in a marginal connection enviroment, Network Manager may try to connect a little longer than the cli tools, i.e. if dhclient doesn't get an ip address the 1st time, it may run again. You may have to try the dhclient command 2 or 3 times if the signal is weak.

---

### Post by bivab on 2009-10-25
Thanks...I actually went through that thread originally when I was trying this before I posted, but I didn't go through all 94 pages...

Anyway, I can keep trying with dhclient, though my signal is pretty strong so I doubt it's the case that it just needs longer to connect. Thanks for you help!

---

