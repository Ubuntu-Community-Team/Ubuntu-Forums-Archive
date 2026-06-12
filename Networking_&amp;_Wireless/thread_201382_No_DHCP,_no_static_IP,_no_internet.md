---
title: "No DHCP, no static IP, no internet"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by Vcount on 2006-06-21
I really need a linux guru.  

No internet.  This has been a recurring problem for me with linux.  I've tried for ten hours with Suse 10 to get internet, and it's been stumping two of their message boards continuously for two days.  Finally, I got sick of it and decided to go to Ubuntu, because I like it better and if I'm not going to have internet anyways, it may as well be with an OS that I like.  

So I now have a fresh, just installed Dapper for 64 bit processors on my computer, and I'm very impressed.  It's blazingly fast!  It's convenient!  It had no problems installing!  All more than I can say for Suse or U-64 Breezy, so I'm favorably impressed from the beginning here.  Except I STILL have my recurring problem of no internet with linux.  

So, to begin.  I have a linksys wireless router working as my hub, and use DHCP for windows.  Windows has no internet problems.  My network card is two integrated Nvidia ethernet adapters on an MSI K9N mobo.  They are both active, and show up in Ubuntu's networking administration.  

I've tried deactivating one of them, no internet.  I've tried getting the static IP from windows that has working internet and entering those, the subnet mask, and the default gateway of my router (192.168.1.1), no internet.  I've tried with both cards with static IP and activated, no internet.  I've tried deactivating first one and trying the remaining one, then the other and trying the remaining one with static IP, no internet.  I've tried having both activated, and one be static and the other be DHCP, no internet.  

I feel I should mention at this point that I don't have the firewall installed, so that is not an issue.  

Here are some of the ifconfig and lspci logs:

ifconfig

buu@TenchuLightbox:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:42:99:AF
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe42:99af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:228 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:16:17:43:1D:8F
          inet6 addr: fe80::216:17ff:fe43:1d8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:12 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:50

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:687 errors:0 dropped:0 overruns:0 frame:0
          TX packets:687 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53091 (51.8 KiB)  TX bytes:53091 (51.8 KiB)


ifdown and ifup for a DHCP one

buu@TenchuLightbox:~$ sudo ifdown eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:16:17:43:1d:8f
Sending on   LPF/eth1/00:16:17:43:1d:8f
Sending on   Socket/fallback
buu@TenchuLightbox:~$ sudo ifup eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth1/00:16:17:43:1d:8f
Sending on   LPF/eth1/00:16:17:43:1d:8f
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Here's lspci

buu@TenchuLightbox:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
0000:00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
0000:00:01.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
0000:00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
0000:00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:06.0 PCI bridge: nVidia Corporation: Unknown device 0370 (rev a2)
0000:00:06.1 0403: nVidia Corporation: Unknown device 0371 (rev a2)
0000:00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:09.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 0374 (rev a2)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 0378 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 0375 (rev a2)
0000:00:0f.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:06:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00c3 (rev a2)


And finally, here is a relevant section of dmesg.  I have the whole dmesg if it will help anyone.  

[  528.792121] eth0: tx_timeout: dead entries!
[  633.032324] eth1: no IPv6 routers present
[  696.096244] eth0: no IPv6 routers present
[  738.664713] NETDEV WATCHDOG: eth0: transmit timed out
[  738.664717] eth0: Got tx_timeout. irq: 00000000
[  738.664720] eth0: Ring at 3e252000: next 64 nic 0
[  738.664722] eth0: Dumping tx registers

So I PRAY that somebody here on the ubuntu forums will be able to help me, because I've had no luck myself with hours of tinkering, and had no luck finding a linux internet guru either.  Thanks in advance.

---

### Post by doonium on 2006-06-21
nm...

---

