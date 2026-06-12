---
title: "Intrepid upgrade broken my friend's ethernet"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by joelholdsworth on 2008-12-17
Hi All,

I have a friend with an Dell Inspiron 9000. She was running Hardy, and everything was working very happily, but after upgrading to Intrepid her laptop is unable to connect to her wired network. It gets stuck trying to do DHCP process through NetworkManager. I began to make a series of tests:

1. Static IP - FAILS
2. Connecting via dhclient - FAILS
3. Tested with old kernel left over from Hardy - FAILS
4. Tested on a different cable and router socket - FAILS
5. Tested with Intrepid live disk - FAILS
6. Tested with Hardy live disk - WORKS
7. Testing with Intrepid over a wireless connection - WORKS
8. Testing with Intrepid on a different wired network - here in my house - WORKS
9. Tested with Windows XP - WORKS
10. Tested a different WinXP laptop on that cable - WORKS

I'm don't understand what's going on here. Both Intrepid and Hardy use the b44 driver, so if the driver's the same, I don't understand why the laptop won't connect, especially when there are no problems in when I test the laptop in my house rather than hers.

Does anyone have any suggestions?

---

### Post by Ayuthia on 2008-12-17
> **joelholdsworth said:**
> Hi All,

I have a friend with an Dell Inspiron 9000. She was running Hardy, and everything was working very happily, but after upgrading to Intrepid her laptop is unable to connect to her wired network. It gets stuck trying to do DHCP process through NetworkManager. I began to make a series of tests:

1. Static IP - FAILS
2. Connecting via dhclient - FAILS
3. Tested with old kernel left over from Hardy - FAILS
4. Tested on a different cable and router socket - FAILS
5. Tested with Intrepid live disk - FAILS
6. Tested with Hardy live disk - WORKS
7. Testing with Intrepid over a wireless connection - WORKS
8. Testing with Intrepid on a different wired network - here in my house - WORKS
9. Tested with Windows XP - WORKS
10. Tested a different WinXP laptop on that cable - WORKS

I'm don't understand what's going on here. Both Intrepid and Hardy use the b44 driver, so if the driver's the same, I don't understand why the laptop won't connect, especially when there are no problems in when I test the laptop in my house rather than hers.

Does anyone have any suggestions?

Have you checked to see if the b44 module is loaded:
```
lsmod | grep b44
```

If it is not, you can load it:
```
sudo modprobe b44
sudo /etc/init.d/networking restart
```

If you need more help, please let us know what wireless card she has.  I just want to be sure that I don't cause any problems with it also.  Sometimes ssb creates problems with other modules.

I am not for sure if they are backporting the b44 module or not.  I know that they are making some changes with the loading sequence of the b44 module because of the Broadcom STA (wl) module.  I am just not for sure about how they are doing it.

---

### Post by joelholdsworth on 2008-12-17
I can't check the module loading thing right now. But I got the b44 info with ```
sudo ethtool -i eth0
``` I assume that if ethtool reports the driver status, that implies that the kernel module is loaded.

I forget exactly what wireless driver the system uses. IIRC it's an independent chipset.

---

### Post by ackattack on 2008-12-17
Intrepid broke the wired network on BOTH my machines using my Belkin Router (both were working with Hardy).  Works with my D-Link router (!!).  Two completely different network chipsets.  Network Manager seems to be the culprit.  The solution for me was to add the lines;

```
auto eth0
iface eth0 inet dhcp
```

to /etc/network/interfaces and reboot.

however this makes Network Manager angry and I have DNS problems on the laptop which also has a wireless card, I believe due to a conflict with Network Manager.  Other people report success replacing Network Manager with WICD.  I've yet to try it.

EDIT:

Since posting this, I decided to try WICD on the laptop - totally painless.  Download the .deb from [the SouceForge download page]("http://sourceforge.net/project/showfiles.php?group_id=194573"), remove Network Manager using Synaptic, then install the .deb using GDebi.

Worked like a charm, wireless and wired now co-existing peacefully.

---

### Post by joelholdsworth on 2008-12-18
Hmm ok, I will try this out. Do you know if a bug has been filed for this?

---

### Post by ackattack on 2008-12-18
I don't know if a bug report has been filed.  I'm a relative newb but I know from searching that a lot of people in the forum have been having problems with Network Manager and wired connections.  In my case the error shows up in the /var/log/deamon.log as:
```

