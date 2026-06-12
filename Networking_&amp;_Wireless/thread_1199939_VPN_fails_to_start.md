---
title: "VPN fails to start"
date: 2009-06-29
forum: Networking &amp; Wireless
---

### Post by the_joey_o on 2009-06-29
I'm having trouble connecting to my work via a VPN. I get the following error message:

"VPN Connection Failed. The VPN connection (null) failed because the VPN service failed to start."

I've read through a lot of the documentation out there and many of the forum posts on VPN problems. I haven't been able to find one that helps me out.

Some additional information: I'm working with a PPTP connection. My work doesn't supply an IP address, but I do have a normal address (Vpn-st.something.com) and a DNS address.

---

### Post by the_joey_o on 2009-06-30
Bump.

---

### Post by wagoodman on 2009-07-04
I am having the *exact* same problem. Anyone have any suggestions?

---

### Post by zonyl on 2009-07-09
Just upgraded from Ibex and have the same problem.. Tried deleting and recreating the connection as well with no luck.

---

### Post by the_joey_o on 2009-07-15
Let's try this again. Bump.

---

### Post by jasondrew on 2009-07-25
Following the steps on this page worked for me:
[http://bartolomew.net/2009/01/29/vpn-over-pptp-in-ubuntu-broken/](http://bartolomew.net/2009/01/29/vpn-over-pptp-in-ubuntu-broken/)

I didn't need to do steps 4 and 5, but VPNs can differ.

Another solution that worked for me is to install kvpnc and its dependencies and follow the set-up instructions in the "PPTP for OpenSUSE 10.2" section of the page:
[http://en.opensuse.org/Documentation/VPN](http://en.opensuse.org/Documentation/VPN)

Hope that helps.

---

### Post by Copernicus1234 on 2009-07-28
I had the exact same problem. I reinstalled the pptp network manager package.

sudo apt-get remove network-manager-pptp
sudo apt-get install network-manager-pptp

Now it works.

---

