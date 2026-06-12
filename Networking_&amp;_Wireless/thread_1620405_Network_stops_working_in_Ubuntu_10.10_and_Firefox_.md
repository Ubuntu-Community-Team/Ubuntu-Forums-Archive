---
title: "Network stops working in Ubuntu 10.10 and Firefox randomly stops working"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by maverick280857 on 2010-11-13
Hi,

I'm running Ubuntu 10.10 Maverick Meerkat 64-bit on my desktop with a wired internet connection (with no firewall). For the past 2 days, I have observed that

1. Firefox randomly throws up errors like "Problem loading page" whenever I click on a hyperlink. When I click on Reload, the page loads up just fine. This has been happening a lot recently..and I do not remember updating anything consciously. By the way, ipv6 is disabled in Firefox.

2. The network stops working all of a sudden (usually indicated by the Firefox error). The Autho Eth0 indication is active, but I am unable to connect to any external machine.

3. Needless to say, this error is manifesting itself in apt-get as well. I get "something wicked happened" errors all the time, and am unable to download or install anything.

That this is not a problem with the ISP is obvious because I also have Windows (from which I'm typing this, ironically), which is able to access the internet.

Is this a bug in Ubuntu 10.10? I really don't want to downgrade (referring to a thread regarding wireless issues) so any advice other than that is welcome :)

Thanks in advance.

---

### Post by grahammechanical on 2010-11-13
Is IPv6 disabled in network manger? See the IPv6 Settings tab under Edit Connections. Set the mode to ignore. Might help.

Regards.

---

### Post by maverick280857 on 2010-11-13
IPv6 is indeed disabled. I am back in Windows...now, I am unable to access the network in Ubuntu at all. No browser works, nor does ping.

If by Network manager you meant

System -> Preferences -> Network Connections -> Auto eth0 -> Edit -> IPv6 settings -> Method = Ignore

then yes. I could not find a separate Network Manager utility anywhere and system-config-network is not a recognized command on my system.

---

### Post by maverick280857 on 2010-11-14
I tried resetting the network settings, removing and adding the network adapter. I have two adapters on my MB, so I tried connecting it to another one, in vain.

Here's the output from ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:24:1d:15:ff:97  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe15:ff97/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49767 (49.7 KB)  TX bytes:64674 (64.6 KB)
          Interrupt:48 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:15:ff:95  
          inet6 addr: fe80::224:1dff:fe15:ff95/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11358 (11.3 KB)  TX bytes:21155 (21.1 KB)
          Interrupt:49 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:70 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5288 (5.2 KB)  TX bytes:5288 (5.2 KB)

```

and here's a portion of the output from lspci (if its any help):

```

[B]0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0b:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)[/B]
0c:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

```

So right now, absolutely no network works. Any ideas, short of reinstalling Ubuntu? :confused:

PS -- Already tried [https://help.ubuntu.com/10.10/internet/C/troubleshooting-lan.html](https://help.ubuntu.com/10.10/internet/C/troubleshooting-lan.html). Ping does not work.

---

### Post by dineshs on 2010-11-14
Can you ```
ping 4.2.2.1 -c3
```

---

### Post by Tekno.Statik on 2010-11-14
I think I got it...

1. System > Administration > Network tools:

   Network Device: Switch to "Ethernet Interface".

2. System > Preference > Network Connections:

   Add a NEW "Wired connection1"
   IPv4 Settings: Method: "Automatic (DHCP)"
   IPv6 Settings: Method: "Ignore"

3. Try switching between Auto_eth0 and Wired connection1 until you see the icon for "Connected".

It took me a while, and while trying to help you out I lost my internet as well, but this fixed it.

4. [http://chrome.google.com](http://chrome.google.com) (Try it out, man. You won't regret it)

---

### Post by maverick280857 on 2010-11-14
So after a few more reboots, the network suddenly started working again, **before** I manually blacklisted ipv6 (which has had little or no effect).

> **dineshs said:**
> Can you ```
ping 4.2.2.1 -c3
```

```

PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_req=1 ttl=55 time=286 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=55 time=286 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=55 time=286 ms

--- 4.2.2.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 286.126/286.312/286.666/0.250 ms

