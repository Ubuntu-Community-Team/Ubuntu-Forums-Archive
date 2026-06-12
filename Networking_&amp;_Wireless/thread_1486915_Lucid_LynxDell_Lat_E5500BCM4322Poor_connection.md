---
title: "Lucid Lynx/Dell Lat E5500/BCM4322/Poor connection"
date: 2010-05-18
forum: Networking &amp; Wireless
---

### Post by Linoobius on 2010-05-18
Greetings and thanks for taking the time to read this, I have a Dell Latitude E5500 with the Broadcom BCM4322 wireless chipset. Prior to the 10.04 LTS upgrade I was running 9.10 over a wireless connection with no problems whatsoever. Since the upgrade the wireless connects fine and never reports dropping but data transfers both up and down only work in short bursts. For example if I download a file or run a speed test at dslreports I can watch my nic traffic increase then drop to zero for 10 seconds or so then rise up for a couple of seconds then drop back to zero. This is very frustrating and makes the connection next to useless.

I initially assumed it was a router problem and replaced the router but when there was no change I began looking at the wireless connection. I can reboot 9.10 and the problem disappear so I know it's not a hardware issue. A hardwire connection also works perfectly so it's only the wireless that's affected. I have sat 10' from the router with the same results so it's not a connection quality issue. I removed and reinstalled the STA driver with no effect. I downloaded the latest driver from the Broadcom site and compiled on my laptop and replaced the wl.ko with the one I compiled and no change. Any assistance you can offer will be greatly appreciated. Below is some information which may be helpful.

```
steve@Loki:~$ lspci -nn | grep Broadcom
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5756ME Gigabit Ethernet PCI Express [14e4:1674]
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
steve@Loki:~$ 
```

```
steve@Loki:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:189  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

pan0      no wireless extensions.

steve@Loki:~$ 
```

```
steve@Loki:~$ ifconfig eth1

eth1      Link encap:Ethernet  HWaddr 00:23:4d:d9:d6:37  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fed9:d637/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59382 errors:1 dropped:0 overruns:0 frame:77977
          TX packets:43794 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74738840 (74.7 MB)  TX bytes:5520062 (5.5 MB)
          Interrupt:17 Base address:0xc000

steve@Loki:~$ 
```

```
steve@Loki:~$ lsmod | grep wl
wl                   1964968  0 
lib80211                6119  2 lib80211_crypt_tkip,wl
steve@Loki:~$ 
```

```
steve@Loki:~$ sudo lshw -C network
[sudo] password for steve: 
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:23:4d:d9:d6:37
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.2.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5756ME Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 00
       serial: 00:23:ae:0a:67:70
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5756m-v3.11 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68f0000-f68fffff
steve@Loki:~$ 
```

```
steve@Loki:~$ uname -a
Linux Loki 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
steve@Loki:~$
```

Cleaned up the post some, thanks for any help!

---

### Post by JohnDoe365 on 2010-05-19
You are not alone and very likely speed will back to normal, when you disable wireless and re-enable wirells. This should bring back speed to normal, but inly for some varying time until it drops of again.

See [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3)
and try to raise awareness by commenting on launchpad bug 
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936)

Johann

---

### Post by Linoobius on 2010-05-19
> You are not alone and very likely speed will back to normal, when you  disable wireless and re-enable wirells. This should bring back speed to  normal, but inly for some varying time until it drops of again.I tried disabling and re-enabling the wireless with both software and hardware switches. This caused the connection to stabilize long enough for me to get 1 good speed test from DSLreports, on the second attempt to run the test the connection was back to being slow and bursty with long (5 - 30sec) intervals of 0kbps traffic.

I tried setting a fixed rate with "sudo iwconfig eth1 rate 54M" but that had no effect. The thread you referenced seems to center on 802.11 N connections and they report some success by disabling the N but router here is only b/g. Is there a way to disable the N capability of the BCM4322 or would that be ineffective as well?

I also tried "sudo iwconfig eth1 power off" and that does not seem to affect the situation either.

I will post on your launchpad bug report.

Thanks

---

### Post by Linoobius on 2010-05-19
Well, I have removed the Gnome network-manager and installed Wicd available [here]("http://wicd.sourceforge.net/") or in the Ubuntu repositories "sudo apt-get install wicd" and so far it seems to be working much better. Even though the Wicd documentation said that it would remove network-manager, I had to manually remove network-manager and reboot before Wicd would connect but after restarting Wicd came up and connected fine. I will hold off on marking the thread solved for a couple more hours just to make sure. Even though it's not a true solution, so far it seems to be working fine. Will update again after more testing.

---

### Post by JohnDoe365 on 2010-05-19
Thank you for tryong out. Yes, you're right, disabling the N part of your router does not help nor disabling auto sensing or adpative speed negotiation.

Especially disabling IPv6 has no effect, as long as you have no IPv6 aware router.

It's interessting though that wcid helps ... please come back later to affirm that with this network manager it's back to normal.

---

### Post by Linoobius on 2010-05-20
Well, I used the connection today early in the day and all seemed well. I launched my Windows VM in vbox and connected to a VPN and the laptop sat for many hours without being touched. When I came back to it, it was seriously hosed up, I couldn't  CTRL ALT BKSP to kill the xsession or get a command prompt up to poke around, CPU was at about 40%. I was in a hurry so just rebooted the machine and all seemed okay, haven't check the vm to see if it was corrupted and I don't know if this was in any way connected to the network but it's never done anything like that before. Will try again tomorrow and see how it goes, I'll try to use it more throughout the day this time to keep an eye on it. Jury still out...

---

### Post by Happibun on 2010-09-05
Well, FWIW I seem to have had the same problem.

I have a Dell Latitude 120L which as the same type of Broadcom wireless chipset. I've been running various flavours of Ubuntu on it since Gutsy. My main problem had always been the wireless connection, and with each new 'buntu, I always had to revert to WiCd to get it to play. 

I run plenty of other laptops and desktops on this network. The signal where this particular one resides is very good, and I was reluctant to upgrade from Karmic until I knew all the niggles had been ironed out of the Lynx. In the end I needed to upgrade the HD, and so went for a completely fresh install.

Ok, so I had to plug in to the ethernet connection to get all of the updates - nothing new there, particularly since the Broadcom drivers always need updating. Once done and rebooted, I was delighted to see network manager had found my network, and after I told it how, connected to it without a murmer. It was fast too. At last! A LTS 'buntu that just worked. Joy.

Ten minutes later and the connection had dropped. What's more, I could not get it to reconnect at all. Nothing wrong with the router, all the other machines sat online just fine, but this one keeps bouncing off, and only a reboot seems to do the trick. 

So, it looks like I'm going to have to go back to WiCd unless there is a hack around it. I've not managed to find an awful lot out there about it, most people do what I'm about to. Is there a different work around? How have you been getting on Linoobius?

---

