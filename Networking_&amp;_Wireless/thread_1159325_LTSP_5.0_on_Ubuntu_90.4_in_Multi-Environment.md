---
title: "LTSP 5.0 on Ubuntu 90.4 in Multi-Environment"
date: 2009-05-14
forum: Networking &amp; Wireless
---

### Post by xine11 on 2009-05-14
I have setup a LTSP 5.0 setup on Ubuntu Server in a Multi environment (There is a Windows Server 2003 dishing out IPs (DHCP) and giving internet access). Everytime I try to boot, the PXE correctly finds the server and downloads a few modules and then the Ubuntu splash comes up, using Alt + F1, I can see mount errors coming up and the boot fails leading to a BusyBox prompt.

> mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init                      The same thing happens on two computers.. one ancient P2 and a P4.

I have read ALL the other threads in these forums, aswell as the Ubuntu Documentation and the Administrators Guide. Everything doesn't seem to work... 

[LIST]
[*]Edits to the config file
[*]Listing Individual hosts in the file
[*]checked if xinetd is installed (No)
[*]Triple Checked all IPs
[/LIST]
The only funny thing is that when mounting it tells me the root server's IP is: 192.168.2.16 - which is the windows fileserver + DHCP, which probably is supposed to be the linux server at 192.168.2.25.

192.168.2.16 isn't listed anywhere in the LTSP config file... 

The school I'm doing it for is getting frustrated and will end up giving up on Linux forever if this fails.

Thank You in advance!

---