### Post by Lungs on 2006-06-22
Hey, I couldn't help but notice a suspicious 'nm...', does that mean 'nevermind' and if so has the problem then been fixed?  I am curious only because the problem described resembles mine, and if it has been solved I would be grateful if that information were leaked!  Haha, hopefully that was polite enough, if not - thankyou!

I've been weened onto Linux, which has been excellent, but unfortunately I haven't yet been able to fend for myself.  Having network issues is a common problem for me and my school quality computer, it likes to confuse things and usually it's only a matter of tweaking before it is restored to an useful state.  However, this time round, there doesn't *seem* to be anything wrong (in my untrained eye), and I am slightly too inept to deal with this in a respectible fashion!  If I could be helped, or instructed on how to prepare for help, I would be a much happier man.  Thankyou.

---

### Post by Vcount on 2006-06-22
Alas, no my friend.  That "nm" wasn't from me, it was from a well-wisher who had thought I was trying to do wireless internet, and he had told me to do iwconfig and get the essid.  

I know that because that's the reply I saw in the "you got a response" email.  But I think that he noticed that I wasn't wireless, so he edited that out and put "nm".  

So, my problem is still unresolved.  I'm working on it as best I can, but haven't had any success yet.  If I figure it out, I'll be sure to post it back here, to let you know.

---

### Post by Vcount on 2006-06-22
I finally got internet.  

After pinging my router and getting nothing (among hours of other troubleshooting things), I decided that Ubuntu was having troubles with my integrated mobo lan adapters.  So I put in a Netgear PCI card I had lying around, and it solved my problem.  

So apparently, Ubuntu doesn't have the drivers for the newest Nvidia network adapters or something, but if you go with an older PCI card it'll have no troubles.

---

### Post by NamShubCMX on 2006-08-19
If anyone finds a fix, please let us know. I too had to install a PCI card to work, but I'm running short on PCI resources (had to uninstall the TV tuner) so any help would be appreciated.

The weirdest part is that the built-in Nvidia ethernet card works with all other linux I tried + winxp

---

### Post by hajk on 2006-08-20
Hey Vcount, I notice from the data in your original post that apparently the eth0 interface is up and has an IP (192.168.1.108) assigned to it. What confuses me is what the second NIC (eth1) is for, you don't want two simultaneous connections to the LAN, do you? So, why not set eth0 as the default route (you could do that in the System/Administration/Networking menu, and possibly set your router as the DNS, and then you should have internet... 

Just my €0.02 worth.

---

### Post by Vcount on 2006-08-20
Well **hajk** I did try disabling first one and then the other network card, so that I only had one active, and it never did a thing for me.  I also fiddled with DNS while doing so, and I had the configuration you suggest at one time (one card not active, one card active, router as DNS), and it never worked.  

It seems for some reason, Ubuntu just doesn't like the newer Nvidia ethernet adapters.  On that subject, **NamShubCMX**, have you tried downloading newer nvidia modules?  I could never find one that worked for my application, so was always only using the forcedeth module, but perhaps you can find one for yours.  Then you could free up your PCI slot.

---

### Post by nkassi on 2006-08-20
It dosen't sound like a driver problem since the card is recognized and is assigned to an interface. 

The problem might be at the router level.(mostly a guess) What kind of router are you using ? 

Nic

---

### Post by nkassi on 2006-08-20
Also if you bypass the router and connect the computer directly to what ever  internet connection you have do you get any problem ?

Nic

---

### Post by Vcount on 2006-08-20
I was using a linksys router, with the standard linksys 192.168.1.1 address.  

And no, it never worked with the nvidia adapters.  Also, I tried multiple times to either A) go direct from modem to computer, no router, and B) trying to use an SMC router instead, and neither of those things worked at all.  

The only thing that worked is putting a seperate PCI card in, and then any and all router or DNS or modem combinations worked.

---

### Post by scxtt on 2006-08-20
what's your output for /etc/resolv.conf? -- can you connect to your router via a browser? -- what DE are you using?

---