Dec 17 17:57:12 dan-laptop NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Dec 17 17:57:12 dan-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 17 17:57:12 dan-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 17 17:57:12 dan-laptop dhclient: All rights reserved.
Dec 17 17:57:12 dan-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 17 17:57:12 dan-laptop dhclient: 
Dec 17 17:57:12 dan-laptop NetworkManager: <info>  dhclient started with pid 5176 
Dec 17 17:57:12 dan-laptop NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 17 17:57:12 dan-laptop NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Dec 17 17:57:12 dan-laptop dhclient: Listening on LPF/eth0/00:0d:60:2d:b8:d0
Dec 17 17:57:12 dan-laptop dhclient: Sending on   LPF/eth0/00:0d:60:2d:b8:d0
Dec 17 17:57:12 dan-laptop dhclient: Sending on   Socket/fallback
Dec 17 17:57:16 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Dec 17 17:57:16 dan-laptop dhclient: send_packet: Message too long
Dec 17 17:57:19 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Dec 17 17:57:19 dan-laptop dhclient: send_packet: Message too long
Dec 17 17:57:26 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
Dec 17 17:57:26 dan-laptop dhclient: send_packet: Message too long
Dec 17 17:57:36 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 17 17:57:36 dan-laptop dhclient: send_packet: Message too long
Dec 17 17:57:51 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
Dec 17 17:57:51 dan-laptop dhclient: send_packet: Message too long
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5176 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Dec 17 17:57:57 dan-laptop NetworkManager: <info>  Activation (eth0) failed. 
```

As you can see, the DHCP process failed due to "Message too Long" from the dhclient.  Now the weird thing is that WICD also uses the "dhclient" for DHCP yet it works fine, as shown below after installation of WICD.  So beyond this I'm stumped and don't really know enough to file a bug report.

```
Dec 17 18:55:42 dan-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 17 18:55:42 dan-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 17 18:55:42 dan-laptop dhclient: All rights reserved.
Dec 17 18:55:42 dan-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 17 18:55:42 dan-laptop dhclient: 
Dec 17 18:55:43 dan-laptop dhclient: Listening on LPF/eth0/00:0d:60:2d:b8:d0
Dec 17 18:55:43 dan-laptop dhclient: Sending on   LPF/eth0/00:0d:60:2d:b8:d0
Dec 17 18:55:43 dan-laptop dhclient: Sending on   Socket/fallback
Dec 17 18:55:44 dan-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Dec 17 18:55:45 dan-laptop avahi-daemon[4667]: Registering new address record for fe80::20d:60ff:fe2d:b8d0 on eth0.*.
Dec 17 18:55:45 dan-laptop dhclient: DHCPOFFER of 192.168.2.53 from 192.168.2.1
Dec 17 18:55:45 dan-laptop dhclient: DHCPREQUEST of 192.168.2.53 on eth0 to 255.255.255.255 port 67
Dec 17 18:55:46 dan-laptop dhclient: DHCPACK of 192.168.2.53 from 192.168.2.1
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.53.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: New relevant interface eth0.IPv4 for mDNS.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Registering new address record for 192.168.2.53 on eth0.IPv4.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Withdrawing address record for 192.168.2.53 on eth0.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Leaving mDNS multicast group on interface eth0.IPv4 with address 192.168.2.53.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Interface eth0.IPv4 no longer relevant for mDNS.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.2.53.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: New relevant interface eth0.IPv4 for mDNS.
Dec 17 18:55:46 dan-laptop avahi-daemon[4667]: Registering new address record for 192.168.2.53 on eth0.IPv4.
Dec 17 18:55:46 dan-laptop dhclient: bound to 192.168.2.53 -- renewal in 917925501 seconds.
```

---

### Post by joelholdsworth on 2008-12-18
Yes I got that message too long stuff when calling dhclient on the command line. I guess this must be a dhclient bug! - I will investigate.

---

### Post by joelholdsworth on 2008-12-18
Hmm it looks like this bug is back: [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/61989) - it comes with a workabout!

---

### Post by ackattack on 2008-12-18
Hmmm... I'd say that's it!  Come to think of it, I recall seeing that ifconfig was reporting an MTU of 64 when I was trying (unsuccessfully) to connect after the upgrade to Intrepid.  I knew it was a suspicious value but not how to fix it.

Now, using WICD, the MTU is set correctly to 1500.  Perhaps WICD is smart enough to override the bogus MTU in dhclient while Network Manager is not?  Just guessing here.

I think if this was fixed it would solve a lot of heartache for a lot of people.

---