```

> **Tekno.Statik said:**
> I think I got it...

1. System > Administration > Network tools:

   Network Device: Switch to "Ethernet Interface".

2. System > Preference > Network Connections:

   Add a NEW "Wired connection1"
   IPv4 Settings: Method: "Automatic (DHCP)"
   IPv6 Settings: Method: "Ignore"

3. Try switching between Auto_eth0 and Wired connection1 until you see the icon for "Connected".

It took me a while, and while trying to help you out I lost my internet as well, but this fixed it.


Yeah, I had already tried this but it didn't help.

> 4. [http://chrome.google.com](http://chrome.google.com) (Try it out, man. You won't regret it)

I have Chrome, and Chrome too wasn't working when Firefox wasn't working :)

I confirmed that the problem is(was) not caused by connman or some of the other DHCP-related things that are mentioned on other threads. Firefox is still erratic (so is Chrome!) but generally things are working better now...and I repeat, there has been NO intervention from my side. Perhaps a bug?

---

### Post by maverick280857 on 2010-11-16
Back to the same problem...in Firefox **and** Chrome. ipV6 is disabled. But at least network works...slightly better.

---

### Post by dineshs on 2010-11-16
Can you explain the setup?eth1 to internet and eth0 to network?Can you post the results of```
route -n
```and```
cat /etc/network/interfaces
```
Did you try open DNS?
(System -> Preferences -> Network Connections -> Auto eth0 -> Edit -> ipv4-automatic DHCP addresses only-enter DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply)

---

### Post by maverick280857 on 2010-11-16
Okay Dinesh, I'll post the output in a bit. Meanwhile, I can provide some more (perhaps not so useful) information:

1. The problem has worsened. I am back to the 'no network access' in Ubuntu (not just the internet).

2. When the internet was working, I ran Ktorrent briefly and found that while it was running, the browsers (Chrome, Firefox both) would not work -- I would keep getting error messages ("Page cannot be displayed" or "Server not found") even though the torrent client was successful in transferring data for that duration.

I don't see why Ktorrent should cause damage..it works fine on Fedora at least.

---

### Post by maverick280857 on 2010-11-16
> **dineshs said:**
> Can you explain the setup?eth1 to internet and eth0 to network?

eth0 is the only one connected (to an ADSL modem), eth10 is disconnected.

> Can you post the results of```
route -n
```

```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```

> and```
cat /etc/network/interfaces
```

```

auto lo
iface lo inet loopback