### Post by hajk on 2006-08-20
> **Vcount said:**
> 
It seems for some reason, Ubuntu just doesn't like the newer Nvidia ethernet adapters. 


It is not a hardware problem, look at the output of ifconfig in your original post: eth0 is up and has received an IP from the DHCP server in your network. 

Conclusion: it must be a configuration problem, most likely a DNS problem or the default route (gateway) not set up right. What is the output of the "sudo route" command? What are the contents of /etc/resolv.conf? Can you ping the router?

---

### Post by Vcount on 2006-08-20
Okay, this isn't even a problem for me anymore, the PCI card fixed it and I was fine with that.  I was only posting again to try and help out **NamShubCMX**, who didn't want to use up a PCI slot on something he should have onboard.    

But you know, I'm curious as to why the damn thing never worked too.  

So here's my current resolv.conf, this is with the PCI card, and connected directly to the modem.  

search gateway.2wire.net
nameserver 172.16.0.1

I will hook up the router, and get back to you guys on the resolv.conf for the non-working internet setups using the onboard ethernet adapters.  I will have to get back to you on that, because I won't have internet when I'm trying to use the router, so this may take some time.  

I do remember from back when I was trying to get the onboard ethernet to work that it wouldn't even ping the router at all, and you couldn't reach it by typing 192.168.1.1 in the address bar.  

I'm not sure what you mean by what DE I'm using.  What is a DE?

---

### Post by scxtt on 2006-08-20
DE is Desktop Environment (i.e. Gnome or KDE, mainly) ... i asked because it will determine which tools you'd use to correct things (if it's the problem i'm thinking you have) ...

basically i think your onboard adapter isn't getting nameserver info from your router and your router isn't being set to the default gateway ... which is why you can't connect to the router and why you can't view webpages (it doesn't know what to do w/ something like [www.google.com](www.google.com), that's the job of the nameserver) ...

i NEVER used to have that problem (i use onboard as well) until i installed KDE (don't think that's why) - so i have to specify to use 192.168.1.1 as the gateway and i HAVE TO enter my DNS nameservers - then it works fine ...

---

### Post by leargaf on 2006-08-20
Hi, 
I have the same problem, eth0 is up and has received an ip but still no internet. Coul you please tell me how to fix the router/dns problem?
Below are the outputs from resolv.conf and sudo route. Thanks!
resolv.conf:
search gateway.2wire.net
nameserver 192.168.1.254
sudo route:
Destination: 192.168.1.254
Gateway: *
Genmask: 255.255.255.0
Flags: U
Metric: 0
Ref: 0
Use: 0
Iface: eth0
Destination: default
Gateway: 192.168.1.254
Genmask: 0.0.0.0
Flags: UG
Metric: 0
Ref: 0
Use: 0
Iface: eth0

---

### Post by Vcount on 2006-08-20
Okay!  

Yeah, doing this pretty much screwed up my internet to the point where it took a good 15 minutes of tinkering to get it back up.  Ubuntu kept freezing when I tried to sudo ifup eth3.  

But I got the /etc/resolv.conf for the nonworking internet setups.  Here's the first one, plugged in through my linksys router, 192.168.1.1

Here's ifup for it;

Listening on LPF/eth0/00:16:17:42:99:af
Sending on   LPF/eth0/00:16:17:42:99:af
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 39841 seconds.

And here's sudo route for it;

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

And finally /etc/resolv.conf

search gateway.2wire.net
nameserver 172.16.0.1

Every ethernet adapter but my onboard eth0 was off.  It actually successfully got a DHCP, which it in fact didn't used to do.  I was mildly surprised.  But the internet still didn't work.  I went in and added a DNS entry for 192.168.1.1, and still no dice.  

SO, I decided to try it no router, direct to modem.  

Here's sudo route for it;

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface172.16.0.0      *               255.255.0.0     U     0      0        0 eth1default         172.16.0.1      0.0.0.0         UG    0      0        0 eth1

And /etc/resolv.conf 

