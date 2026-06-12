---
title: "VPN server/client"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by nephesh on 2006-06-01
I've read/searched the forums but can't seem to find what I need.

I'm looking for a walkthrough/guide on howto install a vpn server and client for connecting to it.  I want to be able to access local network samba shares and gain remote control over my home computer through this vpn connection.

Thanks for any help.

---

### Post by spin2cool on 2006-06-01
vpnc is a good vpn client.  Offhand, I don't know of any servers.  Tried google/searching the forums yet?

---

### Post by kiddyfurby on 2006-06-02
install the pptp-linux package
that includes server and client as far as i know

I use it as client myself

To get you started: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

---

### Post by jetpeach on 2006-06-11
I tried to follow the steps in the guide listed above, but the address they say to add to the sources.conf to download the GUI configuration program doesn't resolve properly.  Does anybody know if there is another location to find this GUI config program?  I saw you can manually configure it, but the instructions looks very lengthy and time-consuming.
Thanks!
jet

---

### Post by masinger53 on 2006-06-13
jetpeach, I had a similar problem with the directions for installing pptpconfig on that page with my fresh Ubuntu Dapper install.  

When I vi'd /etc/apt/sources.list to make sure I'd pasted in the correct code, I noticed that all the other entries were paired, with a second line for deb-src.

So, I did:

[FONT="Courier New"]
# James Cameron's PPTP GUI packaging
deb [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
deb-src [http://quozl.netrek.org/pptp/pptpconfig](http://quozl.netrek.org/pptp/pptpconfig) ./
[/FONT]

then the install worked fine.

---

