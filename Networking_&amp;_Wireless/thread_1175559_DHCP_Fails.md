---
title: "DHCP Fails"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by wrwarwick on 2009-06-01
Hi all,

I recently rolled back from 9.04 to 8.10 due to wireless issues I was having. I have an HP laptop with a broadcom wireless card and was not able to get it to work on 9.04 but the card is functioning with 8.10. 

The problem that I am having is that it fails to get an IP address via DHCP. If I watch the logs while it connects I can see the card connect to the wireless network and send out a DHCP request, but it times out and will not get an IP. 

Does anyone know what might be causing this?

---

### Post by MichaelSammels on 2009-06-01
I do not know what may be causing this, but I have a possible solution. If you know your internal IP address, gateway and subnet mask you can set this up manually via Network Manager. You will also need your gateway, which can be obtained from your routers settings page normally.

---

### Post by wrwarwick on 2009-06-01
I should probably try setting the IP configuration manually, but am really trying to setup DHCP. The laptop will be used in different locations and static IP settings is not the most efficient solution.

---

### Post by MichaelSammels on 2009-06-01
I suggest that you examine your /var/log/syslog file for any errors or sticking points. If you are unsure then please post it here and we will take a look.

Common problems are a failure to associate, failure to complete handshake (authenticate) or DHCP times out and avahi-autoip kicks in.

---

### Post by superprash2003 on 2009-06-01
post content of /etc/dhcp3/dhclient.conf

post output of **sudo dhclient eth0 **
where eth0 is the interface where DHCP is enabled

---

### Post by Iowan on 2009-06-01
> **wrwarwick said:**
> Does anyone know what might be causing this?Maybe...
Check [here]("http://ubuntuforums.org/showthread.php?t=1156441") or [here]("http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html") ... 
No promises... ;)

---

