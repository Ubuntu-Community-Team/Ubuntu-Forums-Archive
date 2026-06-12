---
title: "Very odd internet connection problem"
date: 2013-01-15
forum: Networking &amp; Wireless
---

### Post by randytuggle on 2013-01-15
I have a problem with my internet connection. No matter whether I use wired or wireless, I cannot login to msn.com. Also, I have frequent connection drops using Chromium. Does anyone know a fix for this? I use Comcast and everything works fine on other OS's around the house. I've tried resetting to router and nothing helps. I can't even pull up msn.com the majority of the time.

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> I have a problem with my internet connection. No matter whether I use wired or wireless, I cannot login to msn.com. Also, I have frequent connection drops using Chromium. Does anyone know a fix for this? I use Comcast and everything works fine on other OS's around the house. I've tried resetting to router and nothing helps. I can't even pull up msn.com the majority of the time.

Are your issues only with msn.com or with every other website?  Since MSN is part of Microsoft, I'd expect they would prefer people to use Internet Explorer when visiting that website. Perhaps they do not test with other browsers on other OSes as much?

I just visited msn.com and the page loaded fine under firefox even with javascript blocked.  I've never had any Microsoft account (never intend to have one), so I can't check the login. Clicking to that login page did appear to have some complex javascript. The more complex the js, to more likely that it isn't cross-browser.

It is possible to run IE8 under WINE, however, WINE is also a good way to get Windows viruses.

Could you explain the exact steps and results for each step so that someone might be able to reproduce the issue on MSN?

If this is an issue with every website, we need to know that too. That would be very important information. Please, only use the wired connection until we get this sorted.  We'll need to know:
* which OS
* network card data - chipset from **lshw**
* contents of** /etc/network/interfaces**
* contents of** /etc/resolv.conf**
* output from **ifconfig**
* vendor/model of  modem
* vendor/model of router

It could be that your DNS is having issues and that the internet is actually just fine. To most people, when DNS is unavailable, the internet seems completely broken, though it is just fine.

---

