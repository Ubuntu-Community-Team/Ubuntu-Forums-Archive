---
title: "Weird Network Problem"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by axeman69 on 2009-02-27
I put Intrepid up and it found my wireless network fine. When I take the computer to my office, and plug it into my wired network, it grabs an address and connects fine. 

Now, I'm trying to use System -->Preferences-->Network Administration to both add a new wireless network (office) and change my wired address to static. I'd also like to configure a couple of PPTP VPNs. The problem is that the information in the Network Administration applet is being ignored. And, when I reboot the computer, the static address is lost, and the applet is set back to DHCP. 

When I try to edit the configuration file using sudo gpedit /etc/network/interfaces all that's in there is:

auto lo
iface lo inet loopback

Any idea how I can either get Network Administration or manually configure the config files to be able to add these networks? 

Thanks

---

### Post by axeman69 on 2009-03-02
Bump

---

### Post by axeman69 on 2009-03-02
Bump

---

