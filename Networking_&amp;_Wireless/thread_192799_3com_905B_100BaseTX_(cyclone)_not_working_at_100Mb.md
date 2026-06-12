---
title: "3com 905B 100BaseTX (cyclone) not working at 100Mbps"
date: 2006-06-09
forum: Networking &amp; Wireless
---

### Post by chimpsky on 2006-06-09
Hello,

We're trying to get a 3com 905B 100BaseTX (cyclone) card working at 100Mbps. When we set the switch to full duplex, 100Mbps, the card stops responding, there's no light on either at the switch or on the back of the machine. 

When we try and set the switch to 10Mbps, it manages to connect to the DHCP server and gets IP access. But, the card works at an extrememly slow speed. 

We're assuming were using the 3c59x modules, as it's the module we've read about in other postings for this card. When we perform the command:

lsmod | grep 3c59x

The output is:

3c59x                  47784  0
mii                     6176  2 e100,3c59x

So, the module is there, but it doesn't appear to be used by anything. Is this perhaps the problem with the card? If so, how can we force it to use this module?

Thanks for any help...

---

### Post by Aramis on 2006-06-09
For Completeness,

I work with Chimpsky on the kit that he mentions and this post aims at giving participants more data about the overall setup.

First of all and most importantly, most of the PCs that we use and run Ubuntu have this 3Com NIC card. For instance, at the moment we have a Breezy PC that has the exact same problem, whereas Chimpsky reports a problem that we first encountered on a Dapper Ubuntu OS.

I just finished verifying the configuration of our switch (Cisco Catalyst 3550 series, VLAN enabled, portfast enable [save 30 seconds on the spanning tree protocol] ). in a nutshell, I plugged my SAMSUNG laptop that runs Breezy and my NIC got its IP address from the DHCP server and was the card was _automatically configured for 100mbps in Full duplex_. Hence, I conclude that the problem we have with the 3 Com NICs is not due to the configuration of the switch.

Furthermore, the "dmesg" command told us that there were several problems with the IRQs, we fixed it by editing the Grub menu accordingly. Now the "dmesg" no longer include IRQ related error. Unfortunately, this has not change our luck (sights).

We also had a go at the "mii-diag" command. Basically, on the 1 PC (Dapper) we tried to force the 100mbps Full dupex with the following commands :
```

sudo mii-diag -A 100baseTx-FD eth3
sudo mii-diag -F 100baseTx-FD eth3

```
The switch however indicates that the interface is configured in half duplex ... and to add to our trouble communication on the wire fails. Indeed, the DHCLIENT fails, the DHCP server does not receive any DHCP request. I thus conclude that there is a duplex mismatch between the PC and the switch.

We repeated the above commands for the 2nd PC (Breezy), as before the command seems to be accepted no problem but the interface only acheive the great speed of 10mbps in full duplex.

Our objective is to be able to change the speed of the various interface of the switch, and these changes to be cascaded to the Ubuntu PCs without having to mess about with NICs every time :!: We used to have FreeBSD before hand and changing link speed from the switch did not produce such problem what so ever.

After a search on the web we have established that the 3com cards that we use are supported in Ubuntu. Surely, we missed out a detail or two...

Hence,

1 - how do we know which driver(s) a NIC is using ?
2 - if the NIC is not using the proper driver(s), how do we force the NIC to use a set of drivers... From what we can find online this 905B series is compatible with the 3c59x module...

Finally, if you think there are some tests we have not done, please let us know. We will gladly post the results and so on.

It must simple I am sure....

Thanks in advance to all participants

Ar@mi$

---

### Post by Aramis on 2006-06-09
Hi Again...

okay I collected a bunch of commands that might be of interrest.... here is the output of "lspci -v" for the Dapper machine:
```

0000:02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (CNR) Ethernet Controller (rev 81)
        Subsystem: ASUSTeK Computer Inc.: Unknown device 8071
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at e5000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at b800 [size=64]
        Capabilities: [dc] Power Management version 2

0000:02:09.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
        Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5
        I/O ports at b400 [size=256]
        Memory at e4800000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e7e00000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2

0000:02:0a.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)
        Subsystem: D-Link System Inc DGE-528T Gigabit Ethernet Adapter
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 9
        I/O ports at b000 [size=256]
        Memory at e4000000 (32-bit, non-prefetchable) [size=256]
        Expansion ROM at e7e20000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2

0000:02:0b.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
        Subsystem: 3Com Corporation 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 32, IRQ 9
        I/O ports at a800 [size=128]
        Memory at e3800000 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at e7e40000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 1


```

