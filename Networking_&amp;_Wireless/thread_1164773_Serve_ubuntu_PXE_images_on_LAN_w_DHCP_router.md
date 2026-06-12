---
title: "Serve ubuntu PXE images on LAN w/ DHCP router?"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by SoftwareExplorer on 2009-05-20
Hi all,
I have a computer that I would like to use for folding at home. It has no hard drives and I used to run it off LiveCD. However, it is cumbersome because I have to set everything back up whenever the power is interrupted. I've been reading about PXE booting and thought it might be the perfect way to solve my problem. However, Setting it up has me confused. I have a router that does the DHCP for the lan. My computer that would be the server has a wireless card that is natively supported and a cabled lan port. The client also has a cabled lan port. I don't want to turn off DHCP on the router and use my computer as a DHCP server because my father wouldn't be able to get on the Internet if my computer was off. So, is it possible to set up my computer to serve a PXE image to the client without having DHCP on the server **or** to have the server connected to the router via wireless and the client connect to the server via cable and serve DHCP just for the cable connection?

---

### Post by SoftwareExplorer on 2009-06-26
bump

---

### Post by jhannah on 2009-06-28
I'm afraid there isn't really an easy solution to your needs. The PXE filename is passed as part of the DHCP reply so the server that is handing out leases to the machine you wish to PXE off must be configured to serve the PXE filename as well. That isn't to say that, if your router has a configuration DHCP server, you might not be able to specify a custom option. You do also have two other options that come to mind.

First, it is possible to restrict a scope to a subclass of machines based on MAC address. With this in mind, you could restrict the whole scope of addresses on your PXE DHCP server to only a particular MAC address with something like the below configuration:

```

subclass "pxeclients" 00:11:22:33:44:55;

subnet 10.0.0.0 netmask 255.255.255.0 {
  pool {
    filename "/tftpboot/pxeimage";
    allow members of "pxeclients";
    range 10.0.0.50 10.0.0.60;
  }
}

```

Keep in mind that if you misconfigure the DHCP server and it starts sending leases to machines that the primary DHCP server is also providing leases to you will likely end up with less than ideal results. It is also worth mentioning that if you are running a DHCP server, you need to have a static IP configured on the interface that is in the scope you are defining.

Your other option would be to create a new broadcast domain. You could do this by simply plugging the machine into the wired port on your machine with a cross over cable or by hooking up that port to a switch which has the machine you wish to PXE boot also connected. You can then configure your wired interface with a static IP that isn't a part of your general network and serve leases over that interface.

Either should work but it depends on how much you want to dig into DHCP and what options your router's DHCP server offers.

Hope that helps.

---

### Post by SoftwareExplorer on 2009-07-04
So if I made a cable between the server and client, then could I make the server assign DHCP Addresses on just that connection?

---

### Post by cuschu on 2009-07-04
You can tell the DHCP server to only listen on one particular interface by editing the */etc/default/dhcp3-server* file.

---

### Post by SoftwareExplorer on 2009-07-04
> **cuschu said:**
> You can tell the DHCP server to only listen on one particular interface by editing the */etc/default/dhcp3-server* file.

So, could the client still get Internet access if I did that?

---

### Post by airchie on 2009-07-04
Could you not use the router to reserve specific IPs for specific machines based on MAC address?
Thus allowing one mchine to act as a server as it never changes IP while still allowing any visitors to the LAN to get on?

---

### Post by SoftwareExplorer on 2009-07-05
> **airchie said:**
> Could you not use the router to reserve specific IPs for specific machines based on MAC address?
Thus allowing one machine to act as a server as it never changes IP while still allowing any visitors to the LAN to get on?

My router doesn't have that feature, but I know how to set my servers ip static and tell the DHCP on the router not to use those ones.

---

