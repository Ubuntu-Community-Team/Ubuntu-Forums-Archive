---
title: "Nokia CS-15 not working in 12.04 Precise Pangolin"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by achim_59 on 2012-09-29
Due to a harddisk failure (HD duly replaced) I recently replaced Lucid Lynx with Precise Pangolin on my IBM T43 Thinkpad. I was forced to reinstall much of the peripheral stuff from backups which is never easy. Amongst other problems, my CS-15 UMTS modem nolonger works properly.

There is a bug noted on Ubuntu Launchpad. See
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/992639]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/992639")

There is a workaround described (comment number 8 ) which allows the modem to be recognised. I made the necessary change and the modem was correctly assigned to device ttyACM0. However, when I ran the wvdial script I've been using for the past 2 years with ubuntu 10.04 I got the following response:

```
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet.eplus.de","",0,0
--> Sending: ATQ0
--> Re-Sending: AT+CGDCONT=1,"IP","internet.eplus.de","",0,0
--> Modem not responding.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: AT+CGDCONT=1,"IP","internet.eplus.de","",0,0
--> Sending: ATQ0
--> Re-Sending: AT+CGDCONT=1,"IP","internet.eplus.de","",0,0
OK
OK
OK
OK
OK
OK
OK
OK
OK
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
CONNECT
~[7f]}#@!}!}!} }<}!}$}&@}#}$@#}%}&E}^t[0e]}"}&} } } } }'}"}(}"AB~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Sep 29 14:22:50 2012
--> Pid of pppd: 12804
--> Using interface ppp0
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> pppd: xUs&#65533;&#65533;?n [10]7n [01]
--> Disconnecting at Sat Sep 29 14:23:26 2012
--> The PPP daemon has died: Pty program error (exit code = 9)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 20 seconds

```

This sequence was repeated ad nauseum, so I cancelled the dialup process. I then checked /var/log/syslog to see what had been happenning (at least as far as the system was concerned). Here's what I found:

```
Sep 29 14:21:41 achim-T43 pppd[12797]: pppd 2.4.5 started by root, uid 0
Sep 29 14:21:41 achim-T43 NetworkManager[790]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 29 14:21:41 achim-T43 NetworkManager[790]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Sep 29 14:21:41 achim-T43 pppd[12797]: Using interface ppp0
Sep 29 14:21:41 achim-T43 pppd[12797]: Connect: ppp0 <--> /dev/ttyACM0
Sep 29 14:21:41 achim-T43 pppd[12797]: Remote message: TTP Com PPP - Password Verified OK
Sep 29 14:21:41 achim-T43 pppd[12797]: PAP authentication succeeded
Sep 29 14:21:47 achim-T43 pppd[12797]: Received bad configure-nak:  02 06 00 2d 0f 01 81 06 00 00 00 00 83 06 00 00 00 00
Sep 29 14:22:17  pppd[12797]: last message repeated 9 times
Sep 29 14:22:17 achim-T43 pppd[12797]: IPCP: timeout sending Config-Requests
Sep 29 14:22:17 achim-T43 pppd[12797]: Connection terminated.
Sep 29 14:22:17 achim-T43 avahi-daemon[800]: Withdrawing workstation service for ppp0.
Sep 29 14:22:17 achim-T43 NetworkManager[790]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Sep 29 14:22:17 achim-T43 pppd[12797]: Exit.

```

This was also repeated over and over. I'm guessing the problem lies with the message "Received bad configure-nak", though I really don't understand what it means. I had similar problems about 2 years ago, but switching to using wvdial seemed to solve the problems. At least I thought it did,

Can anyone help? Please! I really need this thing to function in order to do my work. 

Achim

---

### Post by achim_59 on 2012-09-30
OK, I haven't yet found the link to mark this as solved but I *do* think I know what was wrong.

Unplugging and reinserting the device, I noticed that the CS-15 was no longer being recognised as a UMTS device and it wasn't being assigned the expecten ttyACM0 device ID. Odd!

In Lucid it didn't seem to matter a bean (coffee or otherwise) whether I was attached via a LAN or not, when I attached the CS15. It was always recognised as a UMTS device. 

However, on spec I unplugged the LAN cable from my laptop just now. I reinserted the device and fired up wvdial... and hey presto! I am writing this post using the CS-15 for my connection.

I think that pretty well sorts it out. I'll mark this as solved as soon as I've found the appropriate link.

Achim ;)

P.S. I have another post inwhich I'm not sure whether it's a desktop problem or a WLAN problem. If one of you wireless gurus could take a look and give me a hint as to what's wrong, I'd be very grateful:
[http://ubuntuforums.org/showthread.php?t=2063953]("http://ubuntuforums.org/showthread.php?t=2063953")

---