**_NOTE:_** This morning we ran some test with the GigaBit cards and these work out of the box :!:

Now the Breezy computer (arff.... no good inside joke [-(  )
```

0000:02:00.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
        Subsystem: 3Com Corporation 3C905B Fast Etherlink XL 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 10
        I/O ports at ac00 [size=128]
        Memory at efefff80 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at efec0000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 1

0000:02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
        Subsystem: 3Com Corporation 3C905C-TX Fast Etherlink for PC Management NIC
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at a800 [size=128]
        Memory at efefff00 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at efea0000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2

0000:02:02.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
        Subsystem: 3Com Corporation 3C905C-TX Fast Etherlink for PC Management NIC
 Flags: bus master, medium devsel, latency 64, IRQ 3
        I/O ports at a400 [size=128]
        Memory at efeffe80 (32-bit, non-prefetchable) [size=128]
        Expansion ROM at efe80000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2

```

I hope that helps.

Ar@mi$

---

### Post by Aramis on 2006-06-22
[SIZE="4"][COLOR="Red"]This problem is _now_ SOLVED[/COLOR][/SIZE]. 
All the credits go to our department's very experienced technicians.

What started with an apparant flaw within the drivers or the Kernell is in fact entirely 3Com's fault. In a nutshell, the chips on some of the cards we tested were setup to "*maximum compatibilites*" that is to say 10mbps half duplex (speed that all equipement must be compatible with). Some of the cards we had were set to "auto-negociate" and hence work very well.

The reason why some of the "faulty" cards worked "flawlessly" in operating systems such as FreeBSD or Microsoft Windows is because these operating systems have drivers capable of overriding the on board chip configuration (I gather that Windows drivers systematically do that). As far as I am concerned I believe that it is bad engineering to force hardware capabilities as opposed to write drivers that simply exploit these capabilities.

It is possible to go around this problem using a tool called 3c90xCFG.exe [version 5.0] (DOS mode only). This tool allows accessing the on board chip, from there one can modify the registers to activate "auto-negotiation". Since this modification, we no longer experience problem, in fact we have somewhat better performances :mrgreen: . 

Some may wonder why the cards were setup in such a weird way... Well, network equipment is expensive and difficult to replace (some times) probably because these are seldom switched off, and turning them off could be troublesome for users (no Internet access :lol: ). On the top of that some equipment do no support "auto-negotiation" such as HUBs, hence admins/technicians needs to be able to "force" the NIC to a pre-determined setup. I reckon this is what happened to most of the cards we tested. Of course, admins/techinicians need a tool to achieve that.

I think it is unfortunate that it took us so long to figure this one out, and that we had a all host of tests, checks, readings and so on to do before reaching this conclusion. It is even more regrettable that there is no Unix/Linux tool capable (that I know of) to modify/adapt the onboard chip setup.

If you are encountering the same problem, here is a simple test that you can do. It does work with a lot of NIC and not only 3com's.

1 - Take a good switch, that supports auto-negotiation and is able to "tell you" the current ports' setting with LEDs.
2 - Fit the NIC onto the motherboard
3 - Make sure that the power cable is plugged in BUT DO NOT start the computer.
4 - Pay attention to the NIC, it is possible that LEDs light up. On our 3 Com cards LEDs turn yellow when they support auto-negotiation. Wrongly configured NIC turn green.
5 - If you can read from the NIC try from the Switch. It should be able to tell you the current settting
6 - if step 4 and 5 do not work, start up the computer and read the result from the switch. The operating system does not need to be up and running to get an accurate reading.

_@forums administrators, and moderators_
While crawling on Google I have learnt that complains about the 3c59x driver reach the Kernell mailing list(s) as well as Donald Becker's mailing list. These people deserve to know that ultimately their drivers and kernell **work**. By the same token people in difficulty need to know that work arounds, and simple tests (as described here) do exists. Hence, could you forward the relevant information to the poeple concerned or indicate where I could share my findings.

Good day to you all. I do hope this will help other.

Ar@mi$ a Researcher that found something ... for once.

---

