---
title: "Network Config"
date: 2009-08-03
forum: Networking &amp; Wireless
---

### Post by Topher88 on 2009-08-03
Hey.  Thought I'd give Ubuntu Studio a try.  I installed it today and am dual booting it with Vista, and during the installation it told me that the network configuration failed.  I chose to configure the network later, thinking it should be no big deal, but now I can't figure out how to get my internet working.  I want to use wireless, and in Ubuntu it says that it is using the propriety hardware, but nothing works and I don't know how to configure it.  Everything works in Vista, but when I switch over to Ubuntu, I can't get anything working.  sudo lshw -C network tells me that the wireless is DISABLED even though it is on on my laptop.  Any help would be appreciated...

---

### Post by Topher88 on 2009-08-03
UPDATE:  I was curious to see what would happen if I tried accessing the internet while running the LiveCD version of regular Ubuntu 9.04, and everything runs just like it should.  It still says that it's using propriety hardware, but there are no problems in the network manager (which studio doesn't have for some reason...).  

So what do I need to do?  This obviously has to do with Studio, and I just don't know how to configure it...  and plus, it's just stupid not having network manager O.o wtf is up with that???

---

### Post by Topher88 on 2009-08-03
No ideas at all?  I tried downloading the Network Manager package by using a LiveCD as a source in Synaptics because I had read elsewhere that you can do that, but it wouldn't recognize the CD and said something like "Maybe it's not a Debian CD."

I'm at a loss...  The internet simply won't work without the Network Manager, and why they wouldn't include something so crucial is beyond me...

---

### Post by Topher88 on 2009-08-03
Apparently all I need to do is install Network Manager, but...  That's kind of hard to do without an internet connection; I can't even get internet via an Ethernet cable.  If someone could **please** walk me through configuring the wired connection, I think I can handle the rest.

---

### Post by BigWoop on 2009-08-03
You need to look in Network Connections or configuration or something, I have only looked at Ubuntu a bit myself so I can't tell you exactly (and my install is fsked right now), but an item under system or something like that in the menu.

The window you're looking for should mention an ethernet device or something, look carefully there are a few network windows. You then need to just configure the correct ip settings on your wired device, which I can't really help you with that much.

You need to know the ip of you're router on the network and have an idea of what ip you should assign to your device (it will be similar but the last nuber different) also you need to know the correct subnet. You need someone who "manages" the internet access wherever you are to help you out with that info.

Try setting it to dhcp or automatic and see if that works first, it will be a lot easier.

---

### Post by slakkie on 2009-08-03
i will show you what you can do for now to get your network up and running.

I will give an example based on your windows networking config. This is taken from a virtual machine, but it could have been your config (IP addresses may differ, but the principle applies).

```

C:\Documents and Settings\Wesley>ipconfig /all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : legacyos
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : euronet.nl

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : euronet.nl
        Description . . . . . . . . . . . : AMD PCNET Family PCI Ethernet Adapte
r
        Physical Address. . . . . . . . . : 08-00-27-3C-97-6A
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 10.0.2.15
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 10.0.2.2
        DHCP Server . . . . . . . . . . . : 10.0.2.2
        DNS Servers . . . . . . . . . . . : 10.0.2.3
        Lease Obtained. . . . . . . . . . : maandag 3 augustus 2009 18:33:47
        Lease Expires . . . . . . . . . . : dinsdag 4 augustus 2009 18:33:47

C:\Documents and Settings\Wesley>

```

