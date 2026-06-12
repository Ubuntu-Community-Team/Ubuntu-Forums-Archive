---
title: "Can hostnames be setup without modifying /etc/hosts"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by oygle on 2010-06-24
Every time I do a fresh install, there are a number of manual config things to change. One of them is to modify /etc/hosts to add the local IP addresses to a computer name.

Can this be done via the Ubuntu networking somehow ?  It would be nice not to have to change some of these config files.

---

### Post by Iowan on 2010-06-24
A local DNS would make the job easier - I use DNSMasq as DHCP/DNS server. It keeps track of hostnames/IP addresses (if machines are configured to "send hostname").

---

### Post by oygle on 2010-06-25
Not too sure about the 'send hostnames' part ?

Found this ........

> DNSmasq is not designed for so-called "Internet Connection Sharing," however, it does provide a lot of the services needed in the background. With DNSmasq set up, only two additional commands can set up internet connection sharing (ref?).

from the [Dnsmasq documentation]("https://help.ubuntu.com/community/Dnsmasq") , and I use ICS, so not too sure how it would all affect my internet connection setup and the dns I use now.

Maybe I'll just have to edit those files each time. Pity there is nothing setup under the GUI networking side of things. I use a USB dongle for internet, so if I had a USB router, no doubt I could setup the hostnames on that, just once.

Thanks,

Oygle

---

### Post by Iowan on 2010-06-25
> **oygle said:**
> Not too sure about the 'send hostnames' part ?
Sorry...
*/etc/dhcp3/dhclient.conf* has a line:```
send host-name "<hostname>";
```
that can be changed to the machine's actual hostname.
The older setup for [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") called for installing DNSMasq - I'm not really trying to push DNSMasq, though ...

---

### Post by oygle on 2010-06-26
Thanks Iowan. I need to define 3 computer names, one for each LAN IP, so it looks like I'll just make a note to modify /etc/hosts on a new install.

---

