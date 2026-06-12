---
title: "First-time home FTP server."
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by venividibitchy on 2010-01-13
Any assistance with getting my first FTP server up and running would be appreciated. I've tried three different ways, and am really getting frustrated. I've read all of the articles online about how to do it, but they are all incomplete or ambiguous.

I want the FTP server to be hosted using my own internet connection/computer. I am running Ubuntu 9.10, and connect to the internet wirelessly through a wireless router and cable modem. I've forwarded ports 20 and 21, and 50000-50100, and checked that my ISP allows FTP servers.

I installed vsftpd in terminal, but no client/window ever appears afterwards. I don't see any new applications in my menu that I could launch. Is vsftpd meant to be a hidden running process only?

---

### Post by changingstate on 2010-01-13
Yes. nmap your machine and you should see the ftp port open. The program is entirely controlled through /etc/vsftpd.conf

---

### Post by venividibitchy on 2010-01-13
For anyone who finds this info. useful, I've been able to get it mostly up and running.

I had to enable my router's DMZ and set it to my internal ip.

I then discovered the directory for placing files into is /srv/ftp and *not* /var/www/ftp.

Directing my brower to [ftp://127.0.0.1](ftp://127.0.0.1) and [ftp://internal](ftp://internal) ip (192.168.1.x) works, but unfortunately, accessing it externally through [ftp://external](ftp://external) ip (69.x.x.x) from an outside network does not.

Checked the config. file, and it was set to allow both anonymous and local users. I also disabled my firewall. No bueno.

Any ideas?

---

### Post by lisati on 2010-01-13
Check out your router's "Port forwarding" options. The location is pretty obvious on my Netgear router's control panel, but on my Thomson Speedtouch it's hidden under "Game and Application" sharing.

---

### Post by changingstate on 2010-01-13
I had these symptoms when setting up my asterisk server, as my router wouldn't loopback packets from the internal network. I had to log into the routers shell to enable local loopback. 

You could also ask a friend to try connecting to test it, if it is this fault.

Edit : If desperate, you could try asking for a portscan from grc's shields up here : [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by venividibitchy on 2010-01-13
> **changingstate said:**
> I had these symptoms when setting up my asterisk server, as my router wouldn't loopback packets from the internal network. I had to log into the routers shell to enable local loopback. 

You could also ask a friend to try connecting to test it, if it is this fault.

Edit : If desperate, you could try asking for a portscan from grc's shields up here : [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

> **lisati said:**
> Check out your router's "Port forwarding" options. The location is pretty obvious on my Netgear router's control panel, but on my Thomson Speedtouch it's hidden under "Game and Application" sharing.

Thank goodness you mentioned this again -- I realized that I had originally set the port forwarding to .101, when it needed to be .103, and as soon as I fixed it, VOILA. Thanks so much-

Also of note to anyone doing this for the first time, you can just disable port 20/21 instead of disabling the entire firewall. Here's what link I followed: [http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/](http://www.cyberciti.biz/faq/iptables-open-ftp-port-21/)

---