search gateway.2wire.net
nameserver 172.16.0.1


Still no internet.  This time I connected it up to eth1 onboard adapter (I have two onboard ethernet adapters), just for kicks.  I deactivated eth0 before doing that.  And still no internet.  

Of course, after doing all of this, when I plugged the cord back into eth3 and tried sudo ifup eth3, Ubuntu totally froze every time I tried it, to the point where all I could do was push the reset button, as it wouldn't recognize mouseclicks.  I even ctrl alt f1'd, got terminal up, got back into xwindows, and tried xkill to kill the frozen apps (mozilla), and it said no mouse cursor or some such nonsense.  I could move the mouse around, but no button clicks were recognized.  

But in any event, there is the nonworking /etc/resolv.conf and sudo routes.

---

### Post by Vcount on 2006-08-20
Oh, also I tried pinging the router and the modem, respectively both of the nonworking internet times, and got 100% packet loss.

And my DE is gnome.

---

### Post by neouser99 on 2006-08-20
that resolv.conf that you are getting isn't even close to right. what is your isp? university? cable? dsl? neither are your routes on the two onboard interfaces, which really really doesn't make any sense what so ever. unless this is your setup...

you have a dsl 2wire modem with a linksys router behind it. if this is the case, then you do not need the linksys router, as the 2wire modem is a router, in disguise :) basically all i am asking for is a network map, and some more specifics on the devices. are the two onboard cards gig? what about the pci? is the router gig? what brand? what is the modem? and what is your isp?

-neo

---

### Post by scxtt on 2006-08-21
neouser99 is right, not much about your resolv.conf makes sense ... i'll give you (most of) the output from my /etc/network/interfaces and /etc/resolv.conf and you should do something similar ...
```
:> cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
```this sets up my ability to connect to my router ...
```
:> cat /etc/resolv.conf
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver <IP #1 supplied by my ISP>
nameserver <IP #2 supplied by my ISP>
```once you can connect to your router, you should be able to get your nameserver addresses from it, which you can put in /etc/resolv.conf ...

---

### Post by Vcount on 2006-08-21
> **neouser99 said:**
> 
you have a dsl 2wire modem with a linksys router behind it. if this is the case, then you do not need the linksys router, as the 2wire modem is a router, in disguise :) basically all i am asking for is a network map, and some more specifics on the devices. are the two onboard cards gig? what about the pci? is the router gig? what brand? what is the modem? and what is your isp?

-neo

Well, the setup I have is actually the 2wire modem in the living room, then the line goes from modem into an ethernet hub.  One line from the hub is coming into my bedroom, to the linksys router (which I basically just use as a hub in my BEDROOM).  I am aware I don't NEED the linksys router, and could just not use a hub and plug ethernet into only one computer in my bedroom (there are 3 or 4 in there), but even THAT doesn't work with any of the onboard ethernet adapters on my linux box.  I tried that this last time, that was the "direct to modem" time, when it almost matched up to resolv.conf because the modem's address is 176.16.0.1.  

As to some more specifics, yes the two onboard ones are gigabit internet capable.  The PCI one is not, I got it from an older box laying around.  I'm not sure if the router is gigabit capable, I'd guess probably not, and the brand is linksys.  It's one of the wireless B linksys routers, I got it for $1.99 once when Compusa was having a sale.  The modem is a 2wire modem, and my ISP is SBC.  

My resolv.conf wasn't THAT far off when I was plugging the modem directly into one of the onboard cards and not getting internet.  After all, it was nearly the setup I had before, with working internet into the PCI card, and resolv.conf was exactly the same then.  

search gateway.2wire.net
nameserver 172.16.0.1

It didn't seem to change at all any of the three times, really.  The working internet resolv.conf and both of the nonworking times were all the same.  It is probably because I have 172.16.0.1 as my DNS, which is what works.  I tried putting 192.168.1.1 in as a DNS as well with the router hooked up, but it didn't change resolv.conf at all.    

