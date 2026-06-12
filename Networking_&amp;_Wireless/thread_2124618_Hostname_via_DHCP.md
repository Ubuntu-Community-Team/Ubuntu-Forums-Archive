---
title: "Hostname via DHCP"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by sandy on 2013-03-11
Hi All,

I have just started with Ubuntu and will need to set a number of PC hostnames using DHCP, I have tried all sorts of changes to config files to no avail.  Can someone please point me in the right direction so that I may achieve this.

My DHCP server will hand out hostnames the Fedora and Gentoo PCs I have all pick up thier hostnames via DHCP.

I have installed version 12.10, the machine is now has a fresh installation nothing has been changed the hostname is as set during installation.

Thanks in advance,

Sandy Spence

---

### Post by jonobr on 2013-03-11
Hello


Im a bit confused, The DHCP will repond with IP addresses , not hostnames.
Hostnames are usually configured on your machines and can supply them to the server.
Again, maybe Im not understanding your post

---

### Post by efflandt on 2013-03-11
Some routers may pick up the netbios hostname from Windows networking, which might work if you have installed samba and have it properly configured. I don't use Windows networking, so I am not sure about that.

Ubuntu typically installs avahi-daemon by default. That uses the same thing as Apple Zeroconfig, or Bonjour available for Windows, to find other computers by hostname (typically with .local appended to the hostname as the domain). So for example if you had a computer with the hostname ubuntu, you could **ssh ubuntu.local** (or scp or sftp).

If you have Bonjour in Windows, it can use PuTTY to ssh by the hostname.local. Although, it can be a bit trickier to access a local website on Linux from a web browser. For Internet Explorer you have to **disable searching from the location bar**, for Firefox in about:config search for fixup and set **browser.fixup.alternate.enabled** to **false**, and for either browser in Windows you would need to leave off the .local, and just use the hostname.

I learned about avahi when I got a couple of Raspberry Pi computers and needed to ssh/scp to/from them. Although, I had to install avahi-browser in the Debian Linux version that they use. Raspberry Pi is a $35 ARM computer on a credit card size board.

In any case it helps to make sure that each computer has a unique hostname.

---

### Post by sandy on 2013-03-12
Thanks for replying I found the solution I was looking for if it helps anyone else here is a link to the online article I found:

[http://nullcore.wordpress.com/2011/12/09/setting-the-system-hostname-from-dhcp-in-ubuntu-11-10/](http://nullcore.wordpress.com/2011/12/09/setting-the-system-hostname-from-dhcp-in-ubuntu-11-10/)

I am installing 12.10 and it worked for me.

My DHCP server will hand out an IP address along with the Hostname of the PCs I am connecting to my network.

Regards,

Sandy

---

