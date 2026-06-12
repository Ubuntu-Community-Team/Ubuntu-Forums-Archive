---
title: "Network Manager keeps asking for WPA key even though its correct"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by justin23 on 2009-05-03
Been tryin to get online now for four days. I've tried just about everything. I haven't gotten 1 reply to any of my posts. Installed ndiswrapper and ndiswrapper utilities. Tried configuring my /etc/network/interfaces file. I've tried configuring the wpa_supplicant.conf file, all to no avail. Running a dell inspiron 1501. 32 bit jaunty. Can't connect to non broadcasting signal. If anyone has any ideas I want to hear. Thanks in advance.

justin@justin:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
justin@justin:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:19:b9:6d:39:99
inet addr:192.168.2.4 Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::219:b9ff:fe6d:3999/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2538 errors:0 dropped:0 overruns:0 frame:0
TX packets:2494 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:2331671 (2.3 MB) TX bytes:419036 (419.0 KB)
Interrupt:21

eth1 Link encap:Ethernet HWaddr 00:1a:92:b1:6c:24
inet6 addr: fe80::21a:92ff:feb1:6c24/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:480 (480.0 B) TX bytes:480 (480.0 B)

pan0 Link encap:Ethernet HWaddr 72:bf:4b:47:d0:66
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

justin@justin:~$ iwconfig
lo no wireless extensions.

eth1 IEEE 802.11 Nickname:""
Access Point: Not-Associated
Link Quality:5 Signal level:199 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

eth0 no wireless extensions.

pan0 no wireless extensions.

justin@justin:~$ lshw -C network
WARNING: you should run this program as super-user.
*-network
description: Wireless interface
product: BCM4311 802.11b/g WLAN
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:05:00.0
logical name: eth1
version: 01
serial: 00:1a:92:b1:6c:24
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11
*-network
description: Ethernet interface
product: BCM4401-B0 100Base-TX
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
logical name: eth0
version: 02
serial: 00:19:b9:6d:39:99
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.4 latency=64 module=ssb multicast=yes
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 72:bf:4b:47:d0:66
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
justin@justin:~$
Last edited by justin23; 2 Minutes Ago at 11:24 PM..
justin23 is online now Report Post   	Edit/Delete Message

---

### Post by JK3mp on 2009-05-03
Your card should be supported...has it ever worked? Will it connect w/o the wpa key?

---

### Post by justin23 on 2009-05-03
yup working with 8.1 no problem.

---

### Post by justin23 on 2009-05-03
it keeps asking me for wpa key

---

### Post by justin23 on 2009-05-03
Any idea why my posts aren't showin up as new?

---

### Post by papangul on 2009-05-04
If I were you I would first replace NM with WICD, then think of anything else:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by sgosnell on 2009-05-04
Your posts don't show up as new to you because you posted them and presumably know about them.

I'm assuming you mean that your router is not broadcasting the SSID.  Exactly how have you tried to connect to it?  I would suggest turning the SSID broadcast on long enough to try to connect, then turning it back off.

---

### Post by justin23 on 2009-05-04
Installed wicd and now it won't connect at all

---

### Post by justin23 on 2009-05-04
will do.  i really don't think its a driver issue because i can see all the other wifi networks around me.  it must be a problem with wpa. will try to broadcast ssid and connect.

---

### Post by adambh on 2009-05-04
try resetting the router to factory default and redoing your setup

---

### Post by justin23 on 2009-05-04
its not an issue with the router.  all the other computers in the house connect to it just fine.  we have five computers in the house with internet access. the only machiene who can't connect is my laptop with jaunty.  it must have to do with the wpa. some setting isn't configured correctly

---

### Post by sgosnell on 2009-05-04
Well, I don't have an explanation.  WPA works on my Asus, and it seems to work for most users.  I don't have ndiswrapper installed, or anything else other than the stock Jaunty.  I do have the .29 kernel installed, but wireless works fine on the standard .28 kernel.

---

### Post by promet on 2009-05-05
Hey Justin23,

I am having similar issues and, for what it is worth, when I am unconnected wirelessly and NM keeps popping up the WPA authentication login with the correct key already entered like you mentioned; I've found that a "cold-restart" of the window manager with "ctrl-alt-backspace" often resets NM and allows it make the connection cleanly.

