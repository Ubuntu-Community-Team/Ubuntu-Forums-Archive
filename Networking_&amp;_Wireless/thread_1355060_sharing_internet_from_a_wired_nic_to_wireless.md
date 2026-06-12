---
title: "sharing internet from a wired nic to wireless?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by me2621a on 2009-12-14
Hi, im new to ubuntu(9.10) and trying to figure out if this is possible. My computer is connected to the internet using the ethernet cable. The computer also has a wireless card, what i would like to do is share the network connection from the ethernet to the wireless card so other devices can connect through the wireless card to the internet.

So my questions are
can this be done?
if so how do i do it?
and can i make it secure (WPA) 

Thanks for the help

---

### Post by MaindotC on 2009-12-14
[Yes you can.](http://is.gd/5ns5U)

---

### Post by me2621a on 2009-12-14
Thanks, i tried the first tutorial and now have my wireless card broadcasting a network but its not assigning ip's and forwarding the internet though, any ideas?
Thanks

---

### Post by MaindotC on 2009-12-14
Yes you need to set up the DHCP service to issue addresses on your wireless NIC.  You could also assign the wireless card an IP, and assign any clients you wish to connect ip addresses manually to save time.

---

### Post by me2621a on 2009-12-14
could you please explain how to go about doing this, or link me to a tutorial? Thank you again for all your help so far.

---

### Post by Iowan on 2009-12-14
[This]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") kinda looks like what you're trying to do - although UFW has replaced Firestarter as preferred **iptables** front-end. The ICS link at the bottom provides some DHCP setup information.

---

### Post by MaindotC on 2009-12-14
> **me2621a said:**
> could you please explain how to go about doing this, or link me to a tutorial? Thank you again for all your help so far.

Ok no one needs to do anything with iptables or ufw so please don't make this more complicated than it needs to be :D  Iowan that is a good link tho.

[This is the official documentation](https://help.ubuntu.com/community/Internet/ConnectionSharing) for enabling Internet Connection Sharing as well as setting up DHCP services.

---

### Post by Iowan on 2009-12-14
> **strAlan said:**
> [This is the official documentation](https://help.ubuntu.com/community/Internet/ConnectionSharing) for enabling Internet Connection Sharing as well as setting up DHCP services.That's the link at the bottom I referenced...;)
**iptables** and Firestarter got mentioned there as well.

---

