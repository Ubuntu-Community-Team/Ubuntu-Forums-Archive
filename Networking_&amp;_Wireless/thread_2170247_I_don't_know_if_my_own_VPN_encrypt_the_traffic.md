---
title: "I don't know if my own VPN encrypt the traffic"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by joan_carles2 on 2013-08-25
I've installed a VPN server. The VPN server is pptpd. I've used the default configuration and I've just done the basic steps to make the server works properly.

I have a doubt. And I don't know if my server is encripting the traffic from the client to the server.

When I setup the client I chose the option encrypt from point to point (MPPE) and I can perfectly connect to the server. Then I use wireshark to sniff the traffic. With wireshark I can see that all the traffic from the client to the server is like this one:
[FONT=Arial]Protocol: PPP Comp
Info Compressed Data[/FONT]
[FONT=Arial]Protocol: GRE
Info Encapsulated PPP[/FONT]

So with this data anyone can confirm if the traffic between the client and the server is encripted? 

I really hesitate because with some VPN I see lines that says encrypted... SSL. But I guess that this is because the other servers works with SSL encription. I think that pptd works with another type of encryption. (I odn't know which one) 

Regards and thanks in advance

---

### Post by Cheesemill on 2013-08-25
This doesn't really answer your question but do you have a good reason for wanting to use PPTP?

PPTP has known vulnerabilities which make it easy to crack, I'd recommend using OpenVPN instead if you are after a secure VPN solution.

---

### Post by SeijiSensei on 2013-08-25
Microsoft's implementation of PPTP was [cracked by Bruce Schneier]("http://www.schneier.com/paper-pptp.html") in 1998.  Unless you live in a Windows-only environment, you should use another method.  Like Cheesemill, I use OpenVPN.

---

### Post by joan_carles2 on 2013-08-25
Thks for your reply. I don't have a really good reason to use PPTP. Anyway I would like to know if my data use MPPE 128 bits encryption.

Also if anyone has a good guide to configure an openvpn server please let me know it.  (In Linux of course)

I also would like to know why pptp is most suitable for windows users. As far as I know with windows you also can connect to openvpn servers.

And thanks to let me know the problems of pptp.

---

### Post by SeijiSensei on 2013-08-25
> **joan_carles2 said:**
> Thks for your reply. I don't have a really good reason to use PPTP. Anyway I would like to know if my data use MPPE 128 bits encryption.

Look in the server's logs, probably in /var/log/syslog.  You should see pptpd entries; if it is using MPPE it will be reported there.

> Also if anyone has a good guide to configure an openvpn server please let me know it.  (In Linux of course)

I use simple [static-key]("http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html") tunnels which are pretty easy to set up.  If you have to support multiple roaming users, you'll need a more complex arrangement.  The OpenVPN site has pretty good documentation.

> I also would like to know why pptp is most suitable for windows users. As far as I know with windows you also can connect to openvpn servers.

Yes, if you install the OpenVPN client for Windows.  Microsoft adopted PPTP/MPPE as its remote access solution nearly two decades ago and integrated support for it into the OS.  I don't if that is still true, but given Microsoft's need to support legacy technologies, I'd bet it is.  I wasn't recommending PPTP as a solution even for Windows users; it's just much more commonly used in Microsoft shops.  There are other VPN solutions like IPSec, but I've found OpenVPN much simpler to configure.

---

### Post by joan_carles2 on 2013-08-25
thanks seiji Sensei

I've checked the log that you mentioned. In the log I found next sentence:

pppd [2633] MPPE - 128 bit stateless compression enabled

So I guess that pptd offers encryption.

I will have a look to how to configure an openvpn server. Just the last question.

You said that pptd has know vulnerabilities. The developers of pptd doesn't try to fix the vulnerabilities?

---

