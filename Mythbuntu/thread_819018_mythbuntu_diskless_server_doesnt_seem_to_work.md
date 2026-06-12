---
title: "mythbuntu diskless server doesnt seem to work"
date: 2008-06-05
forum: Mythbuntu
---

### Post by kainalu on 2008-06-05
Hi,


I have mythbuntu installed, but i cant get the diskless server to work. I went to the roles option in the control center, clicked on the dhcp and the diskless server icons, applied, and then built the image on the appropriate tab and rebooted the box. my 2 other machined cannot boot the pxe image, they say no boot file is sent to them. They dont seem to see the server at all. i can boot these two machines off a knoppix terminalserver just fine

anyone have this issue?

---

### Post by laga on 2008-06-05
Well, for starters:

Can you post some information:
* /etc/ltsp/dhcpd.conf
* /etc/inetd.conf
* relevant messages from tftp and dhcp in /var/log/daemon.log and maybe from /var/log/messages
* the output of 'find /var/lib/tftpboot/ltsp/' and 'ls -al /opt/ltsp/images'

Also, it'd be good to know the exact message your client gives you when you try to boot it.

---

### Post by kainalu on 2008-06-05
hmmmm..... no /etc/ltsp/dhcpd.conf on my server

output of inetd.conf:

cat /etc/inetd.conf 
2000               stream  tcp            nowait  nobody /usr/sbin/tcpd /usr/sbin/nbdrootd /opt/ltsp/images/i386.img


output of dhcp, the ltsp isnt in there:

Jun  5 08:46:16 myth dhcpd: Internet Systems Consortium DHCP Server V3.0.6
Jun  5 08:46:16 myth dhcpd: Copyright 2004-2007 Internet Systems Consortium.
Jun  5 08:46:16 myth dhcpd: All rights reserved.
Jun  5 08:46:16 myth dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)




 find /var/lib/tftpboot/ltsp/
/var/lib/tftpboot/ltsp/
/var/lib/tftpboot/ltsp/i386
/var/lib/tftpboot/ltsp/i386/abi-2.6.24-18-generic
/var/lib/tftpboot/ltsp/i386/pxelinux.0
/var/lib/tftpboot/ltsp/i386/initrd.img-2.6.24-18-generic
/var/lib/tftpboot/ltsp/i386/initrd.img-2.6.24-18-generic.bak
/var/lib/tftpboot/ltsp/i386/pxelinux.cfg
/var/lib/tftpboot/ltsp/i386/pxelinux.cfg/default
/var/lib/tftpboot/ltsp/i386/initrd.img
/var/lib/tftpboot/ltsp/i386/config-2.6.24-18-generic
/var/lib/tftpboot/ltsp/i386/vmlinuz
/var/lib/tftpboot/ltsp/i386/nbi.img
/var/lib/tftpboot/ltsp/i386/System.map-2.6.24-18-generic
/var/lib/tftpboot/ltsp/i386/nbi.img-2.6.24-18-generic
/var/lib/tftpboot/ltsp/i386/vmlinuz-2.6.24-18-generic

ls -al /opt/ltsp/images
total 429632
drwxr-xr-x 2 root root      4096 2008-06-04 23:39 .
drwxr-xr-x 4 root root      4096 2008-06-04 23:03 ..
-rwxr--r-- 1 root root 439500800 2008-06-04 23:39 i386.img

---

### Post by laga on 2008-06-05
Well, that looks like a bug :(

For now, you can copy /usr/share/doc/ltsp-server/examples/dhcpd.conf to /etc/ltsp/dhcpd.conf and edit it to suit your setup. Afterwards, you can sudo /etc/init.d/dhcp3-server restart.

---

### Post by kainalu on 2008-06-05
ok ill try but i have no clue how to use the file or how to set it up, so ill read about to find out how, ill let you know how it goes.... thanks!

---

### Post by laga on 2008-06-06
Basically, if your network is 192.168.0.0/24, then you'll be fine. If it's like 192.168.1.0/24, then you'd simply run sudo ```
sed -i -e 's/192.168.0/192.168.1/g' /etc/ltsp/dhcpd.conf
```. Of course, adjust the first value in the sed expression for your environment :)

---