### Post by randytuggle on 2013-01-15
My ethernet card doesn't work well because the cable clip falls out of the card, but here is the output from running lshw.  Below this you'll see the contents from /etc/network/interfaces, etc/resolv.conf, ifconfig. I have an xfinity router but no phone service to it.

        
    description: Computer
    width: 64 bits
    capabilities: vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1993MiB
     *-cpu:0
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr
     *-cpu:1
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@1
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc pebs bts nopl pni dtes64 monitor ds_cpl est cid cx16 xtpr
     *-pci
          description: Host bridge
          product: 82945G/GZ/P/PL Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 memory:efd00000-efdfffff
        *-display:0
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:eff00000-eff7ffff ioport:ecd8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
             resources: memory:eff80000-efffffff
        *-multimedia
             description: Audio device
             product: NM10/ICH7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:42 memory:efebc000-efebffff
        *-pci:1
             description: PCI bridge
             product: NM10/ICH7 Family PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:1000(size=4096) memory:efc00000-efcfffff ioport:80000000(size=2097152)
        *-usb:0
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:ff80(size=32)
        *-usb:1
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:22 ioport:ff60(size=32)
        *-usb:2
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:ff40(size=32)
        *-usb:3
             description: USB controller
             product: NM10/ICH7 Family USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1d.3
             bus info: pci@0000:00:1d.3
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:23 ioport:ff20(size=32)
        *-usb:4
             description: USB controller
             product: NM10/ICH7 Family USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:21 memory:ffa80800-ffa80bff
        *-pci:2
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: e1
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:d000(size=4096) memory:efb00000-efbfffff
           *-network
                description: Ethernet interface
                product: NM10/ICH7 Family LAN Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@0000:03:08.0
                logical name: eth0
                version: 01
                serial: 00:13:72:e2:e9:7c
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
                resources: irq:20 memory:efbff000-efbfffff ioport:dcc0(size=64)
        *-isa
             description: ISA bridge
             product: 82801GB/GR (ICH7 Family) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide:0
             description: IDE interface
             product: 82801G (ICH7 Family) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ffa0(size=16)
        *-ide:1
             description: IDE interface
             product: NM10/ICH7 Family SATA Controller [IDE mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=ata_piix latency=0
             resources: irq:20 ioport:fe00(size=8) ioport:fe10(size=4) ioport:fe20(size=8) ioport:fe30(size=4) ioport:fea0(size=16) memory:80200000-802003ff
        *-serial UNCLAIMED
             description: SMBus
             product: NM10/ICH7 Family SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 01
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:ece0(size=32)
     *-scsi
          physical id: 3
          logical name: scsi0
          capabilities: emulated
        *-cdrom
             description: DVD writer
             product: DVD+-RW GSA-H21N
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             version: A105
             serial: [
             capabilities: removable audio cd-r cd-rw dvd dvd-r
             configuration: ansiversion=5 status=nodisc
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: 08:86:3b:fb:76:29
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=10.0.0.4 multicast=yes wireless=IEEE 802.11bgn


from interfaces:

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf:

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.pa.comcast.net

ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:13:72:e2:e9:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2803 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:295302 (295.3 KB)  TX bytes:295302 (295.3 KB)

wlan0     Link encap:Ethernet  HWaddr 08:86:3b:fb:76:29  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a86:3bff:fefb:7629/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:307770 errors:0 dropped:38129 overruns:0 frame:0
          TX packets:217453 errors:0 dropped:2 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123617279 (123.6 MB)  TX bytes:24112810 (24.1 MB)

---

### Post by randytuggle on 2013-01-15
I'm using Lubuntu 12.10 64 bit. This only happens with msn.com -- and I don't even use it that much with the exception of viewing news and checking hotmail. Weird thing is, hotmail works. I do notice intermittent connectivity problems when clicking on links.

---

### Post by TheFu on 2013-01-15
Ok, so it appears you are using wifi, not wired ethernet.

It appears that **the DNS server** is screwed up. You need to fix that by manually setting it.  I don't know how to accomplish that for wifi connections, but for wired connections, you specify the DNS servers in the /etc/network/interfaces file.  Using DHCP makes it easier when everything works, but not easier to troubleshoot, IMHO.


So, if you can plug in the box with an ethernet cable and edit the /etc/network/interfaces file to add these lines:
-----------------------------
auto eth0
iface eth0 inet dhcp
# Force google DNS servers
  dns-nameservers 8.8.8.8
---------------------------
I think it will work fine.  You might want to use a different DNS service or even use the one from Comcast. Usually you want to have 2 DNS providers so that if 1 is failing (like you are seeing today), then the other will still work.  It is hard to choose one when nothing works. I just happen to have the google DNS memorized, though I wouldn't recommend it to any who cares about their privacy. I'd use it just long enough to find a different DNS provider.

If you can find the setting for your wifi network connection, then you can enter the 8.8.8.8 IP address there. It will work the same.

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> I'm using Lubuntu 12.10 64 bit. This only happens with msn.com -- and I don't even use it that much with the exception of viewing news and checking hotmail. Weird thing is, hotmail works. I do notice intermittent connectivity problems when clicking on links.

I use LXDE on 12.04 myself.  12.10 is too new for me. I prefer LTS releases when I need something that will **just work.**  I do not use wifi connections unless absolutely required.  None of the machines I can get to have wifi cards, so I can't look up the wifi-specific commands. Sorry.

I'd be surprised if hotmail works. You don't appear to have a valid DNS service provider inside the network settings.  Why are you using Microsoft-centric services in Ubuntu?  msn, hotmail .... I'm curious.

---

### Post by randytuggle on 2013-01-15
I changed the interfaces file but after a reboot, still no good. I don't even need msn really. I just use it as a news site from time to time. I just hate when things don't work as they should.

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> I changed the interfaces file but after a reboot, still no good. I don't even need msn really. I just use it as a news site from time to time. I just hate when things don't work as they should.

What does /etc/resolv.conf say?  If it doesn't have an IP address on the internet, then it isn't working.  If there is an IP address inside it, then you can check if you can "ping" it.

```
ping 8.8.8.8
```

If that works, then you are actually on the internet, and it is just the DNS that isn't working.

**If you are not using the wired ethernet connection, the settings inside the **interfaces **file do not matter.** It doesn't work for wifi - or at least it may not work for wifi. I don't know since the wpa* commands were all introduced a few yrs ago.

Having both wired ethernet AND wifi working at the same time is a bad idea. Disable wifi when using wired or
disable wired when using wifi.  **Don't allow both.**

Finally, no need to reboot.  run
```
sudo service networking restart
```
to restart all networking on the machine. The only time a reboot is necessary is when the physical hardware changes or you use the BIOS to enable/disable hardware (sometimes).  I'd always try the restart command first before rebooting.

---

### Post by randytuggle on 2013-01-15
resolv.conf shows 8.8.8.8 and when I ping it, it works fine. I'm using wired ethernet without any wi-fi, too. I tried the network reboot method you suggested, and nothing helps. This is really odd.

---

### Post by Grenage on 2013-01-15
Is there a reason you're using resolve.conf, rather than the Network Connections GUI?

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> resolv.conf shows 8.8.8.8 and when I ping it, it works fine. I'm using wired ethernet without any wi-fi, too. I tried the network reboot method you suggested, and nothing helps. This is really odd.

Ok, let's summarize.  Please correct anything you think that I have wrong:
* wired ethernet - eth0 is the device
* you can ping 8.8.8.8 - the google DNS
* /etc/resolv.conf is automatically generated and has 8.8.8.8
* you can ping it.
* you have disabled wifi - check the **ifconfig **output (post it would be good)

There are DNS commands that will query the DNS server.  
* dig google.com
* host google.com
Do those work?
Can you use Chromium to visit those web pages?

Try those commands with msn.com and hotmail.com. Do they work?

Look inside your /etc/hosts and /etc/nsswitch.conf files (please post them). Both should be tiny - 20 lines or less.  

/etc/nsswitch.conf should have lines like this:
```
hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files
```

I'd post my /etc/hosts file, but it is huge. Here's an article on Lifehacker that I wrote about this: [http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file](http://lifehacker.com/5817447/how-to-block-unwanted-ads-in-all-applications-and-speed-up-web-browsing-with-the-hosts-file)

Yours probably looks something like this:
```
127.0.0.1 localhost
127.0.1.1 lubuntu

# The following lines are desirable for IPv6 capable hosts
# ::1 ip6-localhost ip6-loopback
# fe00::0 ip6-localnet
# ff00::0 ip6-mcastprefix
# ff02::1 ip6-allnodes
# ff02::2 ip6-allrouters
# ff02::3 ip6-allhosts
```

---

### Post by TheFu on 2013-01-15
> **Grenage said:**
> Is there a reason you're using resolve.conf, rather than the Network Connections GUI?

Lubuntu - the key thing is not to edit /etc/resolv.conf in 12.04 and later. It is a generated file from the resolvconf tool.  I can see where this is great for GUI users, but it sucks for me personally and for people running servers without a GUI. 

I looked in my LXDE menus ... don't see anything related to networking available there.  What is the **actual program name** we can run? there is nothing that starts with netw* on the machine.

---

### Post by randytuggle on 2013-01-15
You have everything correct so far. My ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:13:72:e2:e9:7c  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fee2:e97c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22549474 (22.5 MB)  TX bytes:5949624 (5.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8242 (8.2 KB)  TX bytes:8242 (8.2 KB)

I can successfully run dig and host on google.com but msn.com brings up no ip info as google did. I can load google in chromium, but cannot load msn.com

I don't have files for etc/hosts or nsswitch.conf.. odd.

---

### Post by Grenage on 2013-01-15
> **TheFu said:**
> Lubuntu - the key thing is not to edit /etc/resolv.conf in 12.04 and later. It is a generated file from the resolvconf tool.  I can see where this is great for GUI users, but it sucks for me personally and for people running servers without a GUI. 

I looked in my LXDE menus ... don't see anything related to networking available there.  What is the **actual program name** we can run? there is nothing that starts with netw* on the machine.

Ah cheers; I had missed the Lubuntu flag on the post.

---

### Post by jdthood on 2013-01-15
> **TheFu said:**
> Lubuntu - the key thing is not to edit /etc/resolv.conf in 12.04 and later. It is a generated file from the resolvconf tool. I can see where this is great for GUI users, but it sucks for me personally and for people running servers without a GUI.

Resolvconf does not depend on a GUI. 

Resolvconf is new, so some server admins don't know yet how to configure it. It's not too hard. If an interface is configured via DHCP you don't have to do anything extra. For static configuration of an interface using ifup you have to add a "dns-nameservers" option to the relevant stanza in /etc/network/interfaces. See resolvconf(8) and the following blog posting.

    [https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> I can successfully run dig and host on google.com but msn.com brings up no ip info as google did. I can load google in chromium, but cannot load msn.com

I don't have files for etc/hosts or nsswitch.conf.. odd.

msn.com not being resolved with either of those commands, yet  other websites are working, probably means they are under some sort of  attack or that China or Pakistan pushed a bad routing table again and  stole all their IP addresses ... again.

Did you find a different set of DNS servers to use?  I never asked where you were - I assume in the USA since Comcast.  There are DNS performance tools available which will help you locate the fastest DNS for your specific location. Just be certain that you trust completely the DNS provider who you select. DNS is the basis of all trust on the internet. HTTPS can easily be broken with a less-than-honest DNS provider involved.

If you were running MS-Windows, I'd strongly suspect your machine had been hacked and you had a rootkit, viruses, and all sorts of other nasties on it.** DNS is the backbone of internet trust.**

Everyone should have an /etc/hosts file and /etc/nsswitch.conf file.

At this point, I think you want to force a reinstall of the networking stuff on your box.  Sadly, I don't know the name of the package - I'd guess **netbase** and **net-tools**.

```
sudo apt-get --reinstall install net-tools  netbase
```
is my guess. **I don't know if this is a good idea or not.**  The /etc/network/interfaces file should be reworked after this.  I'd have a great backup and expect a 20% chance that reinstalling the OS might be necessary - before running that command. Everything will probably be fine, but ....

---

### Post by TheFu on 2013-01-15
> **jdthood said:**
> Resolvconf does not depend on a GUI. 

Resolvconf is new, so some server admins don't know yet how to configure it. It's not too hard. If an interface is configured via DHCP you don't have to do anything extra. For static configuration of an interface using ifup you have to add a "dns-nameservers" option to the relevant stanza in /etc/network/interfaces. See resolvconf(8) and the following blog posting.

    [https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/](https://www.stgraber.org/2012/02/24/dns-in-ubuntu-12-04/)
[B]
This is true, but when you've been adding [/B]nameservers** and **search **to the** /etc/resolv.conf** file with scripts for 20+ years and it stopped working with 12.04,** THAT does** suck.** It took me some time to find a solution and another day to update AND test the automatic tools which manage these files across our infrastructure. I had better things to do that day.  Plus, there isn't any added functionality for servers (static IPs) provided that I can see, besides another level of indirection.

The text file method was working just fine for servers.  The resolvconf devs should have made that tool backwards compatible, IMHO.  Change for the sake of change seems foolish.  I'm just sayin'.  </rant>  Sorry for that. I do feel better now. ;)

I'm not saying that it isn't an improvement for GUI users on DHCP. It definitely seems to be for them.

It would be extremely helpful if the default /etc/network/interfaces file actually contained an example for static IP configuration - all commented out. THAT would be useful with the** dns-nameservers **listed and would help people transition quicker. Everyone is a critic, including me.

---

### Post by randytuggle on 2013-01-15
I think I'll just let this go rather than do a potential reinstall. This has been an issue on previous installations as well.

---

### Post by TheFu on 2013-01-15
> **randytuggle said:**
> I think I'll just let this go rather than do a potential reinstall. This has been an issue on previous installations as well.

Really?  That is good to know. Perhaps your cable modem or router are failing?
I've had a comcast modem fail a few times. If the modem partially fails, getting the DHCP address and extra parameters ... like the DNS servers to use .... can break too.

---

### Post by randytuggle on 2013-01-15
I'll blame comcast. LOL!

---

### Post by jdthood on 2013-01-15
> **TheFu said:**
> [B]
This is true, but when you've been adding [/B]nameservers** and **search **to the** /etc/resolv.conf** file with scripts for 20+ years and it stopped working with 12.04,** THAT does** suck.** It took me some time to find a solution and another day to update AND test the automatic tools which manage these files across our infrastructure. I had better things to do that day.  Plus, there isn't any added functionality for servers (static IPs) provided that I can see, besides another level of indirection.

Even with resolvconf installed you can run with a static file at /etc/resolv.conf, so all you had to do if you wanted to continue using your custom scripts was answer No to the "linkify" question or, after upgrade, delete the symbolic link at /etc/resolv.conf.

A minor advantage of resolvconf even for a server is that nameserver addresses are associated with the interfaces over which they are accessible, which is clearer.

> The text file method was working just fine for servers.  The resolvconf devs should have made that tool backwards compatible

The package is designed not to break name service on upgrade on machines that have static resolv.conf. I can imagine that machines whose resolv.conf is managed by custom scripts have problems on upgrade. Supporting such machines would have required enhancing glibc so that it could be configured to read another file than /etc/resolv.conf. This would have been a lot of work and would just have made other people unhappy.

> Change for the sake of change seems foolish.  I'm just sayin'.  </rant>  Sorry for that. I do feel better now. ;)

Changes like that aren't made for no good reason. Prior to resolvconf, all sorts of programs fiddled with /etc/resolv.conf, none of them preserving one another's changes. Resolvconf imposes order on all that.

> I'm not saying that it isn't an improvement for GUI users on DHCP. It definitely seems to be for them.

It would be extremely helpful if the default /etc/network/interfaces file actually contained an example for static IP configuration - all commented out.

It does, on a fresh install.

---

### Post by jdthood on 2013-01-15
> **randytuggle said:**
> 
from interfaces:
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
resolv.conf:
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search hsd1.pa.comcast.net

```


That you had "nameserver 127.0.1.1" in /etc/resolv.conf indicates that you were using NetworkManager and its forwarding nameserver dnsmasq. Dnsmasq has known bugs.

   [https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842](https://bugs.launchpad.net/ubuntu/+source/dnsmasq/+bug/1003842)

Best to disable it. Comment out "dns=dnsmasq" in /etc/NetworkManager/NetworkManager.conf and then reboot.

> **randytuggle said:**
> resolv.conf shows 8.8.8.8 and when I ping it, it works fine. I'm using wired ethernet without any wi-fi, too. I tried the network reboot method you suggested, and nothing helps. This is really odd.

You later set your nameserver address to 8.8.8.8. The correct way to do this when you are using resolvconf and NetworkManager is to open the Connection Editor and set Method to "Automatic (DHCP) addresses only" and add the desired address (in this case, 8.8.8.8) to the "Additional DNS servers" field.

If you are using ifup to configure the interface in question rather than NetworkManager then you put a "dns-nameservers" option in /etc/network/interfaces as has been mentioned earlier.

Either way, make sure that /etc/resolv.conf is a symbolic link pointing to ../run/resolvconf/resolv.conf. Unless you've decided to run with a static resolv.conf file, that is.

---

### Post by TheFu on 2013-01-15
> **jdthood said:**
> 
It does, on a fresh install.

**Thank you very much** for the detailed response.  My network needs have always been fairly simple with no more than 4 interfaces involved and stacked DNS providers, so having a different provider for a different interface never occurred to me.  **THAT is slick!**

Please keep fighting the good fight to make it better for idiots like myself even when we seem unappreciative!

---

### Post by jdthood on 2013-01-16
> **TheFu said:**
> **having a different provider for a different interface never occurred to me.  [B]THAT is slick!**

It sounds as if you may have misinterpreted what I said. Resolvconf can't cause the glibc resolver to use different nameservers for different network interfaces. The glibc resolver always uses the same nameserver list for all interfaces. What resolvconf does is: it allows, for each interface, nameserver address information to be included with other information relevant to that interface (gateway address, etc.)

Whereas the glibc resolver can't select a different nameserver per interface, the dnsmasq forwarding nameserver can select an upstream nameserver depending on the domain to be looked up. This is the most important feature for the sake of which dnsmasq (controlled by NetworkManager) was introduced to the default Desktop installation in 12.04.

---

### Post by TheFu on 2013-01-16
> **jdthood said:**
> It sounds as if you may have misinterpreted what I said. Resolvconf can't cause the glibc resolver to use different nameservers for different network interfaces. The glibc resolver always uses the same nameserver list for all interfaces. What resolvconf does is: it allows, for each interface, nameserver address information to be included with other information relevant to that interface (gateway address, etc.)

Whereas the glibc resolver can't select a different nameserver per interface, the dnsmasq forwarding nameserver can select an upstream nameserver depending on the domain to be looked up. This is the most important feature for the sake of which dnsmasq (controlled by NetworkManager) was introduced to the default Desktop installation in 12.04.

I must still misunderstand 'cause DNS works by letting different nameservers respond to different domains as the authoritative answer, otherwise we'd all have local hosts files like in the beginning.

Well, we should probably not take over this thread and I should probably read up on resolveconf more before asking anymore questions. ;) Thanks for trying.

---

