---
title: "randomly unable to get inbound connections"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by JLahm on 2010-06-24
I have Ubuntu Desktop 10.04 installed on a machine that I use as a simple print server. I run CUPS on it so my wife can print downstairs from her laptop. Everything worked great until I upgraded to 9.10. I now have frequent problems where we cannot connect to the CUPS server on Apache. This has continued since I upgraded to 10.04. The basic symptoms:

* You cannot print to the CUPS server.
* You cannot browse to the CUPS server admin pages
* You cannot browse to any web page on the Apache server
* You cannot connect to the machine using SSH or Telnet
* You can use wget from a remote machine to access web pages on the Apache server (including CUPS)
* On the machine itself, you can use Firefox to browse the Internet

This condition will continue for a while and then the machine will "recover" and all will be fine again - for a while.

WICD says it is still connected. If I go ahead and browse for any available networks, I can connect to my local network (even though it says it is still connected) and reconnect. When I do, every thing works.

I am not running a firewall on this machine. I've disabled IPv6 as I read that caused issues. I am using WPA2/AES and have assigned the machine a static IP on my local network. The machine uses a RaLink RT2561/RT61 wireless chipset with the rt61pci driver.

Any ideas? This is driving me a little wacky... :-)

Many thanks.  ---Jim

---

