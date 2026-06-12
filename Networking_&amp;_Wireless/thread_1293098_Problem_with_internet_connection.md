---
title: "Problem with internet connection"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by AlmoG on 2009-10-16
Hello, I'm trying to help a friend with his first ubuntu installation.
Everything went smoothly only after the installation (from disc) the internet connection won't work :(

He is using a wired LAN cable modem (model number SB4101 motorola).
I can't seem to find what is the IP of the config utility for this modem...

Ubuntu seems to recognize the modem type, NetworkManager Applet showed me the correct model and all.

Can anyone help me with this? I've never had to set up any internet connection before so I'm kind of stuck.

---

### Post by Iowan on 2009-10-16
Does the machine get an IP address? (**ifconfig** from a terminal)

---

### Post by jonobr on 2009-10-16
is your client running DHCP? Im guessing it is,

Run an ifconfig on a terminal window and see if you are getting an IP address.

If you are then if its a 192.168.1 private address the most likely address for the router is 192.168.1.1

Stick that in a browser and see if that responds.
If not I would check for a manual somewhere to see if it differs.
However, you need to ensure you are getting an ip address from the thing first,

---

