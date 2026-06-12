---
title: "Wireless Woes"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by Tea on 2005-12-28
Hi, I'm trying to get wireless working on my T42 which is duel booting Windows XP and Ubuntu 5.10. The wireless works fine on windows, but it wont work on Ubuntu, I've looked at the trouble shooter in the Wiki, but I still dont know whats wrong.

Here is what I know, 

---------------------------------------------------------------------------

iwconfig =

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"XXX"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:49:03:35
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

iwlist ath0 scan =

ath0      Scan completed :
          Cell 01 - Address: 00:40:05:49:03:35
                    ESSID:"XXXXXXXXXXXXX"
                    Mode:Master	
                    Frequency:2.437 GHz (Channel 6)
                    Quality=12/94  Signal level=-83 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5 Mb/s
                    Bit Rate:11 Mb/s
                    Extra:bcn_int=100

ls pci =

0000:00:00.0 Host bridge: Intel Corp. 82855PM Processor to I/O Controller (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 82855PM Processor to AGP Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DBM LPC Interface Controller (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DBM (ICH4) Ultra ATA Storage Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
0000:02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
0000:02:01.0 Ethernet controller: Intel Corp. 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
0000:02:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

lspci -n =

0000:00:00.0 0600: 8086:3340 (rev 03)
0000:00:01.0 0604: 8086:3341 (rev 03)
0000:00:1d.0 0c03: 8086:24c2 (rev 01)
0000:00:1d.1 0c03: 8086:24c4 (rev 01)
0000:00:1d.2 0c03: 8086:24c7 (rev 01)
0000:00:1d.7 0c03: 8086:24cd (rev 01)
0000:00:1e.0 0604: 8086:2448 (rev 81)
0000:00:1f.0 0601: 8086:24cc (rev 01)
0000:00:1f.1 0101: 8086:24ca (rev 01)
0000:00:1f.3 0c05: 8086:24c3 (rev 01)
0000:00:1f.5 0401: 8086:24c5 (rev 01)
0000:00:1f.6 0703: 8086:24c6 (rev 01)
0000:01:00.0 0300: 1002:4c57
0000:02:00.0 0607: 104c:ac46 (rev 01)
0000:02:00.1 0607: 104c:ac46 (rev 01)
0000:02:01.0 0200: 8086:101e (rev 03)
0000:02:02.0 0200: 168c:0013 (rev 01)

cat /etc/network/interfaces =

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid (XxXxXxXxXxXxXxXxXxX)
wireless-key (YxYxYxYxYxYxYxYxYxYxY)

auto ath0

auto eth0

---------------------------------------------------------------------------

Other stuff: I have network manager installed, and the wireless key is in hex, if that helps. 

Thanks in advance

---

### Post by Lambert on 2005-12-28
You are associated with your router so device is ok and driver should be good.

>  ath0      IEEE 802.11g  ESSID:"XXX"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:40:05:49:03:35

that's what Access Point is telling here. If you weren't associated it would be 00:00:....

A couple more commands

```
ifconfig
```

and

```
route
```

post output of those commands.

Was the guide hard to follow? Any suggestions to improve?

---

### Post by Tea on 2005-12-28
Here is the output of ifconfig and route.

ifconfig =

ath0      Link encap:Ethernet  HWaddr 00:14:A4:54:0B:78
          inet addr:192.168.0.146  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a4ff:fe54:b78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149 errors:432 dropped:0 overruns:0 frame:432
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:10563 (10.3 KiB)  TX bytes:7632 (7.4 KiB)
          Interrupt:11 Memory:e0b80000-e0b90000

eth0      Link encap:Ethernet  HWaddr 00:01:6C:E9:BB:87
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x8000 Memory:c0240000-c0260000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:41690 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3096521 (2.9 MiB)  TX bytes:3096521 (2.9 MiB)


route =

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 ath0

---

### Post by Lambert on 2005-12-28
This may not make sense but there is no route to the router which should have set up with dhcp automatically.

Anyway run this command  and then check to see if you can surf etc...

```
sudo route add default gw ____ dev ath0
```

in the blank put the ip of the router. My guess is it's 192.168.0.1

---

### Post by Tea on 2005-12-28
No luck, 

All i get is from the command is "SIOCADDRT: File exists" nothing changes 

= (

---

### Post by Lambert on 2005-12-28
When you run the command route there needs to be a line that looks like this. the only difference would be the 192.168.0.1. That's the ip of your router.

```
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

```

so I'm not sure why that command wasn't taken.

try this

```
sudo dhclient ath0
```

then re-run route to see if that line showed up as dhcp is supposed to handle this.

---

### Post by Tea on 2005-12-28
Ok, did what you just suggested and it turned up like it is supposed to 

"192.168.0.1 * 0.0.0.0 UG 0 0 0 ath0"

---

### Post by Lambert on 2005-12-28
so you're up and running wirelessly with ubuntu now?

---

### Post by Tea on 2005-12-28
Nope,

I canot ping the router, or anything else.

I have a Destination Host Unreachable error when i try to "ping 192.168.0.1"

---

### Post by Lambert on 2005-12-28
I want to back track and double check everything.

When you run iwconfig you're associated with the router with the line Access Point: (mac address of router) correct?

When you run ifconfig you're assigned an ip addres which the line inet address: (192.168.x.x) correct?

When you run the command route your output looks like this. correct?

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.0.0     U     0      0        0 ath0
default         192.168.0.1     0.0.0.0         UG    0      0        0 ath0

```

If you have an ip assigned to the device can you ping that?

If above ping works ping router. (So far pinging router doesn't work.) same result, not reachable?

Some routers have a setting to refuse icmp packets (ping packets) so try this command.

```
tracepath 82.211.81.130
```
what's your output for this?

---

### Post by Tea on 2005-12-28
Here's the output.

tracepath 82.211.81.130=
 
1:  192.168.0.146 (192.168.0.146)                          0.270ms pmtu 1500
1:  no reply
1:  192.168.0.146 (192.168.0.146)                        2000.719ms !H
     Resume: pmtu 1500

My router is a Dlink DI-714p+ if that helps.

---

### Post by FLeiXiuS on 2005-12-29
Ok...I'm still trying to think of a reason why it wouldn't allow your NIC won't allow you to do anything.  

In my opinion, lets see if your NIC is communicating at layer 2.  Mac Addresses and such, data-link layer for the OSI nerds.

:-)

Mind giving me the output of:
```
sudo arp -a
```

---

### Post by FLeiXiuS on 2005-12-29
> RX packets:149 errors:432 
This is frightening me, seeing you receiving more dead packets then you are alive ones.  Something is wrong here, I'm still determining a prognosis.

---

### Post by FLeiXiuS on 2005-12-29
On windows did you have to insert a setup disk for your router?  

What I'm leading to believe is that your on the network just not authenticated to the router.  This meaning, there is an encryption of some sort, whether it be wep/wpa or a higher protocol.

Consult your routers http configuration page for more details.

[http://192.168.1.1](http://192.168.1.1)

---

### Post by Tea on 2005-12-29
Ok, 

"sudo arp -a" dosent give me any output when im connected wirlessly, but gives  me "? (192.168.0.1) at 00:40:05:49:03:35 [ether] on eth0" when im connected through ethernet. 

Im not sure what kind on security this is, but inorder to connect, it needs a 26 character hexadecimal key. I dont recall having to use a CD to set up my router, but ill go onto my router later to check all of this.

Thanks for all the help so far.

---

### Post by FLeiXiuS on 2005-12-29
There may be an answer for you on the Knowledgebase.

[http://doc.gwos.org/index.php/IBMThinkpadT42Breezy](http://doc.gwos.org/index.php/IBMThinkpadT42Breezy)

---

### Post by FLeiXiuS on 2005-12-29
Actually, that will help you..but first you said it requires a 26 character hex key?  Yeah I figured it was an encryption of some sort. Get the key from Windows or get it from your routers config page.

---

### Post by FLeiXiuS on 2005-12-29
Actually, that will help you..but first you said it requires a 26 character hex key?  Yeah I figured it was an encryption of some sort. Get the key from Windows or get it from your routers config page.  Also do you know whether it's wep // wpa?

---

### Post by Tea on 2005-12-29
I know the key, I dont know if it's WEP or WPA, is there a way to check without logging onto the router? 

Ill go check that link now.

EDIT: Ive used that guide, when I was first setting up the system, it was really helpfull, and it helped solve some earlier problems (hibernation with the old ATI card) but it didnt hold much on networking problems.

---

### Post by isillight on 2005-12-29
I'm having the same problem as 'Tea'

I'm using a WEP key which works under windows, but under linux I get RX errors

Have you made any progress on this issue?

---

### Post by isillight on 2005-12-29
When I disable WEP the ath0 interface seems to function for a few seconds
and then it drops connection.

---

### Post by Tea on 2005-12-30
Bump?

---

### Post by isillight on 2005-12-30
The issue is not WEP

There seems to be some issue with the ath0 interface - even without WEP
I get RX errors although I am able to ping the gw after ifup for a few mins
then the connection drops again.

---

### Post by Tea on 2005-12-30
Aye, I sometimes get a few seconds of connection before it drops. Im thinking about going and buying a "slot in" (or whatever you call em) network card to see if it works.

---

### Post by Lambert on 2005-12-30
Tea, I've been watching hoping someone else would see something.

So let's try something else(I use a new v of madwifi so I'm not sure if this works for the default driver in breezy so just post back if you get an error)

type in this command

```
sudo athdebug 0xffffffff
```

you should see something like this.

```
0x0 => 0xffffffff<xmit,xmit_desc,recv,recv_desc,rate,reset,mode,beacon,watchdog,intr,xmit_proc,recv_proc,beacon_proc,calibrate,keycache,state,node,ff,fatal>

```

then type this command

```
tail -f /var/log/messages
```

Now try to activate your device. There should be some debugging messages print in the terminal. (they will continue to print until you hit ctrl+c) Post output of lines here.

debug mode will continue to print things in the messages file so to stop gathering data do this command.
```
sudo athdebug 0x0
```


This is nothing more then a guess as I don't think anything is wrong with the driver because it can scan and receive dhcp information. But it's something to try.

---

### Post by Tea on 2005-12-30
Yargh, 

"sudo athebug 0xfffffff" = command not found

Could I update madwifi to the version your using?

---

### Post by Lambert on 2005-12-30
[quote=Tea]Yargh, 

"sudo athebug 0xfffffff" = command not found

Could I update madwifi to the version your using?[/quote]

Not sure if you typed incorrectly but it is ath**d**ebug

Upgrading may fix this but no guarantee as I'm not sure driver is the problem. There are warnings on doing this  as you have to remove some other packages that you might need and have to recompile.

First I'll reccomend trying this like. This updates to the latest snapshot of the madwifi-old driver. It might have a fix in it for your situation.

[http://www.ubuntuforums.org/showthread.php?t=75451&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=75451&highlight=madwifi)

The driver I'm using is the new code labled madwifi-ng. Instructions for that are here.

[http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi](http://www.ubuntuforums.org/showthread.php?t=105437&highlight=madwifi)

---

### Post by Tea on 2005-12-30
Hey, 

That was indeed a misstype, sorry.

Im following the instructions in the thread you linked, but im getting a whole bunde of errors when I try to "make" or "make install" madwifi. 

Anyway, while I was looking around I typed "dmesg -" and among all of the junk that appeared, I saw this.

```
[4294697.240000] wlan: 0.8.6.0 (EXPERIMENTAL)
[4294697.243000] ath_rate_sample: 1.2
[4294697.249000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[4294697.252000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294697.675000] Build date: Oct 11 2005
[4294697.675000] Debugging version (IEEE80211)
[4294697.675000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[4294697.675000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294697.675000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[4294697.675000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[4294697.675000] ath0: mac 5.9 phy 4.3 radio 4.6
[4294697.675000] ath0: Use hw queue 1 for WME_AC_BE traffic
[4294697.675000] ath0: Use hw queue 0 for WME_AC_BK traffic
[4294697.675000] ath0: Use hw queue 2 for WME_AC_VI traffic
[4294697.675000] ath0: Use hw queue 3 for WME_AC_VO traffic
[4294697.675000] ath0: Use hw queue 8 for CAB traffic
[4294697.675000] ath0: Use hw queue 9 for beacons
[4294697.675000] Debugging version (ATH)
[4294697.675000] ath0: Atheros 5212: mem=0xc0210000, irq=11

```

Dunno if it helps with anything, I'll get back to trying to install the madwifi drivers.

EDIT: Looked around some more and I found  "[4298239.046000] ath0: no IPv6 routers present" in many places, although I also see the same message, but eth0 instead if ath0, and my ethernet is working fine.

---

### Post by Lambert on 2005-12-30
Ok ipv6, never thought about looking there. So let's try disabling ipv6 to see if that helps.

Open the file /etc/modporbe.d/aliases


Add the first three lines below to the file. The 
line with # starting is already in the file. Find it and add the # in front of it.

 
  alias net-pf-10 ipv6 off
 alias net-pf-10 off
 alias ipv6 off
 #alias net-pf-10 ipv6




 
 After making these changes a reboot is required.

---

### Post by Tea on 2005-12-30
Got the madwifi driver working...I think.... Is there any way I can check to make sure? Im not seeing any diference from it. 

Also, the ipv6 stuff hasnt seemed to do anything .


Im thinking that a reinstall may be a posibility, It's a new system, not much to back up, would there even be the slightest posibility that this could help?

---

### Post by Lambert on 2005-12-30
I've seen others solve their problems with a reinstall. So it may be worth it if it's not that bad of an option.

Depending on which one you followed depends on the difference. Both on the surface appear the same. 

The first one is pretty much minor updates/bug fixes so there isn't much to see. 

The second one (madwifi-ng) there are a lot of under the hood changes. The biggest one you'll see is the interface ath0 is not created automatically, you have to run a command or build a script to create it. There are reasons for this that go along with the changes to the driver.

---

### Post by Tea on 2005-12-30
Sorry, should of made it clearer, i followed the first link.

---

### Post by isillight on 2006-01-01
I'm now using my old 3com pcmcia card which works without any issues:

eth1: 3com 3CRWE62092B

---

