---
title: "All network laptop Ubuntu 9.04 gone.  Need help real bad"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by Jazmac on 2009-07-19
I don't really understand what happened or how all my network drivers vanished but being a noob with Ubuntu,  don't have much of a clue of how to fix this.  With Windows, it's a no brainer of my options but Ubuntu is a challenge for me.  Anyway, this is what my network drivers look like currently.  I hope somebody can help get back online tonight...if not sooner.

>                                   aliensix@ubuntu:~$ sudo lshw -C network 
   *-network                
        description: Ethernet interface  
        product: 88E8038 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 14  
        serial: 00:e0:b8:d4:61:b1  
        size: 100MB/s  
        capacity: 100MB/s  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation  
        configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.2.75 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s  
   *-network:0 DISABLED  
        description: Wireless interface  
        physical id: 2  
        logical name: wlan0  
        serial: 00:c0:a8:f0:ed:6c  
        capabilities: ethernet physical wireless  
        configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg  
   *-network:1 DISABLED  
        description: Ethernet interface  
        physical id: 3  
        logical name: pan0  
        serial: fe:33:87:3b:f1:0c  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes  
 aliensix@ubuntu:~$  
 -Jazmac

---

### Post by pytheas22 on 2009-07-19
According to the output you posted, it looks like you actually are connected on the (ethernet) wired interface, since you have an IP address.  It would be helpful if you could provide a more specific description of what you're unable to do.  Can you not load web pages?  If you right-click on the NetworkManager icon in the upper-right portion of your screen, is networking enabled?

As for the wireless, my first guess is that it's disabled via a switch--either a physical button on the outside of your computer, or a software toggle, like function+F2.  Make sure it's enabled.  If that doesn't help, please post the output of:
```

lspci -nn
dmesg | grep -ie eth -e wlan -e radio
```

---

### Post by Jazmac on 2009-07-20
> **pytheas22 said:**
> According to the output you posted, it looks like you actually are connected on the (ethernet) wired interface, since you have an IP address.  It would be helpful if you could provide a more specific description of what you're unable to do.  Can you not load web pages?  If you right-click on the NetworkManager icon in the upper-right portion of your screen, is networking enabled?

As for the wireless, my first guess is that it's disabled via a switch--either a physical button on the outside of your computer, or a software toggle, like function+F2.  Make sure it's enabled.  If that doesn't help, please post the output of:
```

lspci -nn
dmesg | grep -ie eth -e wlan -e radio
```

The ip address I set in there manually but generally I do DHCP.  I found a link somewhere about setting an ip address and using it to get to the net.  Well, I could not get to the net with this.  I could not ping the router.  As far as the Network Manager goes, there used to be one on there but it no longer is.  I have no idea how it vanished.

On another note, and understand I'm a noob but how are you reading I'm connected from those results again?  

I'm reading both Network 0 and 1 are disabled.  Does Ubuntu disabled and what Windows call disabled different?

-Jazmac

---

### Post by Jazmac on 2009-07-20
aliensix@ubuntu:~$ dmesg | grep -ie eth -e wlan -e radio
[    1.362741] Driver 'sd' needs updating - please use bus_type methods
[    1.362751] Driver 'sr' needs updating - please use bus_type methods
[    2.279060] sky2 0000:02:00.0: Marvell Yukon 88E8038 Fast Ethernet Controller
[    2.284056] sky2 eth0: addr 00:e0:b8:d4:61:b1
[   17.834264] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.471694] sky2 eth0: enabling interface
[   23.472216] ADDRCONF(NETDEV_UP): eth0: link is not ready
aliensix@ubuntu:~$ 

I could not get that other command to work.  Unless the  -nn supposed to be replaced by some number, sudo that as you wrote it, produced a command not found.

-JazMac

---

### Post by Jazmac on 2009-07-20
Any ideas or is this problem a fairly unique one?

-JazMac

---

### Post by jamest09 on 2009-07-20
Post the output of ifconfig

---

### Post by pytheas22 on 2009-07-20
> The ip address I set in there manually but generally I do DHCP. I found a link somewhere about setting an ip address and using it to get to the net. Well, I could not get to the net with this. I could not ping the router. As far as the Network Manager goes, there used to be one on there but it no longer is. I have no idea how it vanished.

It's strange that NetworkManager disappeared.  I imagine you've tried rebooting to no effect?  You can try running this command to manually restart NetworkManager:
```

sudo /etc/init.d/NetworkManager restart
```

Does that make any difference?  If not, you can try running these commands to connect on the wired interface (provided it's plugged in, obviously) without NetworkManager:
```

sudo mv /etc/network/interfaces /etc/network/interfaces-old
sudo /etc/init.d/networking restart
sudo ifconfig eth0 up
sudo dhclient eth0
```

This should connect you via dhcp.  If it fails, please post all the output so I can take a look.

> 
On another note, and understand I'm a noob but how are you reading I'm connected from those results again?

I'm reading both Network 0 and 1 are disabled. Does Ubuntu disabled and what Windows call disabled different?

The fact that you had an IP address on the wired interface made me think you were connected.  But if you set a static IP by hand, that doesn't mean as much.

As for the disabled message, only your wireless interface ("-network:0") is disabled.  The other interface marked as disabled ("-network:1") is not a real network card; it's just a virtual loopback interface used by the system for internal traffic and is always marked as disabled.

Usually when the wireless interface is disabled, it means the wireless is switched off via a switch, as I mentioned in my first post.  There are other possible explanations as well, like missing firmware, but my first guess would be that you simply turned the device off.  If you have any buttons or software switches for toggling the wireless on and off, please make sure they're set to on, then try again.

> I could not get that other command to work. Unless the -nn supposed to be replaced by some number, sudo that as you wrote it, produced a command not found.


Maybe you typed *1spci -nn* rather than *lspci -nn*?  Note that the first letter should be lowercase L, not the number 1.  Please try this again; it should definitely work unless something is seriously wrong with your machine.

---

