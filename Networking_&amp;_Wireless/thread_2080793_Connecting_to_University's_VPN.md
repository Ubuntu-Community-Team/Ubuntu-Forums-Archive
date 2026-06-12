---
title: "Connecting to University's VPN"
date: 2012-11-05
forum: Networking &amp; Wireless
---

### Post by charlescarroll1 on 2012-11-05
I've been having trouble connecting to my university's VPN with Ubuntu 12.10. On the setup instruction page on my university's website, it instructs Windows and Mac users to use download and install Cisco Anyconnect VPN Client ([here's a link to the page]("http://www.pdx.edu/oit/vpn")). I did a bit of searching and found "Network management framework (OpenConnect plugin GNOME GUI)" in the Software Center which is a package that provides GNOME's Network Manager a plugin. 

I go to Network Connections > VPN > Add > Cisco AnyConnect (openconnect) then enter in as much information I can on from PSU's webpage. 

Here's the information I've entered:
Check Connect Automatically
Gateway: vpn.pdx.edu

Not sure if I'm supposed to fill anything else out.

I got to the network dropdown menu and turn on VPN Connections and then a windows pops up "Connect to VPN 'PSU'". Here, I choose the group "PSU Students" and enter in my school user name and password. It connects successfully.

Here's the issue I'm having... Isn't my IP address supposed to be different now that I'm connected to my university's VPN? When I got to whatismyip.com, it is the same IP address regardless if I'm connected to the VPN or not.

Any ideas?
Thanks :)

---

### Post by dwmw2 on 2012-12-03
Please see [http://www.infradead.org/openconnect/mail.html](http://www.infradead.org/openconnect/mail.html)

---

