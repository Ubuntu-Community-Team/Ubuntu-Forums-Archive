---
title: "INTERNET problem..."
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by niyaz_ on 2010-03-05
internet problem...:( 
hey ppl...m cmpltly new to ubuntu..js installed it 2day...bt m nt able to use net..also i hv NO knwledge abt ubuntu..

i put all the information(IP,gateway,Subnetmask) in WIRED-->manually...i cn ping my ip frm network tools...bt cnt use net...

in firefox...wen i type 74.125.87.104...the google page opens...bt i cnt go to anywer else...ths proves (i gues) i have a problem wid DNS...

i also edited dhclient.conf...i typed 
""prepend domain-name-servers 172.16.16.1;"" in tht page...still no use...
plz som1 help me...m rili tired of ths windows..n want to use ubuntu....

---

### Post by JackRock on 2010-03-05
I can't tell what you're saying with all the Leetspeak, but I THINK you are having problems going to any site using a domain name instead of an IP address.

Who is your ISP?  What settings do you have in the Network Connections?  Do you have more than one adapter listed there?

---

### Post by niyaz_ on 2010-03-05
m in bangladesh...i tuk a connection frm local ISP..i gave xp n ubuntu..in xp..its wrkin js fine....i hv only 1 netwrkcard...

m tryin frm whle mrnin...readin forums n other sites...js nt wrkin....tried so mny thngs..:(

---

### Post by 2hot6ft2 on 2010-03-05
Mods this is a duplicate thread of
internet problem...:(
[http://ubuntuforums.org/showthread.php?p=8920316](http://ubuntuforums.org/showthread.php?p=8920316)

---

### Post by niyaz_ on 2010-03-05
yeah it is...i had posted it in multimedia by mstke....

---

### Post by niyaz_ on 2010-03-05
hey...plzz gmme a solution if can...plzz

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> yeah it is...i had posted it in multimedia by mstke....
The mods will move it to the proper place for it. No need to start a new thread for the same problem. At least you did look for the right place to put it.

---

### Post by niyaz_ on 2010-03-05
ty...cn u gmme a soln to ma prob too??

---

### Post by 2hot6ft2 on 2010-03-05
Have you set your connection up in network manager?
The applet is on the top panel on the right hand side.
Network Tools which is the pic you attached to the other thread is NOT where you setup connections.

---

### Post by niyaz_ on 2010-03-05
i hv done smthn in netwrk connections n dhclient.conf......thts it...

---

### Post by 2hot6ft2 on 2010-03-05
Right click on the network manager applet and select Edit Connections.
There you can put in your connection information.

---

### Post by niyaz_ on 2010-03-05
yeah i did tht...it pings too...i ll gv u the screenshots...

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> yeah i did tht...it pings too...i ll gv u the screenshots...
It shouldn't say ifupdown.
Undo what you have done (like your edit of dhclient) and reboot then set your connection up in network manager by selecting the wired connection and then Edit
Put your information in the proper paces in the window that will open.
Click Apply and you should be set.
You may have to reboot for everything to clear any previous changes to the system and start with your new connection information set in the system.

---

### Post by niyaz_ on 2010-03-05
hw shud i undo it??...i cnt edit enthn....the edit option is disabled...:(...

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> hw shud i undo it??...i cnt edit enthn....the edit option is disabled...:(...
You have to select a connection for the Edit option to be available.
So Select the **ifupdown** connection

I have network manager disabled on mine so I can't take screen shots to show you. Someone else will have to do that.

---

### Post by niyaz_ on 2010-03-05
yeah i did tht...many tyms.dsnt wrk..shd i add a new 1??

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> yeah i did tht...many tyms.dsnt wrk..shd i add a new 1??
You can if you want. Like I said you may have to reboot to clear the changes you made before and to start with the new settings you just made in case there are conflicts.

---

### Post by niyaz_ on 2010-03-05
i did sme thngs...added a new 1...i gv thescreenshots....stil no luck....

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> i did sme thngs...added a new 1...i gv thescreenshots....stil no luck....
Ok, select the ifupdown connection and click delete.
Open a terminal
Applications > Accessories > Terminal and copy and paste these in it one at a time and post the results.
```
ifconfig
```
```
route -n
```
```
lspci
```

---

### Post by niyaz_ on 2010-03-05
k i ll gv u the output in a while..but wen i click on ifupdown ..edit n delete option is disabled...nway i ll gv u the output...

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> k i ll gv u the output in a while..but wen i click on ifupdown ..edit n delete option is disabled...nway i ll gv u the output...
That's probably because of the edit you made to dhclient or settings you set in
System > Administration > Network
or
System > Administration > Network Tools

---

### Post by niyaz_ on 2010-03-05
niyaz@niyaz-desktop:~$ ifconfi
g
eth0      Link encap:Ethernet  HWaddr 00:21:27:c6:8c:26  
          inet addr:172.20.17.139  Bcast:172.20.17.255  Mask:255.255.248.0
          inet6 addr: fe80::221:27ff:fec6:8c26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6 txqueuelen:1000 
          RX bytes:364409 (364.4 KB)  TX bytes:4312 (4.3 KB)
          Interrupt:18 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



niyaz@niyaz-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.20.16.0     0.0.0.0         255.255.248.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.20.16.1     0.0.0.0         UG    100    0        0 eth0


niyaz@niyaz-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
niyaz@niyaz-desktop:~$ 



ooops..cn u undstnd ths??...i saved it in ubuntu..bt hre in xp...everythn gt together...

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> niyaz@niyaz-desktop:~$ ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:21:27:c6:8c:26  
          **inet addr:172.20.17.139  Bcast:172.20.17.255  Mask:255.255.248.0**
          inet6 addr: fe80::221:27ff:fec6:8c26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:6 txqueuelen:1000 
          RX bytes:364409 (364.4 KB)  TX bytes:4312 (4.3 KB)
          Interrupt:18 Base address:0xb800 

```


niyaz@niyaz-desktop:~$ route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**172.20.16.0**     0.0.0.0         255.255.248.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         **172.20.16.1**     0.0.0.0         UG    100    0        0 eth0

```

niyaz@niyaz-desktop:~$ lspci
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
02:01.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
**02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**
```
niyaz@niyaz-desktop:~$ 



ooops..cn u undstnd ths??...i saved it in ubuntu..bt hre in xp...everythn gt together...
You didn't put it in code boxes using the # sign in the top of the post window is why it looks like that. The code box saves the formatting.
```
eth0      Link encap:Ethernet  HWaddr 00:21:27:c6:8c:26  
          **inet addr:172.20.17.139  Bcast:172.20.17.255  Mask:255.255.248.0**

```
Shows your information is set for eth0 which is your ethernet connection.
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**172.20.16.0**     0.0.0.0         255.255.248.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         **172.20.16.1**     0.0.0.0         UG    100    0        0 eth0

```
That's the way the kernel is routing traffic and it doesn't match your configuration.
**16 instead of 17**.
I think that somewhere you changed things and used 16 instead of 17.
Go back thru
The dhclient you changed.
System > Administration > Network
System > Administration > Network Tools
and network manager applet
And find the error and fix it.
```

**02:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)**
```
That is your Ethernet cards information so it is being seen by the system.
Once you find and fix the error things should work.

---

### Post by niyaz_ on 2010-03-05
IP : 172.20.17.139
Subnet: 255.255.248.0
gateway: 172.20.16.1
DNS: 172.16.16.1   172.16.16.2

thse r ma configurations...cn u please tel me wt all to do...temme everythn..i dunno wt all i did...werver i saw sme soln..i did it..m nt sure evenm if it rt..plz..

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> IP : 172.20.17.139
Subnet: 255.255.248.0
gateway: 172.20.16.1
DNS: 172.16.16.1   172.16.16.2

thse r ma configurations...cn u please tel me wt all to do...temme everythn..i dunno wt all i did...werver i saw sme soln..i did it..m nt sure evenm if it rt..plz..
Is your keyboard broke?
Okay, I don't know why your gateway is different than your network so lets start with the basics of your setup.

Are you directly connected to your ISP (computer to Internet)?
Are you connected directly to a dsl or cable modem (computer to modem to Internet)?
Are you using a router(computer to router to modem to Internet)?
Is your IP Address dynamic (is it assigned by the ISP and DOES change)?
Or static (is it assigned by the ISP and DOES NOT change)?

---

### Post by niyaz_ on 2010-03-05
lol...ma keyboard is fine...thts wt m usin in xp n its wrkin fine..its static...ma isp gv me thse configurations...n yes m cntcd to ma isp drctly...i mean...the gv me conction..n i plug tht into ma lancard....

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> lol...ma keyboard is fine...thts wt m usin in xp n its wrkin fine..its static...ma isp gv me thse configurations...n yes m cntcd to ma isp drctly...i mean...the gv me conction..n i plug tht into ma lancard....
Could have fooled me since most of the letters are missing from your words.
Then everything is setup according to your information.
The only thing I can think of in that case is to delete one of the 2 wired connections in Network Manager and set the remaining connection to your configuration.
If you can't delete the ifupdown one then you'll have to delete the other one.
Somewhere you put some information that changed it from auto eth0 to ifupdown and I don't know where you did it.

I don't know how else to solve your problem. Sorry.

---

### Post by niyaz_ on 2010-03-05
ty rili..u spent a lotsa tym wid my prob...thnx a alot...

---

### Post by 2hot6ft2 on 2010-03-05
> **niyaz_ said:**
> ty rili..u spent a lotsa tym wid my prob...thnx a alot...
You're welcome. Hope you find the problem and solution soon.

---

### Post by hfxrzw on 2010-03-05
Hi, I have/had the same problem as the OP.Following the above I now have the card listed as eth1 instead of eth0 and the same "ifupdown" listed as eth0, which I can't delete.
I can't get the use of the eth1 however. Completely at a loss here. The problem happened when I had to reboot the computer after a Wine program failed (EAC set-up). 
The /etc/network/interfaces only shows the loopback adaptor settings. 
The /etc/init.d/networking restart does NOT give the message re eth as above. Just *reconfiguring network interfaces    [OK].
The ifconfig gives me eth1 as ethernet and lo for the loopback. No info re eth0.

Any idea what's going on?

Thanks, Rene.

Just noted that eth1 is the wireless network card, not the ethernet card. It seems the ethernet card is not detected, although the green light is on next to the socket???

---

### Post by bhuvi07 on 2010-03-05
ny idea were to fix the WI-FI problems..

---

### Post by hfxrzw on 2010-03-05
No WiFi problem here mate.

---

### Post by 2hot6ft2 on 2010-03-05
Found a thread that may solve the problem here:
[How to remove ifupdown(eth0)?? ]("http://ubuntuforums.org/showthread.php?t=1316705")

---

### Post by niyaz_ on 2010-03-06
thnx bro....its wrkin nw...thnx a lot

---

