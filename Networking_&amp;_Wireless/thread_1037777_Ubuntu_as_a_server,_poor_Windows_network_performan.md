---
title: "Ubuntu as a server, poor Windows network performance"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by PryGuy on 2009-01-12
Good day everyone!
I have installed Ubuntu Feisty (not a server edition) for one of our clients and configured it as a gateway, they also have a Windows Server 2003 that has Terminal Services enabled and people connect to it remotely. So the entire scheme looks like this:
Windows Server 2003 > Ubuntu Gateway with DHCP > ADSL Modem.

Windows remote desktop users suffer very poor network performance, Thunderbird fails to download messages giving me timeout error. Ubuntu works fine and downloads everything well with Evolution. Windows Server configured with a static IP, Ubuntu clients are DHCP. Where's the problem and what's the root of this incompatibility?
Thanks in advance!

---

### Post by superprash2003 on 2009-01-12
could be a dhcp issue..try configuring opendns servers for your client.. 208.67.222.222 and 208.67.220.220`

---

### Post by PryGuy on 2009-01-12
@superprash2003: No, the DHCP clients under Ubuntu work fine! It's the Windows Server that is the pain, and it is configured statically. The worst thing is that the company uses PCs all the time, so I have to fight/wait for hours to reboot or change network interface params. Could there be MTU or some other Windows/Linux incompatibilities?

There's another thing I'm worried about, 'dmesg | grep "eth0"' says it's Realtek blah blah chip, it appears this is the one that caused troubles under Feisty. Sorry, I'm not on the spot to give you detailed info. Will write back as soon as I find out something. Bad chip is in my top 5 list so far.

---

