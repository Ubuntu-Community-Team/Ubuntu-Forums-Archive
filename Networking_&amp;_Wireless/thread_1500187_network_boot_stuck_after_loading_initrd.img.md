---
title: "network boot stuck after loading initrd.img"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by gogapp on 2010-06-02
i have a problem with netboot of one of pc's.
I installed a LTSP version of 9.10 and now trying to boot my PC using this server. 
the first steps of net-booting work perfect, IP address is assigning and vmlinuz and initrd.img are loaded through tftp, but after that moment loading is stuck. the cursor is blinking and i see all pxe and tftp output on the screen, but booting never continues. 
I tried to boot virtual machine using this LTSP installation and everything was perfect, the client successfully loaded and was absolutely working. 
I am thinking about some hardware that is not supported in default LTSP installation, but how should i check this.
thanks.

---

### Post by gogapp on 2010-06-03
solved
I removed "quiet" and "splash" kernel options from /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default to make log visible during boot.
the problem with booting itself was with PCI bus init. So I solved it with adding "acpi=off" option to the /var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default file

---

