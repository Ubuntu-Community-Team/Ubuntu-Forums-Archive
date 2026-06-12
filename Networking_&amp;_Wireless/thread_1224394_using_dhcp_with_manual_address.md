---
title: "using dhcp with manual address"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by paleozogt on 2009-07-27
How can I configure Ubuntu to use DHCP with a static IP address?  There doesn't seem to be anything for it through the gui, and I'm not sure what the syntax for /etc/network/interfaces should be.

---

### Post by raronson on 2009-07-27
Follow the red dots in the attached screenshot using the NetworkManager Applet.  You confused  me a little though, if you use DHCP, your connection should auto-configure.  If you opt to specify a manual address, there's no need to use DHCP.

Hope this helps.

---

### Post by paleozogt on 2009-07-27
That's just a screen for regular manual setup.  What I'm looking for is to be able to specify the IP address statically, but then to get the DNS and router info from DHCP.  

On Mac OS X it looks like the attached screenshot.

---

### Post by audiomick on 2009-07-27
I solved this by reserving an address for my desktop and 2 laptops on the router.(SMC something-or-other)

Hope this helps

---

### Post by raronson on 2009-07-27
Edit: Ah, sorry.  Wasn't paying careful enough attention to your DNS info from the screenshot you posted.

---