In Ubuntu, open a terminal (don't know where it is in Gnome, but you should be able to find it easily):

```

sudo nano /etc/network/interfaces

```

Based on the Windows config above we need to make sure we have something like this (the windows config is DHCP, but I will show you both DHCP configuration and static):

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# DHCP enabled
auto eth0
iface eth0 inet dhcp

# Static IP
auto eth0
iface eth0 inet static
gateway 10.0.2.2
netmask 255.255.255.0
address 10.0.2.15
dns-server 10.0.2.3
dns-domain euronet.nl
dns-search euronet.nl


```

It could differ a bit, your interface could be called different, but you can figure that out by ifconfig -a and looking up what it can be:

```

20:09 pts/0 0 wesleys@chanadm-devel:/home/wesleys$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:29:85:b3:93
          inet addr:172.16.175.133  Bcast:172.16.175.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe85:b393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:334847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:52470956 (50.0 MB)  TX bytes:14582008 (13.9 MB)
          Interrupt:17 Base address:0x2000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:194 errors:0 dropped:0 overruns:0 frame:0
          TX packets:194 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11648 (11.3 KB)  TX bytes:11648 (11.3 KB)

```

After you have editted the interfaces file, you need to restart your networking:

```

sudo /etc/init.d/networking restart

```

If you don't understand anything I just said, you could try this thread: [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

Best of luck

---

### Post by Demented ZA on 2009-08-03
> **BigWoop said:**
> You need to look in Network Connections or configuration or something...

BigWoop, I think what Topher88 is saying is there's no Network Connections (Network manager) program installed to begin with.

I havn't tried Ubuntu studio myself yet, but as all Linux distributions, (Network manager is just a gui)

Please tell us a little more about your set up, aka how are you connecting to the rest of the network? Via cable to a modem router? What type/brand modem router. 

Please also do the following in a command console and post the output here (wrap in CODE tags please)

```
ifconfig
```the above lists your network adaptors and thier properties such as IP address etc

```
nano /etc/networking/interfaces
```the above is the config file for your interfaces. It'll tell us what they are configured as.

Edit, sorry i pressed my post button too late, but our advice is similar lol :-P

---

### Post by Topher88 on 2009-08-03
> **Demented ZA said:**
> BigWoop, I think what Topher88 is saying is there's no Network Connections (Network manager) program installed to begin with.

I havn't tried Ubuntu studio myself yet, but as all Linux distributions, (Network manager is just a gui)

Please tell us a little more about your set up, aka how are you connecting to the rest of the network? Via cable to a modem router? What type/brand modem router. 

Please also do the following in a command console and post the output here (wrap in CODE tags please)

```
ifconfig
```the above lists your network adaptors and thier properties such as IP address etc

```
nano /etc/networking/interfaces
```the above is the config file for your interfaces. It'll tell us what they are configured as.

Edit, sorry i pressed my post button too late, but our advice is similar lol :-P

Just want to mention that it's going to be extremely hard for me to copy information over, being that I have no internet at all in Ubuntu, so I can't easily copy/paste information...  I'll do what I can at lunch, but I dougt I'll get very far.

---

### Post by Topher88 on 2009-08-03
Okay, I managed to get the information you requested

```
chris@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:249 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:25:56:5c:58:14  
          inet6 addr: fe80::225:56ff:fe5c:5814/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:23:8b:d8:5c:c7  
          inet addr:169.254.9.21  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:249 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1026 (1.0 KB)  TX bytes:1026 (1.0 KB)
``````

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# DHCP enabled
auto eth0
iface eth0 inet dhcp

```

---

### Post by Topher88 on 2009-08-03
Any ideas?

---

### Post by slakkie on 2009-08-04
[http://ubuntuforums.org/showpost.php?p=7726427&postcount=6](http://ubuntuforums.org/showpost.php?p=7726427&postcount=6) :(

---

### Post by cariboo on 2009-08-04
Are your network devices actually being detected and the drivers loaded? Open an Applications-->Accessories-->Terminal and type

```
sudo lshw -C network > network.txt
```

The above command creates a text file called network.txt which will print a listing of your network devices, copy network.txt to your Windows partition and paste it in your next post.

---

### Post by Topher88 on 2009-08-04
> **slakkie said:**
> [http://ubuntuforums.org/showpost.php?p=7726427&postcount=6](http://ubuntuforums.org/showpost.php?p=7726427&postcount=6) :(

Saw it and tried it once.  Sorry, should have said something...  I couldn't figure out how to get it to work with wireless (eth1), if you can even do that, which is all I could do at home without interfering with everyone else's internet connection, so I was waiting until today at work where I can try it with an ethernet jack (eth0), which I'm about to do, hopefully with better results.  I'll keep you posted.

---

### Post by Topher88 on 2009-08-04
Slakkie:

I am getting this error message:

```
/etc/network/interfaces: 14: interface eth0 declared allow-auto twice
ifdown: couldn't read interace file "/etc/network/interfaces:
/etc/network/interfaces: 14: interface eth0 declared allow-auto twice
ifup: couldn't read interface file "/etc/network/interfaces [fail] 
```

My IP config doesn't provide me with as much information as yours does...  For instance, I didn't have a DNS server location, just a suffix.  Likewise, my edited interface file did not have this.  I don't know if that has anything to do with why it failed, but I thought I should point that out.

---

### Post by slakkie on 2009-08-04
You have your eth0 defined twice. Remove the duplicate (incorrect?) entry.

Could you post your windows config by any chance?

And with wireless it also works, I have such a setup :)

[http://ubuntuforums.org/showpost.php?p=5752871&postcount=2](http://ubuntuforums.org/showpost.php?p=5752871&postcount=2)

---

### Post by Topher88 on 2009-08-04
> **slakkie said:**
> You have your eth0 defined twice. Remove the duplicate (incorrect?) entry.

Could you post your windows config by any chance?

And with wireless it also works, I have such a setup :)

[http://ubuntuforums.org/showpost.php?p=5752871&postcount=2](http://ubuntuforums.org/showpost.php?p=5752871&postcount=2)

EDIT:  Woops...  Sorry, misunderstanding.  I confused IPconfig with the interfaces file, lol...  But still, my interfaces file mimics your, except with my information and without the DNS-server line.  What duplicate is it talking about???

---

### Post by Topher88 on 2009-08-04
> **cariboo907 said:**
> Are your network devices actually being detected and the drivers loaded? Open an Applications-->Accessories-->Terminal and type

```
sudo lshw -C network > network.txt
```The above command creates a text file called network.txt which will print a listing of your network devices, copy network.txt to your Windows partition and paste it in your next post.

```
*-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:25:56:5c:58:14
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:d8:5c:c7
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=139.78.114.227 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:88:2e:90:e6:c8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by slakkie on 2009-08-04
> **Topher88 said:**
> EDIT:  Woops...  Sorry, misunderstanding.  I confused IPconfig with the interfaces file, lol...  But still, my interfaces file mimics your, except with my information and without the DNS-server line.  What duplicate is it talking about???

You have two auto eth0 statements defined in your interfaces file.

```
grep auto /etc/network/interfaces
``` should return 1 auto eth0 entry.

---

### Post by Topher88 on 2009-08-04
nvm

---

### Post by Topher88 on 2009-08-04
> **slakkie said:**
> You have two auto eth0 statements defined in your interfaces file.

```
grep auto /etc/network/interfaces
``` should return 1 auto eth0 entry.

Huh...  Yeah, it returns "auto lo" once and "auto eth0" twice.

So what do I need to do?  I have no idea where the duplicate is or how it got there...  lol.

Edit: scratch that; found it.  There is a interfaces.save file, for some reason...  *sigh* again, I'm a n00b.  How do I delete it?

---

### Post by Topher88 on 2009-08-04
Okay, so I'm stupid...  I think i see what the problem is.

Sorry for my complete lack of knowledge of anything that's going on here and my apparent disregard for actually reading what you're saying - this is frustrating and I'm not thinking straight.  Hopefully you haven't face/palmed too much because of me...  lol.

---

### Post by Topher88 on 2009-08-04
Success!  I finally got it right, lol.  What I did was when I copied everything into the interfaces file, I didn't realize that the Static and DHCP were supposed to be one or the other, not both.  So upon removing the Static lines, I am now able to connect to the internet.  Thanks!  And sorry for my stupidity, lol.

---

### Post by slakkie on 2009-08-04
No problem and good to see you are connected!

I didn't see your stupidity until after you fixed it. I was busy with getting to know my new cat. No face palms here :)

---

