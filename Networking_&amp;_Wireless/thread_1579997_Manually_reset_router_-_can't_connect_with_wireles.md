---
title: "Manually reset router - can't connect with wireless"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by unckybob on 2010-09-22
I manually reset my router to defaults. 

Then I changed my router default password, SSID, passphrase, and disabled remote management. I used: 

WPA-PSK [TKIP] + WPA2-PSK [AES] 

security on the router. 

When attempting to connect, I use the "WPA & WPA2 Personal" option. 

This is really strange. I can see the SSID on both my laptops, but I can only connect with one now. 

Can someone please help?

---

### Post by MSPdwalt on 2010-09-22
What version of ubuntu are you running?

Can you post the output of ```
sudo lshw -C network
```Do you get any errors when you try to connect or does it just fail?

---

### Post by bkratz on 2010-09-22
Sometimes there is difficulty in using Ubuntu with mixed mode settings.  I had to go to WPA2 with AES only (not wpa/wpa2, tkip/aes) to reliably connect. Can you set your router to one or the other (but not both) it may help.

---

### Post by unckybob on 2010-09-22
I'm running 10.04. 

# sudo lshw -C network 

  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:7f:11:1d
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k5-NAPI firmware=N/A latency=64 link=no mingnt=255 multicast=yes port=twisted pair
       resources: irq:11 memory:c0220000-c023ffff memory:c0200000-c020ffff ioport:8000(size=64) memory:c0240000-c024ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:19:a0:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
       resources: irq:11 memory:c0210000-c0210fff
 
I don't get any errors. It just keeps pinwheeling. After a while it asks for the passphrase again. 

I tried using the WPA2 with AES only, and then WPA with TKIP only, and neither worked.

---

### Post by MSPdwalt on 2010-09-22
Is the SSID set to broadcast or is it hidden?

Have you gone to the System > Preferences > Network Connections, Wireless Tab and deleted the network and re-added it after changing your security settings?

Also how are you initiating the connection? are you clicking the wireless icon, finding your SSID and connecting that way? or are you adding it manually?

You may also want to try right-clicking on the wireless icon, disabling it, and re-enabling it.  I've found Linux or maybe network manager takes awhile to re-scan networks.

**[COLOR=Red]Don't use the hardware switch[/COLOR]**, I've had horrible luck with those (on my dell if I bump the wifi switch I have to go into the BIOS disable wifi, save, go back in and re-enable it)

---

### Post by MSPdwalt on 2010-09-22
Oh dude, this is a B only card, does that even support WPA?

[http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_LAN_2100_3B_Mini_PCI_Adapter](http://www.thinkwiki.org/wiki/Intel_PRO/Wireless_LAN_2100_3B_Mini_PCI_Adapter)

Nevermind, it does [http://bit.ly/aEPFDC](http://bit.ly/aEPFDC)

---

### Post by unckybob on 2010-09-22
Thanks for getting back to me again. 

I'll try to answer all your questions succinctly. 

The SSID is set to broadcast. 

I tried deleting the SSID from the Wireless tab, changing my security settings on the router, and then trying to connect again through the wireless icon on the top panel and using the changed SSID. No go. 

I've used the wireless icon to find all my SSIDs to connect to them. I also tried adding them manually. Both ways, no go. 

Just tried disabling wireless through the wireless icon, re-enabling it, giving it some time to scan for SSIDs, then connecting. No go. 

I neglected to point out at the outset, I've used this card to connect to this router before, so it ought to work again. I also tried to connect to a neighbor's network using this card a few minutes ago and it worked, so we know the card's still working.

---

### Post by MSPdwalt on 2010-09-22
What kind of security is your neighbor using?

---

### Post by unckybob on 2010-09-22
No security. It's just a library.

---

### Post by unckybob on 2010-09-23
Finally got on the phone with the router people. Had the wrong settings on my router. 

I should have called them first. Sorry for wasting your time. I have to do better next time. 

Thanks so much for sticking with me on this one just the same.

---

