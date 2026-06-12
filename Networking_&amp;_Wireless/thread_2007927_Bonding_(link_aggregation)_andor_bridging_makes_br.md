---
title: "Bonding (link aggregation) and/or bridging makes bridged mode in VMs unusable"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by leo_m on 2012-06-21
This is about VMs created using VirtualBox and libvirtd (virtual-machine-manager)

I have wireless wlan0 interface bonded to wired eth0 interface.  wlan0 interface is the active interface - the interfaces are bonded in backup mode (not load balancing mode), so only one is used (wlan0 presently).

I was led astray in the direction of having to do various workarounds since bridging is not supposed to work over wireless...it turns out all those workarounds are  not needed in my case (or may they are if I wish to use bond0/br0 as the bridge device in vm config).

So, this works for me:
Using Virtualbox in bridged mode, bridged with wlan0 interface.

But these do not:
Using Virtualbox in bridged mode, bridged with the br0 bridge interface which in turn has only bond0 as its bridge-port in /etc/network/interfaces.
Using Virtualbox in bridged mode, bridged with the bond0 interface.

Since libvirt bridged mode, as configured via virtual machine manager, needs a host bridge, I cannot use the bridged mode with wlan0 (wlan0 is not a bridge device)

libvirt routed network mode works if I provide suitable ebtables and iptables rules, but I do not want to have to do that - I want to use the bridged mode.

I do not want to use libvirtd routed mode (which requires some workaround to be put in place, like ebtables/iptables rules or proxy-arp with sub-subnetting etc.).  I do not want to use host-only adapter mode in Virtualbox either.

As the bridged mode in Virtualbox works fine if bridged with wlan0 interface and bridged mode with br0/bond0 does not work with either libvirt or Virtualbox, I am wondering why exactly do the DHCP requests not result in DHCP offers being seen in case of bridged mode with br0/bond0 but are seen (and guests get configured correctly) in case of bridged mode with wlan0 using Virtualbox.

My AP, which is built into the ADSL modem-router hardware package, does not appear to have any trouble allocating DHCP addresses to different MAC addresses from the one/s authenticated via WPA2 if those requests came in via the authenticated interface (wlan0/br0/bond0 in my case).  Please note that even in case of using bond0/br0 in the bridged mode networking in libvirt/VBox, I can see DHCP requests are going out (but I do not see any DHCP offers at the wlan0 interface in these cases and I fail to understand why that is the case).

So, the question is: how to get bridged mode in libvirt and Virtualbox to work (where to work means a) get DHCP addresses allocated from the DHCP server running in ADSL modem-router and b) access the internet (that'll work if a) is resolved)), using br0/bond0 in host (as opposed to using wlan0 as the bridge interface in VBox)?

Internet access is okay from the host.

I do not think I can use dhcp-relay as dnsmasq provided by libvirtd is already using the DHCP port.  But do you think a missing dhcp-relay is the only missing piece of the puzzle (is it needed at all?).  I do not know how libvirtd is able to run multiple instances of dnsmasq itself though (one for default network, one for a routed network I created (but not using in any VM at the moment) etc.) with DHCP services running on all these dnsmasq instances...

In case you do think dhcp-relay is the missing piece, I am not sure which two interfaces I would include in the relay as in bridged mode, there are no VBox bridge interfaces  (although in case of libvirt, the vmnet0 interface is brought up when the virtual machine is started, so I can, arguably, start the dhcp-relay at that time as well - via a script to start/stop the virtual machine - if I have the dhcp port free that is).

---

### Post by leo_m on 2012-06-22
Added isc-dhcp-relay, now getting DHCP allocations, but contrary to what I thought, that does not result in success in getting internet connectivity from the guest!  However, isc-dhcp-relay and dnsmasq run by libvirt are both running simultaneously without any apparent problem (again contrary to what I thought)!  I have  included just the br0 interface in the dhcp-relay interfaces, not sure if that's a good thing to do, but had no other known interface used by VBox/libvirt for their bridge mode networking up at the time (both VBox and libvirt bring up their bridging related interfaces at VM boot up)

route shows okay (default route goes to ADSL router)
resolv.conf has DNS listed okay
IP address and network as listed via ifconfig are okay.

So, I don't know else is needed...I can't even reach the ADSL router's web-page (LAN side).

Time for parprouted?

---

