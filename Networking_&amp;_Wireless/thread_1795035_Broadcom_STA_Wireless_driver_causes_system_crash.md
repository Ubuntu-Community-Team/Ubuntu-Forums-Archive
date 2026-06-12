---
title: "Broadcom STA Wireless driver causes system crash"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by NGunslinger on 2011-07-01
I just sent the following email to Broadcom (linux-wlan-client-support-list@broadcom.com). I'll post an update if I receive a response.
-----------------------------------------------------------------
The current Linux STA 802.11 driver causes my system to crash. I've verified this under Ubuntu 11.04 and Linux Mint 11 (an ubuntu derivative). Oddly enough, everything worked find under Ubuntu 10.10. My chipset is the 4321, my CPU is an AMD Phenom II 920, and the motherboard is an ASUS M3A78-EM. I tried the STA driver that ships with Ubuntu as well as compiling the one at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php), including the patch for kernel versions > 2.6.37.

I am confident that the linux driver is the problem. If I connect my machine to my router using an ethernet cable, everything works fine. Also, the wifi adapter works fine under Windows. The symptoms are that the wifi adapter appears to connect to my network correctly and works fine for short transfers. But when I try a larger transfer, such as a speed test or streaming an mp3, one of three things happens after about 5 to 10 seconds:

1) The screen remains in graphics mode but locks up, including the mouse pointer. No keyboard input has any effect.

2) The screen goes into text mode and repeats the following over and over: [435.610002] ehci_hcd 0000:00:13.2:PCI-DMA:Out of IOMMU space for 18 bytes.

3) The screen goes into text mode and prints what appear to be CPU register contents. I took a picture of this with my phone if it will help, but obviously the text is kind of hard to make out.

Any help you can give is appreciated.

---

### Post by Sin@Sin-Sacrifice on 2011-09-03
I actually have a bug report open for this at [the kernel bugzilla]("https://bugzilla.kernel.org/show_bug.cgi?id=39272"). I was actually on Gentoo 11 when I found this and thought it might have been something I did so I switched back to Ubuntu and same thing. Only happens on kernels > 2.6.36. Might make them take it more seriously if you confirmed on the bug report.

---

### Post by praseodym on 2011-09-03
Hi,

which chipset works inside the 4321? It can be two different:

14e4:4321  which may work from kernel 2.6.39 with b32
14e4:4328  which only works imho with the STA-driver so far.

You can try for both chipsets a mainline kernel from 2.6.39 on, see [here]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices")

If you installed the "linux-wireless" drivers from the backported modules you _have to_ uninstall them first, reinstall the kernel and STA-driver, because the **lib80211** subsystem drivers dont work with the STA.

Mainlinekernel-archive: [Klick]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")

I would prefer [2.6.39-4]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39.4-oneiric/"). You need all three possible packages for 32 or 64 bit.

Check with:

```
lspci -nnk | grep -iA2 net
```

---

### Post by NGunslinger on 2011-09-03
@Sin - I'd love to confirm your bug report but the link you provided appears to be broken.

@praseodym - I appreciate your help but what you're describing sounds like it's beyond my abilities, especially the bit about reinstalling the kernel. I've been using Ubuntu for several years and have gotten used to using these forums to resolve previously documented problems, but I'm no Linux expert. In all honesty I'm more inclined to research and buy a new wifi adapter that I know will work than spending a lot more time troubleshooting this.

---

### Post by northd_tech on 2011-09-03
FWIW, my Broadcom "4328" wireless is and has been pretty 'bulletproof' using the STA driver under 64-bit Ubuntu 10.04.3 LTS (as in Long Term Support)- the LTS kernels see much more/better testing and much fewer changes as I understand it.

My current wireless setup is as follows:
> **uname -a**
Linux DV9820-laptop **2.6.32-33-generic** #72-Ubuntu SMP Fri Jul 29 21:07:13 UTC 2011 **x86_64** GNU/Linux

**cat /etc/issue**
Ubuntu 10.04.3 LTS \n \l

**lspci -vvnn | egrep 'net|ireless|etwork'**
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
03:00.0 Network controller [0280]: Broadcom Corporation **BCM4328** 802.11a/b/g/n [14e4:**4328] (rev 03)**

**lsmod | egrep 'wl|b43'**
**wl   **                1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,**wl**

**iwconfig**
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:203  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

