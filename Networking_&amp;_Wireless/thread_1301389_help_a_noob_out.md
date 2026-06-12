---
title: "help a noob out ?"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by chipstack on 2009-10-26
i set up ubuntu on my gfs computer some months ago and it has mysteriously stopped connecting to the internet.
     when i check into the network devices loopback interface {lo} ethernet interface and ethernet interface{eth2:avahi} are listed and looking at them the numbers and all look right for my router as far as the submask and the ip .
     I havent used linux that much and i really dont know much about it but when i go to the network icon on the bottom right and look at the properties all the numbers are 0s  
    the active connection interface shows 0.0.0.0 as does the dns numbers and the others. 
     what should i do ?

---

### Post by Iowan on 2009-10-26
The avahi address usually means DHCP failed. How many interfaces on your machine? From a terminal, check **ifconfig -a** - post results. Can you **ping** the router (also from a terminal)?

---

### Post by chipstack on 2009-10-26
im used to working with windows, how i have it set up is 2 machines  are wired into my router , hers is on ubuntu and mine is windows xp
    what do you mean the dhcp failed and what is a terminal? i saw a ping thing from the administrators network tools , i dont know if this matters but her ubuntu shows gnome on the startup.
   ill try to ping it how do i get to the terminal ? i believe this is some dos box ?
 my computer on the same router is running just fine btw

---

### Post by Iowan on 2009-10-26
> **chipstack said:**
> ... how do i get to the terminal ?  Applications>Accessories>Terminal
CTRL-ALT-F1 will also get a terminal, but will require a login.  You will need to CTRL-ALT-F7 to get back to desktop.

---

### Post by chipstack on 2009-10-28
eth2      Link encap:Ethernet  HWaddr 00:0c:6e:d3:86:f3  
          inet6 addr: fe80::20c:6eff:fed3:86f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:7
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:120 (120.0 B)  TX bytes:6940 (6.7 KB)
          Interrupt:17 Base address:0xe000 

eth2:avahi Link encap:Ethernet  HWaddr 00:0c:6e:d3:86:f3  
          inet addr:169.254.10.57  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98784 (96.4 KB)  TX bytes:98784 (96.4 KB)
 sorry for the delay heres the ifconfig data
 when i tried ping router it said 
ping:unknown host router

---

### Post by Iowan on 2009-10-28
Please post results of **lshw -C network** (also from a terminal). 
Just guessing: **lshw** may show eth0, but **ifconfig** is showing eth2. There are a couple of threads where the eth# keeps climbing.
If that's the case, it may be possible to edit out the extraneous entries in */etc/udev/rules.d/70-persistent-net.rules*... but first things first.

---

### Post by chipstack on 2009-10-28
this is what came up .. doesnt look very useful to me but what do i know? 
 Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

---

### Post by Iowan on 2009-10-28
Those results don't look right (typo somewhere?) Command should be:```
lshw -C network
```

---

### Post by ant2ne on 2009-10-28
eth2 is a wired network interface? If so, start with the basics: Check the cable. Unplug it from the problem computer's nic and plug it in to the working computer's nic. Do you have network access. If not, we proceed to troubleshoot the wire or whatever the wire plugs into. If the working computer has network then you troubleshoot the problem computer's nic and/or its protocol.

169.x.x.x addy means, no DHCP (and no Static) so more then likely,.. no signal on the wire.

---

### Post by chipstack on 2009-10-29
the wire would be difficult to switch but looking at the router its lit , and the end of the wire going into the nic card is also lit and is blinking like information is being exchanged. id like to also note that from the packet manager it looks like it was updated right before it went offline and yes heres the info i must have typed it in wrong
       WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth2
       version: 74
       serial: 00:0c:6e:d3:86:f3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes

 i might try n switch the wires later but my own wire runs behind some desks.

---

### Post by ant2ne on 2009-10-29
> **chipstack said:**
> the wire would be difficult to switch but looking at the router its lit , and the end of the wire going into the nic card is also lit and is blinking like information is being exchanged.Blinking lights are a good diagnostics tool, but you can't rely on them. Find another way to rule out that cable. Swap with known good, Use a known good port on the switch/router. Use a known good cable. Use a known good client. Swap NICs with known good. etc, until you've figured out what device is faulty.

---

### Post by chipstack on 2009-11-02
Thanks guys, I really thought it was a software problem but following your advice i checked the wire then swapped a new card in and it turns out putting a new nic card in did the trick.
     Works like new. I really appriciate the help and getting to know linux a little bit better.

---

### Post by ant2ne on 2009-11-02
\\:D/

You should change the thread title to "SOLVED Help a noob out"

---

