---
title: "Cable modem networking problem"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by maulteez on 2010-02-14
Hi all,
I just got connected to Charter Cable Internet service a few days ago and I'm having a weird problem with my home network. Prior to this my network worked fine. On my network I have a desktop running Ubuntu 9.10/64 and Virtualbox with WinXP installed, an HTPC with Ubuntu 9.10/32 installed and a laptop dual booted with Ubuntu 9.10/32 and WinXP. The desktop and HTPC are hard wired to a wireless router and the laptop is wireless. The cable modem is hard wired to the router. I have samba installed and UFW is disabled. The problem is: with the cable modem turned off or on standby, all machines connect to each other and can transfer files, etc just fine but when I activate the cable modem all of the machines can connect to the Internet but the machines running Ubuntu can't connect to each other on the home network. If I boot the laptop into Windows, it can connect to the Linux machines just fine but if I boot it into Linux, it won't connect to the Linux machines but it can connect to the Internet and as far as the desktop, Ubuntu won't connect to the network but Windows running in the Virtualbox with bridged networking can connect to all of the machines. Any suggestions on how to resolve this issue would be really appreciated.

---

### Post by Iowan on 2010-02-14
Can the machines ping each other - in particular, by IP address? It almost sounds like DNS requests are being sent to internet (where they probably won't be found).

---

### Post by maulteez on 2010-02-14
Hi,
Thanks for the reply. Yes, they can ping each other.

---

