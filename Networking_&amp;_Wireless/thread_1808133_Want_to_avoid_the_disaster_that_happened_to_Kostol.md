---
title: "Want to avoid the disaster that happened to Kostolnik"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by rocksockdoc on 2011-07-19
According to this scary wi-fie hacking article:
- [http://www.cnn.com/2011/TECH/web/07/13/wifi.hacking.neighbor.sentenced.wired/](http://www.cnn.com/2011/TECH/web/07/13/wifi.hacking.neighbor.sentenced.wired/)

A neighbor was sent to jail for 18 years for seriously hacking his neighbor:
- [http://www.wired.com/images_blogs/threatlevel/2011/07/ardolffedssentencingmemo.pdf](http://www.wired.com/images_blogs/threatlevel/2011/07/ardolffedssentencingmemo.pdf)

What can we install on Ubuntu to forestall such an occurrence at home (given a WRT54G router & 1 Ubuntu computer)?

---

### Post by doas777 on 2011-07-19
make sure your router is configured to allow only WPA2 Personal with AES encryption. do **not** allow TKIP/AES, as that is breakable.

consider using a mac filter. its far from fullproof, but does make it a bit harder for the attacker.

disable UPNP on your router, and limit network services within your lan, and do not allow services that expose sensitive data. consider encrypting sensitive data using a tool like truecrypt. practice safe computing regarding email attachments. 

in the long run, physical security is paramount in these cases. if somone can get a couple hours (or even minutes if they are good) unsupervised with your equipment,  they can own you 12 ways from Sunday, with no practical defense, but to teardown everything and bring it back up in the dark.

---

### Post by rocksockdoc on 2011-07-20
> **doas777 said:**
> make sure your router is configured to allow only WPA2 Personal with AES encryption. do **not** allow TKIP/AES, as that is breakable.

Just checked. I only have AES encryption with WPA2 Personal.
```
Linksys WRT54G -> Wireless -> Wireless Security -> Security Mode = WPA2 Personal
Linksys WRT54G -> Wireless -> Wireless Security -> WPA Algorithms = AES

```> **doas777 said:**
> consider using a mac filter

Already using MAC filtering. 
```
Linksys WRT54G -> Wireless -> Wireless MAC Filter -> Wireless MAC Filter = Enable
```> **doas777 said:**
> disable UPNP on your router

It took me a while to find the UPNP setting on the WRT54G router, which was "Enabled" by default. I'm not sure what detrimental effect this may have, but, I disabled it.

```
Linksys WRT54G -> Administration -> Management -> UPnP = Disable
```

And, I turned on "AP Isolation":
```
Linksys WRT54G -> Wireless -> Advanced Wireless Settings -> AP Isolation = On
```I turned off wireless access to the router:
```
Linksys WRT54G -> Administration -> Management -> Wireless Access Web = Disable
```

** What else would dissuade a nosy neighbor from hacking into my router?**

---

### Post by rocksockdoc on 2011-07-20
I also installed [arpwatch as per this web site]("http://aimlinux.com/blog/?p=56"):

> **Arpwatch  keeps  track  for  ethernet/ip  address  pairings.   It syslogs activity and reports certain changes via email.  Arpwatch   uses  pcap(3) to listen for arp packets on a local ethernet interface.** *Note:  you must have exim4 or postfix setup with SMTP, be it local  or  external if you wish to send out “alerts” to external email address.*
 [Click Here ]("http://techgurulive.com/2009/01/09/how-to-install-and-configure-exim4-in-ubuntu/")to find out how to setup exim4 on Debian based systems.
 Run the following commands from terminal.
```
**sudo apt-get install arpwatch**
Create empty file for storing host information:
**sudo touch /var/lib/arpwatch/arp.dat**
Edit the config file:
**sudo nano /etc/arpwatch.conf**
insert line like this:
**eth0 -a -n 192.168.1.0/24 -m youremail@mydomain.com**
Restart arpwatch:
**sudo /etc/init.d/arpwatch restart**
Check if the process is running:
**ps –ef | grep arpwatch**
root 218 1 0 11:38 ? 00:00:00 /usr/sbin/arpwatch ...
```

What else would you suggest to prevent a neighbor from hacking into the router?

---