```

> Did you try open DNS?
(System -> Preferences -> Network Connections -> Auto eth0 -> Edit -> ipv4-automatic DHCP addresses only-enter DNS as [COLOR="Blue"]4.2.2.1[/COLOR] and apply)

I tried this. It seems to work, at least for now, so thanks :-). Before this, there was no DNS IP explicitly mentioned, and before that, I had put the one that my ISP gave me. The network stopped working in both scenarios, so I assumed this wasn't the reason.

---

### Post by sum1cross on 2011-01-04
I have been having a similar problem in Ubuntu 10.10, 64bit, with a Gigabyte M/B and Realtek on-board LAN.

I recently ran an update,and remote rebooted the machine - so I don't think the update completeed correctly - result no mouse, no network, no keyboard.

As a result, I elected to perform a clean install of Ubuntu 10.10. No wired network, ifconfig shows the interface, but no IP details.  IPV6 set to ignore.

Ubuntu 9.10 loads network every time.  Ran updates, then loaded 10.04 (without a reboot after updates).  Network connection killed. Strange, because until November I was running 10.04 on this same machine without issue.

I have played with every setting I can think of, without success in 10.10.  Am currently rebuilding in 9.10, will run updates and reboot.

Something bad is happening!

---

### Post by PatchesTheCaveman on 2011-01-04
sum1cross:  I think one of the kernel updates in Lucid is getting busted like the one in Maverick that hit me and others:  [http://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](http://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

Try following the instructions I just gave another poster to boot into an older kernel and see if that fixes the problem:
[http://ubuntuforums.org/showpost.php?p=10318124&postcount=4](http://ubuntuforums.org/showpost.php?p=10318124&postcount=4)

---

### Post by Bucky Ball on 2011-01-04
10.04 LTS on the other hand seems to be problem free.

The dodgy kernel in question for 10.10 is:

2.6.35-24

Might pay to avoid updating the kernel to that if people haven't already. Problem will be sorted soon no doubt.

---

### Post by Lobby Dosser on 2011-01-05
I have this problem also.  I am running Ubuntu 10.10.  The motherboard is a Gigabyte GA-G41MT-D3.  The ethernet chip is a Realtek RTL8111/8168B.  Kernel is 2.6.35-24.  lsmod showed I was using module R8169.  I then changed the module to R8168.  It didn't help.  If anything things are a bit worse.

I boot up and the networking is Ok.  After a couple of minutes I start getting error messages saying the Web browser cannot find servers.  Doing a ping either for an IP number or a site address gets no response.  The strange thing is that Transmission can be running a bittorrent stream quite happily with no problems yet I cannot ping.  It isn't bittorrent causing this because it will happen even when bittorrent is not running.

If I boot into windows, networking is perfect, so it isn't a hardware problem.

---

### Post by sum1cross on 2011-01-05
First of all, thanks Patches and Bucky Ball for your posts yesterday.

As I said yesterday, I was rebuilding using 9.10, as the network worked - every time.

Following the comment from Bucky Ball that the problem didn't seem to be present in 10.04, I downloaded the ISO for 10.04.1, burned it to a CD, and proceeded to reboot. No wired ethernet connection.

At this point, I decided to try a hard reset (disconnect all power, powersystem on & off several times to discharge any residual capacitors) as suggested in these posts [http://ubuntuforums.org/showthread.php?p=10167364](http://ubuntuforums.org/showthread.php?p=10167364) and [http://fostergrant.ubuntuforums.org/showthread.php?t=1436667](http://fostergrant.ubuntuforums.org/showthread.php?t=1436667).

On reboot from the 10.04.1 CD, ethernet wired network came up immediately.

Seeing this had fixed the problem in 10.04.1, I decided to reboot using a 10.10 CD.  Again wired network came up immediatley, no problems, so I proceeded to install 10.10 as a clean install.

On normal boot, wired ethernet again came up straight away as normal.  At this stage, I decided to push the envelope, and ran all updates (including the "suspect" 2.6.35-24 kernel).  Again, no network problems.

So in summary: 
1. A hard reset (physically removing all power and LAN cable, discharging capacitors) rectified the LAN problem I was experiencing.
2. The issue seems to be around the RealTek LAN controller independant of motherboard.

The question I have not answered is why did 9.10 work flawlessly, both from boot CD and when installed, yet 10.04 and 10.10 consistently fail? What has significantly changed in the network manager and/or kernel to expose the problems in the Realtek LAN Controller?

By the way, the driver in 2.6.35-24 is r8169, but I have not checked the controller (hardware)version.  Either way, it is working flawlessly, so I suspect the r8168/r8169 discussion may not be as relevant.

I hope this post helps others, and the developers in establishing a root cause of the issues being experienced.

---

### Post by Lobby Dosser on 2011-01-09
I have the same problem.  The hard reset solution didn't work for me.  I have Ubuntu 10.10 with kernel 2.6.35.24.  I started off with kernel module R8169 but then changed to R8168 which didn't solve the problem. 

I booted off live CDs of Knoppix 6.2 and Ubuntu Natty Alpha.  Both worked fine.  Both have kernel module R8169 so it can't be that causing the problem.  Knoppix 6.2 has kernel 2.6.32.6 and Natty has kernel 2.6.37-7 generic.  I suspect that the kernels used for 10.10 and 10.4 are what are causing the problem.

---

### Post by Bucky Ball on 2011-01-09
> **sum1cross said:**
> 
So in summary: 
1. A hard reset (physically removing all power and LAN cable, discharging capacitors) rectified the LAN problem I was experiencing.
2. The issue seems to be around the RealTek LAN controller independant of motherboard.



Yes, that fix seems to be working for many. Good news it worked for you and you're up and running. ;)

Odd thing is the driver version in 10.04 (and 10.10) is actually dated. It is 0018 and the there is a newer one, 0019. Updating the driver seems to work for some also, but not for me I discovered last night. The updated Windows driver did fix the problem there but no difference whatever in Ubuntu with my issue of randomly fluctuating signal strength and completely woeful speeds (0.04-0.07Mbps only on my 10.10 install and 10Mbps+ on the other five OS installs on the three other computers in the house, Windows and Ubuntu). :(

---

### Post by Rebelli0us on 2011-05-19
Same problem here, I have two very mainstream mobos GIGABYTE GA-890GPA-UD3H and after about 4 days the wired network **stops working** (wireless still connects fine). I have to shut down and** turn off the power** to the mobo for a few minutes and then reboot. Windows 2000 and XP work just fine on this hardware. **Fix it please**!

---

### Post by Bucky Ball on 2011-05-19
> **Rebelli0us said:**
> Same problem here, I have two very mainstream mobos GIGABYTE GA-890GPA-UD3H and after about 4 days the wired network **stops working** (wireless still connects fine). I have to shut down and** turn off the power** to the mobo for a few minutes and then reboot. Windows 2000 and XP work just fine on this hardware. **Fix it please**!

You would be a lot better off posting a new thread with an descriptive title and as much detail as possible. This thread is four months old and you are buried deep so you probably won't get a lot of help here. 

Post a link here to the new thread if you like. Good luck. ;)

---

### Post by maverick280857 on 2011-05-20
Agree with Bucky Ball. I've marked this thread as solved, to avoid further confusion.

---

