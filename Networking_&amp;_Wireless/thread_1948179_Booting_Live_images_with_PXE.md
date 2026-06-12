---
title: "Booting Live images with PXE"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by inclusivedisjunction on 2012-03-27
I've recently started experimenting with booting/installing over a network using PXE and a TFTP server (I use my router as the DHCP server). Overall, it is working fine, but when I boot recent Live images, the desktops are unable to access the internet. This occurs using the 11.10 and 12.04 beta images of Ubuntu, Kubuntu and Xubuntu, but not with 11.04, and it does not occur when booting the alternate install (text-mode) versions of these distros. 

My question is thus: Is there a parameter I'm missing that is needed to allow more recent Live editions to access the internet? My PXELINUX menu entries for the Live versions look like this:

```
LABEL ubuntulive
     MENU LABEL Ubuntu 64-bit (Live)
     KERNEL ubuntulive/casper/vmlinuz
     INITRD ubuntulive/casper/initrd.lz
     APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.11.2:/home/test/tftpboot/ubuntulive  quiet splash

LABEL ubuntulive32
     MENU LABEL Ubuntu 32-bit (Live)
     KERNEL ubuntulive32/casper/vmlinuz
     INITRD ubuntulive32/casper/initrd.lz
     APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.11.2:/home/test/tftpboot/ubuntulive32  quiet splash

LABEL kubuntulive
     MENU DEFAULT
     MENU LABEL Kubuntu 64-bit (Live)
     KERNEL kubuntulive/casper/vmlinuz
     INITRD kubuntulive/casper/initrd.lz
     APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.11.2:/home/test/tftpboot/kubuntulive quiet splash

LABEL xubuntulive
     MENU LABEL Xubuntu 32-bit (Live)
     KERNEL xubuntulive/casper/vmlinuz
     INITRD xubuntulive/casper/initrd.lz
     APPEND root=/dev/nfs boot=casper netboot=nfs nfsroot=192.168.11.2:/home/test/tftpboot/xubuntulive  quiet splash

```

The Kubuntu entry above works as it is using files from an 11.04 disc.

---

### Post by shiman6 on 2012-07-25
What i found to get internet on a PXE boot server setup, my server has two interfaces, one on the internal or PXE network, with its own DHCP, NFS, and TFTP server, and the other interface hooked up to the internet. Manually set your internal interface to a static IP address, and your external interface to just dhcp, or automatic.  Edit your DHCP server so that it gives external DNS servers,  then set up a NAT translator.

For some odd reason, i cannot find the tutorial i have used. It was really simple and it works well. Anyway, do some googling. I do remember that it uses IPtables.

---

### Post by xicarusx on 2012-12-06
The problem is in the upstart of the init script. The way to get around it is pretty simple, but annoying.

open a terminal
sudo nano /etc/network/interfaces
Change the line “iface eth0 inet manual” to “iface eth0 inet dhcp”
press CTRL-X
press y
press enter
then run 
sudo /etc/init.d/networking restart

The reason this is annoying, is because the changes WILL NOT STAY, and you have to do it every single time.

---