Another thing you may want to look into; I have discovered, on my wired connection, that since I've upgraded to 9.04 there seems to be some sort of conflict between NM and "ifup". I am not quite sure of the details, but NM seems to be erasing my DNS Server entries from "/etc/resolv.conf". Check that file to make sure that your DNS servers are persisting from boot to boot, and indeed at any time where mysterious network dropouts occur. I think there is some network weirdness that needs sorting out with 9.04.

Some very inelegant solutions, but hopefully helpful until we can sort out what's going on. I hope these are useful to you.

Cheers,
promet

---

### Post by MFORE on 2009-05-05
I've been having the same problem. I've gotten as far as having my wifi adapter (linksys wusb11v4) working using ndiswrapper. It picks up the local wifi networks, however, when it comes to connecting to my wireless (WPA encripted) it rejects the correct password. Still fairly new to linux, but I'm fairly determined to get this working.

---

### Post by HumbleGod on 2009-05-05
Same problem here. I can connect to non-secured and WEP networks just fine, but WPA and WPA2 simply won't connect, even when the password is 100% correct. I was using Ubuntu-Eee (based on Hardy) on my Asus Eee 1000 prior to upgrading, and connections to WPA were fine, so I'm certain this isn't a pure hardware thing.

Judging from the number of posts on this site, the wireless networking on Jaunty is all sorts of screwy--some people can't connect at all, some people just can't connect to secured connections. I'm hoping there's a common culprit that can be found soon, but in the meantime I'm forced to either downgrade of forswear WPA connections altogether.

---

### Post by Kobalt on 2009-05-05
Are you using a WPA or WPA2 key? 
I've had lots of trouble connecting to my WPA2 network using the included drivers for my wireless card (rt2860).

---

### Post by MichaelSM on 2009-05-05
Post deleted.

---

### Post by justin23 on 2009-05-05
I believe its a wpa key

---

### Post by HumbleGod on 2009-05-05
My problem has been with both WPA (a friend's house) and WPA2 (on campus). Both worked fine on my previous Hardy-based distro. For both, only the first green light shows up when I try to connect--it never completes the handshake.

---

### Post by iain_b on 2009-05-05
Yep, I've this problem too (card - rt2860). Didn't work on intrepid, I hoped it would work on jaunty, it doesn't. Not just a ubuntu problem, though. I've tried OpenSuse 11.1 and its the same problem, or so it seems.  I don't know enough to spot the common link though...

---

### Post by promet on 2009-05-06
Hey guys,

I got mine working. In my case it was some issue with ndiswrapper. After fidgeting around with everything else, I decided to try a driver reinstall, i.e.:

```
$ sudo ndiswrapper -r your-windows-wireless-driver.inf
```

removing your wireless driver, then:

```
$ sudo ndiswrapper -i your-windows-wireless-driver.inf
```

The simple removal and reinstall caused my Netmwork Manager to stop asking for the WPA and connect right away, thus this post ;)

Hopefully this will be useful,
promet

---

### Post by Emmoth on 2009-05-07
I got the same problem, right after I did a fresh install of 9.04 with the ext4. 

It worked like a charm in 8.10 :/

I got the ralink 2860 card in my Asus 1000H

my lsmod looks like this:

[B]rt2500pci  23936   0
rt2x00pci  15615   1 rt2500pci
rt2x00lib   37888   2 rt2500pci,rt2x00pci[/B]

not sure if that has somthing to do with it.

any help is appreciated

---

### Post by HumbleGod on 2009-05-08
promet, I'm glad you got yours working. Unfortunately, my laptop does not have ndiswrapper or a Windows driver installed, so this won't work for me.

FWIW, I'm using an Asus Eee 1000 with the RaLink RT2860, like many of the others here.

Edit: And to be clear, I'm able to connect to open wireless, able to connect to WEP. Not able to connect to WPA or WPA2.

---

### Post by promet on 2009-05-08
Well it looks like I spoke too soon. It has crapped out again, which is upsetting. I mean it was working great, hot rocks; now? Kaput!

The fact that I found a "fix", which worked for, like, two days, then crapped out and is now stubbornly refusing to work, makes me really think that there is something dynamic going on in the background here. Also, upsetting.

