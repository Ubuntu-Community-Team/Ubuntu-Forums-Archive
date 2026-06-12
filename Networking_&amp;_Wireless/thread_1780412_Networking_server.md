---
title: "Networking server"
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by kid1000002000 on 2011-06-12
Hello world.

I have googled alot but am too new to understand everything my first time thru this.  Here is what I want to do:

I have a home that connects to the internet through a dd-wrt enabled router downstairs.
I have an "ubuntu desktop" server sitting upstairs.  It connects wirelessly to the internet via the router.  This server also runs openVPN.  This device also has a wired Ethernet cable that connects to a switch.

I have a laptop (Ubuntu 11.04), among other devices, that needs to  connect to the server 3 ways: via the internet, home wireless, and via  cat5 for maximum bandwidth.  When the laptop is connected to the server by wire, I still need both machines to have internet access.

1.  How can I configure the server to allow all of these things to happen?  i.e.: do I need to bridge?  Why or why not?

**2.**  Will bridging (or whatever I need to do) slow down my wired connection *between all wired machines *to wifi speeds?  What can I do to avoid this? (important- this is my biggest question!)

3.  I would like to leave my laptop as unconfigured as possible.  i.e. internet access is automatic when a device (like the laptop) connects to the switch.  All configurations need to be done on the server if possible (ddwrt has stability issues, and I crash my laptop too much to bother configuring it).

To accomplish this, will my server need to be configured as a DHCP server, or will the 1st router take care of that?  Will I need to configure the server as a 2nd router for any other reason?  Please explain!

4.  What networks (the switch, home wireless) could the (wired, vpn, wireless) laptop be permitted to "see" in such a setting?  Important for accessing a wireless printer.

Thank you.

---

### Post by kid1000002000 on 2011-06-24
bump

---

