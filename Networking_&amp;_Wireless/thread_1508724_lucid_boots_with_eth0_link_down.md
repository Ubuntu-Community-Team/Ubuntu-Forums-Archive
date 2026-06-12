---
title: "lucid boots with eth0 link down"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by msewing on 2010-06-13
System: Core i7/920, 6GB,  2.6.32-22-generic (same result with 32-21).

Recently (can't say if correlated with a specific update) -- Lucid is booting with the following in dmesg:

> kernel: [    3.075281] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
kernel: [    3.075295] r8169 0000:08:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
kernel: [    3.075705] eth0: RTL8168d/8111d at 0xffffc90000c62000, 00:24:1d:70:e7:ea, XID 081000c0 IRQ 32
kernel: [   78.983686] r8169: eth0: link down
kernel: [   78.984642] ADDRCONF(NETDEV_UP): eth0: link is not ready

If use the Network Manager to disable networking, wait, then enable networking, I usually (maybe not always) get eth0 to come up.

lspci:
> 08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

ifconfig eth0 (when working!)
> eth0      Link encap:Ethernet  HWaddr 00:24:1d:70:e7:ea  
          inet addr:192.168.1.143  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe70:e7ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:7200  Metric:1
          RX packets:3125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2879 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2753869 (2.7 MB)  TX bytes:624042 (624.0 KB)
          Interrupt:32 Base address:0xe000 

/etc/network/interfaces:
> auto lo
iface lo inet loopback

/etc/NetworkManager/nm-system-settings.conf:
> [main]
plugins=ifupdown,keyfile

no-auto-default=00:24:1d:70:e7:ea,

[ifupdown]
managed=false

NB: I have occasionally been experimenting with the RT kernel (2.6.31-10-rt).  Could that have affected my 2.6.32-22-generic boot?  If so, what's the best way to restore the correct boot behavior?

Any ideas?  
TIA
Martin

---

### Post by purelinuxuser on 2010-06-13
Hmm... you could manually bring up eth0 on boot by adding
```
ifconfig eth0 up
```
to the end of /etc/rc.local .

More of a workaround than a fix though :(

---

### Post by bigmojo74 on 2010-06-13
Had the same thing going on with mine after staticly configuring my IP information - 

But if that's all that's in your /etc/network/interfaces that's why it's not up when you boot it needs to be told to be on at boot (auto.) Below is abit from my setups, not knowing your configuration I can only guess.

First few lines of static config from one of my servers
> #Primary Network Interface
auto eth0 
iface eth0 inet static
address 192.168.2.112
....First few lines from my desktop, set for DHCP for a server you probably want to remove that # on the second line.
> # The primary network interface
auto eth0
#iface eth0 inet dhcp


---

### Post by msewing on 2010-06-13
> **bigmojo74 said:**
> 
First few lines of static config from one of my servers
First few lines from my desktop, set for DHCP for a server you probably want to remove that # on the second line.

Yes, but network-manager is supposed to handle the configuration, no?  Anyway, it has been booting fine without any explicit setup in /etc/network/interfaces until now.

Workarounds might work (as does manual disable/enable), but I'd like to get it to work "right".

---

### Post by gsgleason on 2010-06-13
System > Preferences > Network Connections

Do you have anything under 'wired connections?'  If so , edit and see if there is anything obvious to change.

---

### Post by bigmojo74 on 2010-06-13
Truth be told, I'm not familiar with network-manager and a quick man of it is useless. Are you wanting to do this through the GUI utility? If not ignore this, if so right click the icon in the upper right corner and select Edit Connections, then select your connection of choice, edit, and make sure that Connect Automatically is checked.

I'm not sure I consider editing the network configuration file a work around though, since if you're running without a GUI there is no networkmanager (atleast not on my LL base installs.) But after inspecting my own, it's probably best if you plan on using networkmanager to handle changes there.

---

### Post by msewing on 2010-06-13
I have network-manager set up "normally" ie. one "wired" connection with a MAC address and MTU (7200 - this is a gigabit port).  IPv4 for automatic (DHCP).  I tried it with a manual IP - no difference.  The "connect automatically" box is checked.

This is a desktop workstation, and I'd like to keep it working with the normal (by now) network manager system.

---

### Post by bigmojo74 on 2010-06-13
The only other thing that readily comes to mind is if the port is having issues autonegotiating with whatever networking equipment you have setup. On a limb I'll assume it's likely home networking gear (not Cisco/Juniper/other commercial equipment.) I don't see anywhere in Network Manager to check your duplex let alone set it. 

See the section about ethtool:
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

Otherwise, best of luck.

*Edit: Yes that's a link to Ubuntu Server, but essentially the only difference between a server and a workstation is a server shares/provides a service on the network. Before I setup a static IP for my system (yesterday) the connection was always on at startup out of the box - and the lines from it's /etc/network/interfaces are pasted above prior to my editing them. Not sure why you don't have anything referencing eth0 or how to get it created through networkmanager.

---

### Post by msewing on 2010-06-14
Lots of confusing results, ending in total (?) victory...

Deleted / added new "Wired" network connection in network-manager
Saw network coming up 10 mbs/half (ethtool).  Progress?

Got weird varying results with motherboard's Ethernet self-test feature.  Wiggling cables, changing switch ports did not help.

Finally cured (?) by total power off (including master switch at rear of power supply), count to 10, and power on.  Sanity has returned.  I guess there's a moral there.

Still, my nfs drive is not connecting at boot time correctly.  There's always something...

Thanks to all who helped work this through with me!

Martin

---

### Post by charlesall on 2011-12-01
Thanks, the total power down also helped for me. Incidentally the problem was caused by our power tripping.

---

