---
title: "Ubuntu Server - USB Wireless CLI config"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by plague.immortal on 2009-03-25
Hello!

I've decided to setup a PC with Ubuntu server so it can serve me as a FTP server and perhaps even more in the future. 

Soon after install I knew I will have to face the command line interface but what I didn't expect was that my Ethernet Controller somehow died and the computer wont boot with the Ethernet controller in it. 

The original plan was to download the ubuntu-desktop and install it using the wired connection with the Ethernet Controller. After I would complete that I would install the USB Wireless network card and configure it in GUI to work properly. The problem now is that the USB wi-fi card now can't be configuered since I have absolutely NO knowledge of using the CLI. (Been suffering Windows for quite a long time). 

Then I gave it some thought and came up with "Hey maybe this is a great opportunity for me to learn how to use the CLI". I am also running Ubuntu Desktop distro on my laptop and knowing the CLI would help advance in Linux usage. 

So why did I start this thread...

First of all I want to get my USB Wi-fi card running so I get connection and then step it up to server configuration. I will put all my future questions, problems etc. in this thread.

Problem no.1 : How to get the USB Wi-fi configured using only CLI? (USB wireless network card - TP-Link TL-WN422G)

Thank you in advance.

---

### Post by Cheesehead on 2009-03-25
Let's assume your USB device is properly recognized and configured.
TIP  - Each of the commands below has a man page installed on your system. Try '$man iwconfig', for example. 

1) The 'iwconfig' command will tell you what wireless interfaces you have available, including wired, wireless, loopback, and other.

Let's say your new wireless interface is on 'eth1'. Yours may well have a different name - just change the name in the next steps.

```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:  Access Point:   
          Bit Rate=   Tx-Power=
          Retry min limit:   RTS thr:   Fragment thr=   
          Power Management:off
          Link Quality=     Signal level=    Noise level= 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

2) The 'iwlist' command scans for wireless networks. It requires 'sudo' and your password to pass this system-level command to the wireless driver, or else it will fail.
```
$ sudo iwlist eth1 scan
[sudo] password for ian:    #Your password will not show when you type 
eth1      Scan completed :
          Cell 01 - Address: 00:14:BF:EB:94:77
                    ESSID:"MyNetwork"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=94/100  Signal level=-35 dBm  Noise level=-64 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000001571246fadd

```

3) Use 'iwconfig' to connect to a network with the essid 'MyNetwork'. This time, you need to also use sudo, since you're telling it to make a system-level change.
```
$ sudo iwconfig eth1 essid MyNetwork
     # If it's been less than 15 minutes, the system won't ask for your password again

```

4) Let's use 'iwconfig' to check if it worked
```
$ iwconfig eth1
eth1      IEEE 802.11g  ESSID:"MyNetwork"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:EB:94:77   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality=85/100  Signal level=-51 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

5) Now that we're connected, let's use 'dhclient3' to get an IP address
```
$ sudo dhclient3 eth1
There is already a pid file /var/run/dhclient.pid with pid 5056
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
Listening on LPF/eth1/00:13:02:d0:bd:ce
Sending on   LPF/eth1/00:13:02:d0:bd:ce
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.132 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.132 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.132 from 192.168.1.1
bound to 192.168.1.132 -- renewal in 42731 seconds.

```

Finally, let's run a test to make sure we can use our newly acquired network.
```
$ ping www.google.com
PING www.l.google.com (74.125.95.103) 56(84) bytes of data.
64 bytes from iw-in-f103.google.com (74.125.95.103): icmp_seq=1 ttl=245 time=307 ms
64 bytes from iw-in-f103.google.com (74.125.95.103): icmp_seq=2 ttl=245 time=306 ms
64 bytes from iw-in-f103.google.com (74.125.95.103): icmp_seq=3 ttl=245 time=167 ms
<CTRL+C to stop the pings>
--- www.l.google.com ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 2998ms
rtt min/avg/max/mdev = 167.460/260.451/307.891/65.759 ms

```

---

### Post by plague.immortal on 2009-03-26
Thank you for a nicely formed reply.

But unfortunately there has been some differences with my Pc.
The interface name is wlan0 and it picks up the USB device I presume since it prints out a nice report on IEEE 802.11bg ESSID: "mySSID". However I get no Link Quality, no signal strenght, no noise level... plain zeros. That is after the "sudo iwconfig wlan0 essid mySSID" command. Even the scan thingy doesn't do anything it simply prints out an unpleasant "Interface doesn't support scanning : network is down". After the dhclient 3 it gives me a few messages stating "Network is down".

PS: Can you tell me how to copy the output of the commands I type into the PC and how to transfer them onto this PC?

---

### Post by tufcamman on 2009-09-30
Hi,

I am aware that this thread is a few months old, but for the benefit of those who will come after your problem of the network being down is solved by simply bringing it up.

```
sudo ifconfig "network device (eth0, wlan0, etc)" up
```

I am using a Rosewill USB device so my command was

```
sudo ifconfig ra0 up
```

After this you can run the commands specified before.

Cheers!

---

