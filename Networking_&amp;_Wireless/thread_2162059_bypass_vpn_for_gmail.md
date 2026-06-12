---
title: "bypass vpn for gmail"
date: 2013-07-12
forum: Networking &amp; Wireless
---

### Post by Derek Trotter on 2013-07-12
I'm having trouble with my VPN.  It won't let me connect to gmail's SMTP servers.  Their support page says they block access to smtp becuase spammers have abused this in the past.  So I need to bypass the VPN for connections to smtp.googlemail.com port 465.  I'm guessing bypassing the VPN for port 465 would work.  I also would be happy with bypassing the VPN for all traffic to smtp.googlemail.com which resolves to 74.125.137.16.

I have Kubuntu 13.04 on this machine.  It has one ethernet adapter.  Here is it's configuration.

IP address 10.0.0.2
subnet mask 255.0.0.0
gateway 10.0.0.1
DNS 8.8.8.8, 8.8.4.4

This is connected to a router that has an internal IP address of 10.0.0.1

I'm using  Open VPN.  I open network manager settings and it shows the gateway for the VPN is 66.23.230.210 under the OpenVPN tab.  Under IP v4 adress I have entered under routes this:

address 74.125.137.16 Netmask 255.0.0.0 Gateway 10.0.0.1

It doesn't work.  When the VPN connection is active, I can't send email.

Can anyone help?

Thanks
Derek

---

### Post by sanderj on 2013-07-13
What is your output of "ip route show"?

---

### Post by Derek Trotter on 2013-07-13
> **sanderj said:**
> What is your output of "ip route show"?

Thanks for your reply sanderj, but I found out what to do.  I'll pass that along in case someone else runs into this same problem.

smtp.googlemail (74.125.137.16) is the server I wanted to connect to.
My router's internal ip address is 10.0.0.1

Add the following to /etc/hosts.
74.125.137.16 smtp.googlemail.com
Replace the above with the ip address and name of the server you want to connect to.

Then enter at the command line
sudo route add -net 74.125.137.16 netmask         255.255.255.255 gw 10.0.0.1
Replace the ip address and gateway address with your own.

Put the route command into /etc/rc.local so it will be available when the machine is rebooted.

---