Incidentally, EVERYTHING has always worked in windows, straight off the bat.  I can do any networking combination I please in windows.  It was only linux that gave me internet grief and needed a seperate PCI card.  But seeing as I use linux near-exclusively now, that's no small matter.

---

### Post by zerxisk78 on 2006-08-24
I have an asus board with an nvidia integrated network card and I can't connect either if anyone knows a patch or something... well atleast I know it wasn't my doing.

---

### Post by Doogys on 2006-09-05
Hi Vcount, 

I had the same issue with Drapper. 
After getting trouble to get my card able to scan, Then i could connect but no way to get an IP from my router (DHCPDISCOVER issue). 

It was no problem to connect to another router in my area, but not my Linksys WAG54G ;-(

Today troubleshooting for an install of sendmail (boot failure)

I discovered That in the following directory: etc/network/if-down.d/ 
I had a script called "wpasupplicant" i am not using WPA for my router. 

Then I deleted the script (to avoid to run when setting up my Network)

Miracle... It works now. 

Hope for you that it will fix your issue. 

Best Regards, 
Julien

---

### Post by tlh on 2007-05-30
I'm having the same issue on an MSI board with dual gigabit Nvidia Ethernet.  I have been using the machine for several months with Dapper, then decided to upgrade to Feisty.  The connection continued to work through Edgy and Feisty.  The connection stopped working after I installed KVM and Qemu and upgraded numerous packages.    I've been backing out the changes one by one, but no luck so far.

I've also tried all combinations of the two ports, and a static IP address.  The thing we have in common is that the transmit count is 0 and the dropped packet count is non-zero.  My ifconfig returns similar results.  I show lots of received packets, but nothing transmitted and lots of dropped transmit packets.  I think the problem is that the transmitter is disabled somewhere in the driver, MAC or PHY.

---

### Post by Loubart on 2007-06-15
I find i have been having the same issue,

I have set my Dapper box to have static IP 192.168.1.2 but for some reason the WAG54G Linksys gateway keeps assigning 192.168.1.64 (its default Starting IP) I have disabled DHCP server in the router however it keeps assigning an IP only on the Linux machine though my XP machine Keeps it's Static IP 192.168.1.5

I tried reserving the IP 192.168.1.2 to the mac address of the Dapper box in the linksys router but it will still change the IP address at lease renewal

My main annoyance isn't that it will not connect but I have port forwarding for my HTTP, POP3 and other services forwarded to the Dapper box but cant retain 1 IP address permanently to it

Another interesting point is that it has only just started doing it in the last week for the previous 3 months not an issue

So I ask the Question is it the Linksys Router Forcing DHCP even if it is disabled or has an update to Dapper cause an issue that it will not keep a statically assigned IP

---

### Post by thecure on 2007-06-15
As your eth0 was getting it's IP address and such I agree with the other gent who said it was working. Check /etc/network/interfaces and check all the entries. I have four different computers running Feisty and the only one that was a clean install for what ever reason kept adding extra "auto eth0, auto eth1, etc."  to the end of the config file, even though they were already present. (Whenever I clicked to change from wireless to wired or vice-versa on the network icon.( /etc/network/interfaces) Cleaning out all the redundant "auto eth's" brought back the adapters working. Hence the network would work then it would self destruct. Incidentally, the "clean install feisty" was the only one that wouldn't do wep and wpa correctly... I had to manually place the wep key, and the the wpa key in the config file when I changed to that.

---

### Post by mattatt on 2007-10-27
From another site found by googling, I discovered this fix for my problem, which sounds the same:

# service network stop
# modprobe -r forcedeth
# modprobe forcedeth msi=0 msix=0
# service network start

And add the above to your /etc/modprobe.conf file.

---

### Post by mattatt on 2007-10-27
Correction: the modprobe.conf entry should be "options forcedeth msi=0 msix=0" or somesuch.

---

