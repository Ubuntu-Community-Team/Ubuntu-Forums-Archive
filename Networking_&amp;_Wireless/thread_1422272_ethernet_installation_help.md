---
title: "ethernet installation help"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by macca_dacca on 2010-03-05
I have installed Ubuntu 9.04 
uname -r
2.6.28-11-generic
 
Checked cable/network with 386Box running Ubuntu 8.04 all OK.
 
Could not get Realtek 8168 on mother board to work on Gigabyte H55M-S2H motherboard. I tried to install r8168 driver but no luck ... so I bought another Linux compatible card which turned out to be a RTL8139c (eth1) and the driver I am using on this is card is 8139too.
 
ethtool -i eth1
driver: 8139too
version: 0.9.28
 
/etc/init.d/networking restart
....
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
...
No DHCPOFFERS recieved.
 
 
cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth1
iface eth1 inet dhcp
 
dmesg|grep eth
...
[ 4.215982] eth0: RTL8168d/8111d 0x57c5a000, 6c:f0:49:0e:1d:24, XID 283000c0 IRQ 2295
[ 4.224750] eth1: RealTek RTL8139 at 0xce00, 00:e0:1c:3d:0b:90, IRQ 19
[ 4.224752] eth1: Identified 8139 chip type 'RTL-8139C'
[ 13.656782] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 20.605201] r8169: eth0: link down
[ 20.605291] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 24.516058] eth1: no IPv6 routers present
[ 627.009468] eth1 link up, 100Mbps, full-duplex, lpa 0x45E1
[ 637.784058] eth1: no IPv6 routers present
 
My preference would be to get the motherboard ethernet working but perhaps the card may be easier to get working. Anyway after searching the net for ideas and trying different things I've just about given up. I have reinstalled Ubuntu today so eth0 is back to using the r8169 driver.
 
I'm no expert so my attempts at following other recipies have so far failed. From what I have read the 8139too driver should have worked with the RTL8139C chip so I have run out of ideas. I must be doing something wrong.
 
Can anyone get me started?

---

### Post by chili555 on 2010-03-05
It has been a long time since most of us ran 8.04, so some of this is faded memory. Is Network Manager running on this machine? NM and manual configuration, /etc/network/interfaces and dhclient, seldom, if ever, work well together. Either remove all the stanzas from *interfaces* **except** the loopback pair; OR remove NM completely.

May we please see:```
dmesg | grep -e 8169 -e 8139
```

---

### Post by macca_dacca on 2010-03-05
dmesg |grep -e 8169 -e 8139
 
[    4.214535] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.214555] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.214577] r8169 0000:03:00.0: setting latency timer to 64
[    4.215477] r8169 0000:03:00.0: irq 2295 for MSI/MSI-X
[    4.222078] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.222094] 8139cp 0000:04:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.223774] 8139too Fast Ethernet driver 0.9.28
[    4.223799] 8139too 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.224750] eth1: RealTek RTL8139 at 0xce00, 00:e0:1c:3d:0b:90, IRQ 19
[    4.224752] eth1:  Identified 8139 chip type 'RTL-8139C'
[   20.605201] r8169: eth0: link down

---

### Post by chili555 on 2010-03-05
Please do:```
sudo su
echo "blacklist 8139cp" >> /etc/modprobe.d/blacklist.conf
```Now, comment out all the stanzas in */etc/network/interfaces*, except those for loopback and then reboot. Does the add-in Realtek 8139 work? If not, please run the dmesg command I asked for above and post it. Thanks.

We can certainly then move on to troubleshooting the built-in NIC.

---

### Post by macca_dacca on 2010-03-05
Thanks I really really appreciate this.  Sorry for not getting back to you earlier I was asleep in Brisbane, Australia.
 
In my Ubuntu 9.04 box I have blacklisted 8139cp as requested.
tail -2 /etc/modprobe.d/blacklist.conf
[COLOR=blue]blacklist amd76x_edac[/COLOR]
[COLOR=blue]blacklist 8139cp[/COLOR]
 
I connected ethernet cable to the motherboard ethernet controller RTL8111/8168b and rebooted.
 
dmesg |grep -e 8169 -e 8139
[COLOR=blue][    4.214131] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.214150] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.214166] r8169 0000:03:00.0: setting latency timer to 64
[    4.214275] r8169 0000:03:00.0: irq 2295 for MSI/MSI-X
[    4.222062] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.222081] 8139cp 0000:04:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.223899] 8139too Fast Ethernet driver 0.9.28
[    4.223925] 8139too 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.225327] eth1: RealTek RTL8139 at 0xce00, 00:e0:1c:3d:0b:90, IRQ 19
[    4.225329] eth1:  Identified 8139 chip type 'RTL-8139C'
[   20.605379] r8169: eth0: link up
[   20.605416] r8169: eth0: link up[/COLOR]
 
