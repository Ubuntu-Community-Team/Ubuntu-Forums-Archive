---
title: "Can't connect through wireless, Acer Aspire 5536-5519, Ubuntu-9.04"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by Inder on 2009-10-14
Hello,

I can't connect to my wireless network at home. I have been posting around various forums, but have never gotten any success at solving my problem (nor actually identifying what's wrong). I'll try to include in this post ALL information that could be usefull:

First of all, when I click the network manager (top right) and select my wireless network (called "Network", and shown with full signal strength), the network manager icon becomes two greens dots with a blue "shooting star" moving around in circles behind them. Then, at some point, the icon comes back to normal and a little box appears saying "Wireless Network Disconnected". At school, the wireless connection works fine, and at home, I can connect to my wireless network on my other computer, so I guess that rules out any hardware problems.

This is what I get when I use the **iwconfig** command:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

This is what I get when I use the **ifconfig** command:
```

eth0      Link encap:Ethernet  HWaddr 00:1f:16:b4:25:1b  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:feb4:251b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47424039 (47.4 MB)  TX bytes:2597745 (2.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:17:c4:a0:ee:38  
          inet6 addr: fe80::217:c4ff:fea0:ee38/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:330 (330.0 B)  TX bytes:3410 (3.4 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-17-C4-A0-EE-38-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

This is what I get when I use **lspci -v | less** (cropped):
```

03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
        Subsystem: Acer Incorporated [ALI] Device 0207
        Flags: bus master, fast devsel, latency 0, IRQ 2300
        Memory at f0300000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: tg3
        Kernel modules: tg3

06:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a32:0303
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f0400000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```

Is there anything in the above which I could remove for clarity?
Or better, is there anything else I could add to clarify my situation?

By the way, I tried installing Wicd, but it couldn't get me connected either.

Thank you for any help

Shawn

---

### Post by Metaljaz on 2009-10-16
Just a few questions to narrow some things down. Is your wireless at home a secured network? When you left click on the network icon is your home network listed?

---

### Post by Inder on 2009-10-16
yes, I see it there and the "signal strength bar" alongside it looks full (very strong).

---

### Post by wilee-nilee on 2009-10-16
Can you connect with Etho and have you tried a reinstall of Network Manager if you can use Etho.

---

### Post by PrePenguin on 2009-10-16
I am running an Acer Aspire 5536 .. Try disabling the lan in the bios and then see if it detects the wireless connection.. Also are you using the Broadcom lan with the Atheros wireless? Which is whats in my system.. I had no problem with mine being detected however i know sometimes the Lan connection and the wireless bump heads for a IRQ resource on ubuntu 9.04 so you have to disable the lan inside the bios..

---

### Post by Inder on 2009-10-17
@wilee-nilee: Yes, I am presently connected to eth0, the wired connection works perfectly. It's just a shame that my cable is so short and I always have to sit right next to the router:p I just tried re-installing network-manager-gnome and network-manager, and still I can't connect through wireless..

@PrePenguin: I tried your solution, but I couldn't find any mention of LAN in the bios.. The only thing that seemed related to networking was that "booting in network mode" was enabled, or something like that... Also, how can I tell if I'm using the "Broadcom lan with the Atheros Wireless"? I don't actually know what that is..

I am detecting my wireless network though, and getting a strong signal too! It's right there in the list when I click on the network manager.

---

### Post by Metaljaz on 2009-10-17
When you look in the network manager and see your network are you clicking on the network to select it?

---

### Post by Inder on 2009-10-17
@Metaljaz: Yes, I click on it to select it, then the network manager icon becomes two greens dots with a blue "shooting star" moving around in circles behind them. Then, at some point, the icon comes back to normal and a little box appears saying "Wireless Network Disconnected".

---

### Post by PrePenguin on 2009-10-17
Sounds like a router problem with the wireless maybe reset your router but the router is kicking you off maybe? Is this router keyed? WEP?

---

### Post by Metaljaz on 2009-10-17
I have read that installing the below could solve your problem:

# For Ubuntu 9.04 Jaunty users From the terminal window type:

sudo apt-get install linux-backports-modules-jaunty

restart computer and check wireless again

---

### Post by Inder on 2009-10-17
Oh my god you guys don't know how releived I am to have wireless now after more than a month of forums/phone support from D-Link/superuser/conferences/etc.

I was in the midst of answer the two last posts when I decided to call D-Link once more. They made me re-configure my router... again. Then after rebooting my modem and router (again) it works!!

I don't quite understand it, but my best bet would be that installing linux-backports-modules-jaunty (as suggested by Metaljaz) did the trick but needed a modem reboot and router reboot to work...
What do you guys think?

Anyhow thank you all very much for your help

---

### Post by sudharma on 2009-10-18
I have a Desktop Pc running Win-XP & Linux Mint "Gloria" dual booting, 2nd note book with Ubuntu & Vista Home, and a 3rd notebook running only Vista Home Premium. The Desktop pc connect to the Internet via lan cable Wireless Router (D-Link DIR300) & cable Modem (MT-882). Both the note books connects thro' wireless router DIR-300.All PCs were connecting to the Internet on both Linux and Win system without any problem till the Broadband service providers server crashed a few days back. Since then I am unable to connect to internet from the Ubuntu and Linux system. Win XP and Vista connects ok through wireless and cable.
today morning the Linux system internet problem resolved itself without any intervention. But I am still unable to access the internet from ubuntu on my 2nd PC. I would appreciate any help in solving this problem. I could no find any solution from the posts. I am very new to the Linux system

---

### Post by Inder on 2009-12-11
Here's a good one.

I just updated my system to Ubuntu 9.10 - Karmic Koala, and now the wireless won't work again!

Taking a wild guess, I tried installing linux-backports-modules-karmic, but that doesn't work..

What do you say?

---

### Post by Metaljaz on 2009-12-11
try shutting down both the modem running into the router and the router. Wait 20 secs and then restart the modem, wait another 10 seconds and plug in the router. Now check to see if the connection was detected.
Also, check to make sure that you did not accidentially turn off your wireless with a button on the outside of the computer or pushing a key.

If none of these helps tell us a little more about what is going on.

---

### Post by Inder on 2009-12-11
That's a quick reply!

So funny thing, I uninstalled everything called linux-backports-....., rebooted, and now wireless works!
I just hope it's gonna last..

Would you know why uninstalling something would make it work? It just doesn't sound right.

Thanks a lot for your reply though, although I've been power-cycling my modem and router all day to no avail :p)

Shawn

---

### Post by Metaljaz on 2009-12-11
Since it was the newest version maybe install the backports woke the wireless up and uninstalling really didn't matter. Did everything work fine after a system restart?

---

### Post by Inder on 2009-12-11
I unistalled the backports, still nothing worked.
Then I restarted the system, and then it started working

---

