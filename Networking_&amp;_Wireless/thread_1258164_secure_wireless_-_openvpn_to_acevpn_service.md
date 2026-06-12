---
title: "secure wireless - openvpn to acevpn service"
date: 2009-09-04
forum: Networking &amp; Wireless
---

### Post by linux6994 on 2009-09-04
For those of use that are relegated to using open unsecured wireless networks there is an answer that allows encapsulating your INTERNET traffic with a tunnel via openvpn. I am not trying to sell the service even though it's only $5 USD a month but letting you know that it works and is easy to set up, here is how:

sudo apt-get install network-manager-openvpn openvpn

Then use network manager gui to import the acevpn-premium-udp-faster.conf file (once you have brought down and unzipped it according to the site instructions) and add user name and password into the gui. Then you can use the network manager to connect and disconnect at will.

The website instructions do not include using the network manager gui but I have asked them to include it.

Good luck - keep your connections secure!:D

---

### Post by ed5000 on 2009-09-13
encapsulating your INTERNET traffic with a tunnel via openvpn. 

Wow, how does this work?

Thanks

---

### Post by linux6994 on 2009-09-14
When you are in a tunneled service in a vpn even though you are on an open unsecured wifi your data is actually seen as application data and can not be read. Use Wireshark running as root and go Yahoo mail, it's not locked down via https and you will see you data in the clear. Using the vpn you will not be able to see it at all.

good luck.

---

