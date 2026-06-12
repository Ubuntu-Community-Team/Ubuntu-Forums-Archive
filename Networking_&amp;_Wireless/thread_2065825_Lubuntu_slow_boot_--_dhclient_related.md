---
title: "Lubuntu slow boot -- dhclient related?"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by tarkawebfoot on 2012-10-02
Hi all,

I just rescued my Acer AO722 netbook by installing Lubuntu from the alternative ISO (needed to boot from an LVM volume). Doing so, however, has changed the desktop and the set of installed programs.

The most notable thing is that it now takes ~3-4 minutes to boot. In the install made from the live CD, boot was only seconds.

In examining syslog entries and watching timestamps, I see a lot of things like this:

```
Oct  2 20:10:48 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Oct  2 20:11:06 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Oct  2 20:11:22 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Oct  2 20:11:36 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
Oct  2 20:11:52 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Oct  2 20:12:06 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
Oct  2 20:12:27 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Oct  2 20:12:42 Cuddy dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
```

These are pretty long intervals, but I don't really know if that's what's making the system boot so slowly.

I'm also seeing some things like this:

```
Oct  2 20:10:15 Cuddy dhclient: Listening on LPF/wlan0/7c:e9:d3:4c:09:9e
Oct  2 20:10:15 Cuddy dhclient: Sending on   LPF/wlan0/7c:e9:d3:4c:09:9e
Oct  2 20:10:15 Cuddy dhclient: Sending on   Socket/fallback
Oct  2 20:10:15 Cuddy dhclient: DHCPRELEASE on wlan0 to 10.255.240.0 port 67
Oct  2 20:10:15 Cuddy dhclient: send_packet: Network is unreachable
Oct  2 20:10:15 Cuddy dhclient: send_packet: please consult README file regarding broadcast address.
```

Any suggestions as to what to try next?

Thanx in advance,

Brian Myers

---

### Post by tarkawebfoot on 2012-10-03
Update:

I had trouble with Wicd, so I uninstalled and installed network-manager. That was a complete disaster. Couldn't get it to recognize networking services at all.

I uninstalled and re installed Wicd, and all is well. The problem I was having before is fixed.

Never the less, it's still really slow to boot. I believe this is because of the timeout set on the ethernet port. While messing around with network manager, I restarted networking (sudo /etc/init.d/networking restart); this took a good 2-3 minutes. Does seem to be faster now.

Just wish I knew why the install from the Live CD worked so much better. Unfortunately, that's not the only thing that's not working well. 

Brian

---

### Post by tarkawebfoot on 2012-10-03
Update 2:

Rebooted. Problem is NOT solved. It's just as slow to boot as it was before. :(

Brian

---

### Post by tarkawebfoot on 2012-10-04
Well, no one seems to know anything about this, and since the networking is working better now, I don't think it's a network issue, so I'll try asking this on a different forum.

Brian

---

### Post by tarkawebfoot on 2012-10-04
Never mind. Fixed it. You rock Amjjawad! :guitar:

First I installed bootchart. Looking at the png generated, I saw that all the time was being spent in plymouth and network initialization. While examining plymouth I found it was closely related to terminal mode setting.

So I added the nomodeset parameter to the kernel command line while booting. This time while booting I had the Ubuntu splash screen, and I saw that the time was spent with "Waiting for network configuration" and "Waiting up to 60 seconds for network configuration".

Googling that I found this post by Amjjawad:

["HOWTO Fix "waiting for network configuration" Problem"]("http://ubuntuforums.org/showpost.php?p=11835741&postcount=448")

That fixed the problem. Now boot is as fast as it always was. I had lines to setup the eth0 interface in my /etc/network/interfaces, almost certainly because I was plugged in wired when I installed from the alternate CD.

Huh, so it was network related after all.

Brian

---