Now it seems, instead of a simple misconfiguration, that this issue is a "moving target" in the 9.04 networking system, which is always bad, on account of the troubleshooting becomes all that much more difficult. 

So, my hat's back in the ring, sadly, if anyone has any revelations let me know.

Signed,
Wronged by my squirrely network :(

---

### Post by dmp1ce on 2009-05-08
> **HumbleGod said:**
> promet, I'm glad you got yours working. Unfortunately, my laptop does not have ndiswrapper or a Windows driver installed, so this won't work for me.

FWIW, I'm using an Asus Eee 1000 with the RaLink RT2860, like many of the others here.

Edit: And to be clear, I'm able to connect to open wireless, able to connect to WEP. Not able to connect to WPA or WPA2.
I have the exact same problem with an Acer Extensa 4630Z which has a RaLink RT2860 network controller card.

Edit: I found a bug relating to the RT2860 driver.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210725?comments=all)

---

### Post by dmp1ce on 2009-05-08
For what it's worth I was able to download, compile and install the latest version of the RA2860 driver located [here]("http://www.ralinktech.com.tw/data/drivers/2009_0424_RT2860_Linux_STA_V2.1.1.0.tgz").  I'll list out the steps for anyone who wants to try.  BTW, my system is Ubuntu 9.04 on an Acer Extensa 4630Z.

First, download and extract the .tgz somewhere.  Then open a terminal and change directories to the extracted directory.  For me it was ~/src/2009_0424_RT2860_Linux_STA_V2.1.1.0.

Edit the file config.mk located in os/linux, which was ~/src/2009_0424_RT2860_Linux_STA_V2.1.1.0/os/linux/config.mk for me.  Change the line HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y and the line HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Then follow these steps for compiling and installing.

```
sudo make
sudo make install
[FONT=courier new]modprobe rt2860sta
[/FONT]reboot #restarting the system was necessary for me, there is probably a better way
```After that, the card should be able to connect using WPA or WPA2.  My connection was WPA2.  I am also using wicd instead of network manager but I don't know if that will make a difference.

I hope that helps!

---

### Post by promet on 2009-05-08
Update,

Okay so I've got my wireless working, for the time being.

To recap I had been having the stated thread problem, Network Manager Keeps Asking for WPA key, etc.

After trying out Ndiswrapper configs, and module level driver complications. I stumbled across a post (sorry didn't bookmark it, not on Ubuntu Forum though) that mentioned that the Network Manager and it's corresponding nm-applet (the, in my case, Gnome Panel doohickey that manages your network connections) no longer uses "/etc/network/interfaces" for configuration information.

I did not know this, but figured if that's true, maybe that file is causing some conflict. So, I went into "/etc/network/interfaces" and commented out (by added preceding "#" signs on each line) all entries other than the "lo" (LO) entry.

I cannot speak to the details of why, but this worked for me. I rebooted, and the wireless kicked right back on, working like it had in 8.10.

I am guessing that in some hardware configurations (again, I am on a Dell Latitude C640 Laptop with a Linksys WPC54G Wireless pcmcia card) that the "/etc/network/interfaces" file somehow interferes with the, apparently now default, Network Manager method. Again, this is only a guess. 

I hope this provides some insight, for the time being I'm going to enjoy this wireless connectivity before it breaks, :P

Alas, 802.11 is fleeting!

P

---

### Post by HumbleGod on 2009-05-08
I think this Launchpad page is more relevant (it's more recent than yours, dmp1ce, and acknowledges that a fix hasn't really been released): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891)

I'm really reluctant to try any triage right now, as I'm afraid of losing network connectivity altogether (I've had plenty of nightmares with Ubuntu and wireless in the past). Hopefully the fix dmp1ce mentions, or perhaps another one, will make it into the official update stream soon....

---

### Post by promet on 2009-05-08
Roger that. This does seem to work though (for my configuration at any rate) and is very quick to implement/reverse for anyone who would like to to give it a try.

:popcorn:

---

### Post by HumbleGod on 2009-05-20
> **promet said:**
> Roger that. This does seem to work though (for my configuration at any rate) and is very quick to implement/reverse for anyone who would like to to give it a try.

Works for mine as well, now that I've grown a pair and gone through with it! I recommend that patch to anyone with an RT2860 driver, which probably includes anyone with an Eee 1000 (linux).

---

