---
title: "Help connecting WLAN network to LAN network"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by peller on 2012-10-30
Hi,
I have a computer that connects to the WiFi router wirelessly. I'd like to share that wireless connection through a LAN switch with other computers. Some of them will need Static IPs and the rest should get their IPs from the WiFi router over DHCP. They should all be able to connect to the internet as well as see all the other computers connected to the WiFi router (SSH/NFS/Samba/etc). The wifi-to-lan bridge computer will ideally be running Linux, but I can put up with Windows if necessary.

Is this possible, and if so, what keywords should I be Googling? Or even better, how?

Thank you!!!! :P

---

### Post by aromo on 2012-10-30
Normally, wireless routers have at least one Ethernet port.  Look for yours, if that's the case, you could plug a regular switch and that would give you physical connectivity to your wired machines.

Now, you have to configure DHCP on your Wireless router.  Make sure that the static addresses used in your wired network do not overlap (but belong to the same network as) the DHCP scope defined in the router.

If your Wireless router do not have an Ethernet port, you need to set up the Linux router with both Wireless and Ethernet connections, and set a default route from the Ethernet interface to the Wireless.  Then you need to specify the address of the Ethernet interface of your Linux router as the default gateway for your wired machines.

A specialized Linux distro could be more appropriate in your case.  I know of Vyatta (though, never tried it), for instance.

---