**ifconfig**
eth0      Link encap:Ethernet  HWaddr *Ethernet MAC address*
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B )
          Interrupt:27 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr *WiFi Mac addresss*
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe13:2412/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1899225 errors:1 dropped:0 overruns:0 frame:228689
          TX packets:1053257 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2633289962 **(2.6 GB)**  TX bytes:86723505 **(86.7 MB)**
          Interrupt:19 

**sudo lshw -C network**
[sudo] password: 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: *Ethernet MAC address*
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:27 memory:f2588000-f2588fff ioport:30f8(size=0B ) memory:f2589c00-f2589cff memory:f2589800-f258980f
  *-network
       description: Wireless interface
       product: **BCM4328 802.11a/b/g/n**
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 03
       serial: *WiFi MAC address*
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=wl0 driverversion=5.60.48.36 **ip=192.168.0.3 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:19 memory:f2200000-f2203fff memory:f2000000-f20fffff(prefetchable)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: *vbox MAC address*
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
As you can see from the above, my Broadcom STA wireless has been connected for 2.6 GigaBytes (since last night sometime without a dropped connection, and I was running several VirtualBox Win98, WinXP, and Win7 "virtual machines" trying to get all the shared folders set up using Samba and Windows Networking by "bridging" my wireless into a virtual "ethernet" card)- that's **not exactly the easiest task** for wireless networking to do IMHO.

If you can live without whatever fancy additional 'whistles & bells' that Ubuntu 11.04 gives you, I'd seriously consider using the Long Term Support 10.04 version of Ubuntu (I've created most of my own wireless problems trying to run monitor mode with the b43 driver instead of the Broadcom proprietary "STA" driver with my "4328"- so I can't really blame that on Ubuntu or Broadcom there).

**Ubuntu 10.04.3 LTS (Lucid Lynx)**
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

If you do need more 'whistles & bells' you might want to look here at Ultimate Edition 2.7 (based upon Ubuntu 10.04 **LTS**) and [COLOR=Red]**DO NOT Upgrade**[/COLOR] it to 11.xx (but you can still run whatever **updates** you want probably [COLOR=Blue]**until 2015 or so**[/COLOR]- but you might need to remove 1 or 2 Ultimate Edition software repositories to make Update Manager happy ):

[http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/](http://ultimateedition.info/ultimate-edition/ultimate-edition-2-7/)

> **Long-term support**

    Our long-term support (LTS) releases are  supported for three years on the desktop and five years on the server.  Perfect for organisations that need more stability for business  deployments. 

   **Stay up-to-date**

   Long-term stability doesn't come at  the expense of progress with Ubuntu. You can be confident that Ubuntu  will always work with the latest software and hardware. **Point releases  are provided for LTS versions to ensure that Ubuntu is compatible with  new technologies. They are released in six-month intervals until the  next full LTS version becomes available**.
    
   &#8220;I was particularly pleased with the LTS release &#8211; this is perfect  for companies in which a stable server environment is paramount.&#8221; Deven  Phillips, Senior Systems Administrator, Metal Sales Manufacturing
 [http://www.ubuntu.com/business/desktop/long-term-support](http://www.ubuntu.com/business/desktop/long-term-support)

Of course, I fell in love with the pretty blue theme of Ultimate Edition 2.8 so I "needed" to hack that theme into my setup (see attached screencap).

[http://www.themelinux.com/](http://www.themelinux.com/)

Just my $0.02 (and several years' experience with various flavors of Ubuntu and Mint now).

---

### Post by praseodym on 2011-09-03
Off topic:

@northd_tech: You are right, Kernel 2.6.38 s***s in terms of wireless. BTW: Those "errors" in "ifconfig" occur if you use the wrong mtu-value. Ask you provider or google for that and put the number instead of "Automatic" into the NM-applet.

Back to topic:

@NGunslinger:

Thats not difficult. Do you have a wired connection? Then copy/paste the following into the terminal:

```
sudo apt-get install --reinstall linux-image-$(uname -r) linux-headers-$(uname -r) dkms patch fakeroot bcmwl-kernel-source
```
You dont see the password entry, dont be disturbed ;-)

This reinstalls everything you need, I dont think that you accidently installed the "backport-modules".

Reboot after that.

---

### Post by Sin@Sin-Sacrifice on 2011-09-18
I fixed my link but it seems bugzilla.kernel.org is down for maintenance right now. I will come back and check to see if the link works again when kernel.org is back up.

---