some lines in: lsmod
[COLOR=blue]8139too   32128  0[/COLOR]
[COLOR=blue]8139cp    27776  0[/COLOR]
[COLOR=blue]r8169      40836  0[/COLOR]
[COLOR=blue]mii          13312  3  8139too,8139cp,r8169[/COLOR]
 
"comment out all stanzas in /etc/network/interfaces"
my  interfaces file now looks like (is this correct?):
[COLOR=purple]auto lo[/COLOR]
[COLOR=purple]iface lo inet loopback[/COLOR]
[COLOR=purple]#added below[/COLOR]
[COLOR=purple]#auto eth0[/COLOR]
[COLOR=purple]#iface eth0 inet dhcp[/COLOR]
[COLOR=purple]#auto eth1[/COLOR]
[COLOR=purple]#iface eth1 inet dhcp[/COLOR]
 
/etc/init.d/networking restart
[COLOR=blue]* Reconfiguring network interfaces...   [OK][/COLOR]
 
 
Seems as though I need to uncomment the lines in /etc/network/interfaces or am I a step ahead?  I tried again with them (commented out and uncommented) but so far I have not been able to get any DHCPOFFERS.  Hope this extra info helps.

---

### Post by chili555 on 2010-03-05
You are quite correct; let's not get too far ahead of ourselves. I notice two remarkable things. First:> [ 20.605416] r8169: eth0: link upIs the ethernet cable attached to the built-in card? What does this tell us?```
ifconfig
```Next, I notice that, even though we blacklisted 8139cp, it loaded anyway!!> some lines in: lsmod
8139too 32128 0
8139cp 27776 0Let's see what *ifconfig* says before we proceed.

---

### Post by macca_dacca on 2010-03-05
Yes the ethernet cable is attached to the built-in card.
 
ifconfig
[COLOR=blue]eth0      Link encap:Ethernet  HWaddr 6c:f0:49:0e:1d:24  
          inet6 addr: fe80::6ef0:49ff:fe0e:1d24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35944 (35.9 KB)  TX bytes:468 (468.0 B)
          Interrupt:247 [/COLOR]
[COLOR=blue]eth1      Link encap:Ethernet  HWaddr 00:e0:1c:3d:0b:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xce00 [/COLOR]
[COLOR=blue]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/COLOR]

---

### Post by chili555 on 2010-03-05
Both appear healthy. eth0 shows transmission and reception of data, suggesting it's linked but not associated. When you click the Network Manager icon, does it try to connect?

---

### Post by macca_dacca on 2010-03-05
I presume the network manager icon looks like a grey bar graph (with a small red box and white cross).
I clicked it open and clicked the Auto Ethernet button.
It then strated searching (two green dots with a blue line going in a circular motion)
 
I get a quick flash saying [COLOR=blue]No wired connection.[/COLOR]

---

### Post by macca_dacca on 2010-03-05
I noticed in the Network connections window "Wired" tab I have
Auto Ethernet (set with no MAC address) and
Auto eth1 (set with MAC qddress: 00:E0:1C:3D:0B:90)
 
I do not have an entry for eth0.
DO I create one?

---

### Post by chili555 on 2010-03-05
> DO I create one?Please try and let us know the result.

---

### Post by Iowan on 2010-03-05
[This]("http://ubuntuforums.org/showthread.php?t=1156441") probably won't help, but since it was 9.04 wired, it seemed worth mentioning.

---

### Post by macca_dacca on 2010-03-05
In the network connections window "wired" tab I added:
 
conection name: eth0
MAC address: 6C:F0:49:0E:1D:24
MTU: automatic
 
There now seem to be four lines in the Wired tab:
[COLOR=purple]eth0[/COLOR]
[COLOR=purple]Auto Ethernet[/COLOR]
[COLOR=purple]eth1[/COLOR]
[COLOR=purple]Auto eth1[/COLOR]
 
I restarted the computer.
ifconfig
[COLOR=blue]eth0      Link encap:Ethernet  HWaddr 6c:f0:49:0e:1d:24  
          inet6 addr: fe80::6ef0:49ff:fe0e:1d24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35944 (35.9 KB)  TX bytes:468 (468.0 B)
          Interrupt:247 [/COLOR]
[COLOR=blue]eth1      Link encap:Ethernet  HWaddr 00:e0:1c:3d:0b:90  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xce00 [/COLOR]
[COLOR=blue]lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]dmesg |grep -e 8169 -e 8139[/COLOR]
[COLOR=#0000ff][    4.216119] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.216136] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.216153] r8169 0000:03:00.0: setting latency timer to 64
[    4.216293] r8169 0000:03:00.0: irq 2295 for MSI/MSI-X
[    4.228840] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.228864] 8139cp 0000:04:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.230469] 8139too Fast Ethernet driver 0.9.28
[    4.230495] 8139too 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.231863] eth1: RealTek RTL8139 at 0xce00, 00:e0:1c:3d:0b:90, IRQ 19
[    4.231865] eth1:  Identified 8139 chip type 'RTL-8139C'
[   20.609060] r8169: eth0: link down
[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=#0000ff][COLOR=black]Any ideas?[/COLOR]
[/COLOR]

---

### Post by macca_dacca on 2010-03-05
Appologies. On my last atempt I had the ethernet cable attached to the RTL8139C card (eth1) instead of the motherboard ethernet (eth0).
 
I rebooted again.
dmesg
[COLOR=blue][    4.220282] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    4.220299] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.220313] r8169 0000:03:00.0: setting latency timer to 64
[    4.220396] r8169 0000:03:00.0: irq 2295 for MSI/MSI-X
[    4.228047] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.228070] 8139cp 0000:04:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    4.229706] 8139too Fast Ethernet driver 0.9.28
[    4.229731] 8139too 0000:04:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    4.231198] eth1: RealTek RTL8139 at 0xce00, 00:e0:1c:3d:0b:90, IRQ 19
[    4.231201] eth1:  Identified 8139 chip type 'RTL-8139C'
[   20.609747] r8169: eth0: link up
[   20.609755] r8169: eth0: link up
[/COLOR]
[COLOR=blue][COLOR=black]Still no eth0 IP listed in ifconfig.[/COLOR][/COLOR]
[COLOR=blue][COLOR=#000000]Some previous posts mentioned that the 8168 driver may solve the problem but I tried various solutions to no avail.[/COLOR][/COLOR]
 
Still cannot get the RTL 8139C card to worth so maybe these is something I am missing somewhere.

---

### Post by chili555 on 2010-03-05
Please try:```
sudo rmmod -f 8139cp
```Check Network Manager again and see if it more cooperative. I'm getting low on ideas.

---

### Post by macca_dacca on 2010-03-05
OK the 
[COLOR=blue]rmmod -f 8139cp[/COLOR]
seemed to work with lsmod showing only
[COLOR=blue]8134too   32128 0[/COLOR]
[COLOR=blue]r8169      40836 0[/COLOR]
[COLOR=blue]mii          13312   8139too,r8169[/COLOR]
[COLOR=#0000ff][/COLOR] 
[COLOR=black]I tried both eth0 and eth1 and still no connection.[/COLOR]
Just an odd thought but could it be the motherboard not being Linux compatable?
I would think the ethernet card with the RTL8139C chip should have worked...hmmm:confused:

---

### Post by doskyis on 2010-03-05
Sorry for barging in on your conversation, but i am so new to ubuntu i don't even know how to start a new thread. For some reason my laptop no longer recognizes my wired internet connection. It only recognizes the wireless. I've run out of ideas on how to make it recognize both (i'd like wired internet when i plug in the ethernet cord, and wireless when I disconnect it) 
Any ideas will be greatly appreciated. I just installed ubuntu 9.10 a few days.

Thanks

---

### Post by macca_dacca on 2010-03-05
Dear doskyis
 
This thread is still in progress.  To make a new thread please click on "New Thread" on screen instead.

---

### Post by chili555 on 2010-03-06
> could it be the motherboard not being Linux compatable?I highly doubt it. Unless you bought the latest bleeding edge motherboard yesterday, it is highly unlikely. After all, Ubuntu installed and boots and responds to commands, etc. I have three thoughts and the first I have is that you interrupt the boot process and look around in the BIOS to see if there are any settings that we can change that might have any effect; such as, Plug and Play OS: yes/no or IRQ Interrupts: OS assigned/Auto or any other suspicious things.

Second, do you still have your Ubuntu install disc if we need it? If we remove Network Manager and try complete manual configuration, we can only get it back with the install disc or from the internet, which you don't have.

Last, I'd like to look at your entire *dmesg* for clues. Please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Now you will find a file, dmesg.zip that you can transfer with a USB stick and post as an attachment to your reply.

This will be of little comfort, but there are easy questions on this forum and there are very difficult, almost unsolvable ones. Everything looks just about perfect about your settings, especially this:>  20.609755] r8169: eth0: link upExcept, it doesn't actually connect and work!

---

### Post by macca_dacca on 2010-03-06
Thanks for your perserverence Chili.  I think I am learning a lot from this.
 
Had a look at the BIOS and nothing jumped out at me - all looks OK from my interpretation.  To make things simple I disabled the motherboard ethernet controller as other posts suggest problems with the r8169 driver.  It reboots with the ethernet card (RTL 8139C) as eth0 which is using .
 
  
Also I re-install Ubuntu 9.04 so it is a clean distribution.
 
My first commend was 
 
[COLOR=purple]dmesg >dmesg.txt[/COLOR]
[COLOR=purple]zip dmesg.zip gmesg.txt[/COLOR]
 
as attached.
 
[COLOR=purple]ethtool -i eth0[/COLOR]
[COLOR=blue]driver: 8139too[/COLOR]
[COLOR=blue]version: 0.9.28[/COLOR]
[COLOR=blue]firmware-version:[/COLOR]
[COLOR=blue]bus-info: 0000:03:01.0[/COLOR]

---

### Post by chili555 on 2010-03-08
Here are several suggestions. First, is this dual-booting with Windows?

[http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/#post2931777](http://www.linuxquestions.org/questions/linux-networking-3/realtek-813981688169-on-2.6.21.3-or-newer-593495/#post2931777)

Second, has this setup worked with any operating system or live CD, ever? Have you carefully checked the ethernet cable itself? The port you are plugged into in the router, switch, modem or other internet appliance? If you have a router that plugs into a cable modem, have you double-checked those connections and cables?

Is this a DSL or similar PPPOE connection, where a user name and password are required?

If you right-click NM and select Edit Connections, edit your eth0 interface and select IPv6 settings, is 'Ignore' selected? See attached.

Your *dmesg* looks about as perfect as I'd ever want to see. It's just so mysterious that two of the best-supported, most common ethernet cards refuse to connect.

You obviously have the install CD so that, if we get desperate enough, we can remove Network Manager entirely and rule it out as the troublemaker.

---

### Post by macca_dacca on 2010-03-08
Hi Chili
 
The PC is 100% Ubuntu - no Windows.
When I take out the Hard Drive and attach it to my old 386 the connection works fine so that means the ethernet cable and connection are both OK.
 
I don't know what this means: "Is this a DSL or similar PPPOE connection"
 
When I right click on NM and edit the Wired connection and click the Edit tab to edit Auto Ethernet I get only three tabs showing up: "Wired", "802.1x Security" and "IPv4 Settings".  There is no "IPv6 Settings" tab as in your attached thumbnail.
Maybe the system automatically detects "no IPv6 routers present" as listed in dmesg?
 
I am willing to try anything to get this going on my newly built PC.
How do I remove network manager to rule this out?
I thought by editing /etc/network/interfaces and adding:
[COLOR=purple]auto eth0[/COLOR]
[COLOR=purple]iface eth0 inet dhcp[/COLOR]
[COLOR=black]the system would detect this and automatically turn NM off - but maybe I am wrong.[/COLOR]
 
Thanks again - I appreciate this.

---

### Post by chili555 on 2010-03-08
> I thought by editing /etc/network/interfaces and adding:
auto eth0
iface eth0 inet dhcp
the system would detect this and automatically turn NM off - but maybe I am wrong.I thought NM was intended to work that way, but it surely doesn't. Even worse, when we put those stanzas in the file and do commands like dhclient and iwconfig, the system acts like it's going to work, but just doesn't.

Let's cross our fingers and toes, fasten our seatbelts and try to connect without NM. ```
sudo apt-get remove --purge network-manager*
sudo gedit /etc/network/interfaces
```Make it look like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth1
iface eth1 inet dhcp
```The comment symbol, #, says that we know about eth1, but don't start it on boot. Proofread, save and close gedit. Restart networking.```
sudo /etc/init.d/networking restart
```Either we will get some clues in the terminal as to what is going wrong, or, more likely, it will connect. If it doesn't start, you might reboot.

I will be waiting for your good report!

---

### Post by macca_dacca on 2010-03-09
Another 3 hours and no good news on getting my wired internet connented.
I tried your suggestions above without any success.
 
My attention tonight was to focus on the ipv6 as I thought there might be some incompatability occuring between the motherboard which supports ipv6 and the router (tp-link) which possibly does not support ipv6.  I had another hard disk with Ubuntu 8.04 installed (it also connects to internet on my old 386) and used this to turn ipv6 off for testing on my new PC (I ended up switching shorewall off as well because it required ipv6).  lsmod did not even list ipv4 so maybe I created another problem.
 
My attempt at switching ipv6 off did not help me connect to the internet on my new PC.  The problem is somewhere between the new motherboard and ethernet controllers and possibly extending to an incompatability with the router, but so far I am no closer at narrowing down the problem.

---

### Post by chili555 on 2010-03-09
What is the model of the motherboard? Are there bug reports about its compatability with Linux? Sometimes, bug reports will include an ugly hack workaround.

Did you try both eth0 and eth1? Does:```
sudo dhclient eth0
```just time out or are there interesting messages? Anything interesting in *dmesg *after dhclient runs?

---

### Post by psusi on 2010-03-09
Motherboards are not compatible or not with IP anything.  Very few ISPs support IP6 so forget about that, IP4 is the standard.

What does sudo ifconfig eth0 say?

---

### Post by macca_dacca on 2010-03-09
psusi thanks for your interest.  I posted the results of [COLOR=purple]ifconfig[/COLOR] in message #13 of this thread.
 
chili the output from [COLOR=purple]dhclient eth0[/COLOR] with the Ubuntu 8.04 HD looked OK eg
[COLOR=blue]There is already a pid file /var/run/dhclient.pid with pid 134519072[/COLOR]
[COLOR=blue]Internet Systems Consortium DHCP Client V3.0.6[/COLOR]
[COLOR=blue]Copyright 2004-2007 Internet Systems Consortium.[/COLOR]
[COLOR=blue]All rights reserved.[/COLOR]
[COLOR=blue]For info, please visit [/COLOR][[COLOR=blue]http://www.isc.org/sw/dhcp/[/COLOR]]("http://www.isc.org/sw/dhcp/")
[COLOR=blue][/COLOR] 
[COLOR=blue]Listening on LPF/eth0/00:e0:1c:3d:0b:90[/COLOR]
[COLOR=blue]Sending on  LPF/eth0/00:e0:1c:3d:0b:90[/COLOR]
[COLOR=blue]Sending on  Socket/fallback[/COLOR]
[COLOR=blue]DHCP on eth0 to 255.255.255.255 port 67 interval 7[/COLOR]
[COLOR=blue]DHCP on eth0 to 255.255.255.255 port 67 interval 12[/COLOR]
[COLOR=blue]DHCP on eth0 to 255.255.255.255 port 67 interval 12[/COLOR]
[COLOR=blue]No DHCPOFFERS recieved.[/COLOR]
[COLOR=blue]No working leases in persistent database - sleeping.[/COLOR]
[COLOR=black]The output from [/COLOR][COLOR=darkred]/etc/init.d/networking restart [/COLOR][COLOR=black]using Ubuntu 9.04 lastnight (9 hours ago) looked OK except that I got No DHCPOFFERS recieved.[/COLOR]
[COLOR=#0000ff][/COLOR] 
 
I did a Google search for the motherboard (I've heard it has just come out recently) it is a Gigabyte S-series Motherboard H55M-S2H but could not find any posts suggesting any problems.
 
Thanking you again for all your interest!

---

### Post by macca_dacca on 2010-03-12
Has anyone else used a H55M-S2H motherboard and managed to get internet connection ? 
 
I am running low on ideas.
Perhaps the problem is somehow related to the newer H55 chip.
 
As a long shot does anyone think it may be worth while installing the latest kernel 2.6.33 to try and get the internet back on line ?

---

### Post by chili555 on 2010-03-12
> does anyone think it may be worth while installing the latest kernel 2.6.33 to try and get the internet back on line ?Yes. I think you might have the best luck if you install an Ubuntu .deb file. Please check here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33/)

---

### Post by macca_dacca on 2010-03-12
I have installed the latest kernels 2.6.33 and 2.6.34rc1 but still get No DHCPOFFERS recieved.  I think my last option before throwing away the motherboard would be to try one more ethernet card as I am lost for ideas.

---

### Post by psusi on 2010-03-12
What does sudo ifconfig say?  And sudo mii-tool -v?

---

### Post by macca_dacca on 2010-03-12
Managed to get internet connection for short period. What I did was replace the Ubuntu 9.04 HD and replace it with my MS Windows HD. I aborted the Windows boot when I saw a message that I needed to re-register ... the only way I knew was by pulling the plug. Within a minute I exchanged HD and rebooted with my Ubuntu 9.04 (it still has the kernel I installed last night)
[COLOR=purple]#uname -r[/COLOR]
[COLOR=blue]2.6.34-020634rc1[/COLOR]
but I don't think that had anything to do with the connection.
[COLOR=purple]#ethtool -i eth0[/COLOR]
[COLOR=blue]driver: r8169[/COLOR]
[COLOR=#0000ff]version: 2.3LK-NAPI[/COLOR]

[COLOR=black]I did an #ifconfig and it did not show the [COLOR=blue]eth0:avahi Link ...[/COLOR] listed below. I thought this looks promising so I opened up firefox. The website almost timed out (took about a minute) but brought up an internet site!!! I tried to bring up the links from the website but then got address not found. I did another ifconfig and got:[/COLOR]
 
#ifconfig
[COLOR=blue]eth0 Link encap:Ethernet HWaddr 6c:f0:49:0e:1d:24 [/COLOR]
[COLOR=blue]inet6 addr: fe80::6ef0:49ff:fe0e:1d24/64 Scope:Link[/COLOR]
[COLOR=blue]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=blue]RX packets:4427 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=blue]TX packets:456 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=blue]collisions:0 txqueuelen:1000 [/COLOR]
[COLOR=blue]RX bytes:293083 (293.0 KB) TX bytes:29449 (29.4 KB)[/COLOR]
[COLOR=blue]Interrupt:27 [/COLOR]

[COLOR=blue]eth0:avahi Link encap:Ethernet HWaddr 6c:f0:49:0e:1d:24 [/COLOR]
[COLOR=blue]inet addr:169.254.2.213 Bcast:169.254.255.255 Mask:255.255.0.0[/COLOR]
[COLOR=blue]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR]
[COLOR=blue]Interrupt:27 [/COLOR]

[COLOR=blue]lo Link encap:Local Loopback [/COLOR]
[COLOR=blue]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR]
[COLOR=blue]inet6 addr: ::1/128 Scope:Host[/COLOR]
[COLOR=blue]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR]
[COLOR=blue]RX packets:192 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
[COLOR=blue]TX packets:192 errors:0 dropped:0 overruns:0 carrier:0[/COLOR]
[COLOR=blue]collisions:0 txqueuelen:0 [/COLOR]
[COLOR=blue]RX bytes:19536 (19.5 KB) TX bytes:19536 (19.5 KB)[/COLOR]
 
mii-tool -v
[COLOR=#000000][COLOR=blue]eth0: negotiated 100baseTx-FD flow-control, link ok
  product info: vendor 00:07:32, model 17 rev 2
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-HD 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control[/COLOR]
[/COLOR]

 
Seems as though my attempt to initiate a boot in Windows was sufficient to bring up the internet line and get connected. While the line was still up my Ubuntu system could tap into it briefly before getting disconnected. Looks like I can now rule out physical hardware and perhaps my attention should focus on a compatible driver. 
 
At this stage I do not know if the driver problem is somehow related to the new motherboard (H55M-S2H) but perhaps that brief internet encounter may give someone other ideas?

---

### Post by macca_dacca on 2010-03-12
I now have internet access!
I have logged on three times and it's still there (yippee)
 
[COLOR=black]Tried[/COLOR]
[COLOR=purple]#/etc/inid.d/networking restart[/COLOR]
and I get renewal of the IP address.
Hopefully when the IP address expires I will still be able to get a connection.
 
Not too sure why it is now getting connected.
Perhaps it was the new kernel that helped?? But why didn't it work as soon as I installed the new kernel?  Something is geting it to work now and not before and sorry for those who have the same problem as I cannot pinpoint it.
My setup is:
Ubuntu 9.04 base
Network Manager uninstalled
kernel 2.6.34-020634rc1-generic
ethernet drive r8169
 
Thanks very much for all those who have helped.
I have learnt so much along the way and perhaps I can help others.

---

### Post by macca_dacca on 2010-03-12
Just done one more test.
Replaced the Ubuntu 9.04 HD with my Ubuntu 8.04 HD and the connection still works.
Therefore the connection had nothing to do with the kernel upgrade as previously mentioned.
 
Hmmm???

---

### Post by chili555 on 2010-03-13
Hmmmm, indeed! I am very glad it's working. It was a very difficult case, as you know.

---

