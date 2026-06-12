---
title: "Problem getting an NFS system ready for cluster"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by anshumax on 2010-10-06
Hello everyone,
OK so I read this guide to create a simple cluster using Ubuntu, NFS and an SSI software called Kerrighed. The guide is at: [https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide]("https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide")
This guide is pretty simple to follow but lacks a few details which needed to be mentioned to setup the system properly.
I basically have a laptop (HP Compaq 6730b with Intel Core2Duo P8600 2.4Ghz processor, 2GB RAM, 250GB HDD with Broadcom NetLink BCM5787M Gigabit Ethernet NIC, which has a dual-boot of Ubuntu 10.04 and Windows Vista) and a PC (Intel Core2Quad Q6600 2.4Ghz processor, 3GB RAM, 400GB WD HDD with Intel 82566DC-2 Gigabit Network NIC which has a dual-boot of Fedora 9 and Windows XP) which I want in a cluster for the time being; if it works, I'll put more machines into the cluster. The laptop is the server and head node, while the PC is the a node of the cluster. They are designated as kerrighedserver and kerrighednode1, respectively.

As given in the guide, I first installed a dhcp server and then after that I installed a TFTP server and the PXE bootloader.
Then I setup an NFS server to export the directory /nfsroot/kerrighed as mentioned in the guide. After that I installed a bootable filesystem on /nfsroot/kerrighed using [debootstrap]("http://wiki.debian.org/Debootstrap").
I also configured the NFS and DHCP servers as given in the guide. I managed to boot into this minimal ubuntu hardy system installed /nfsroot/kerrighed using the kernel of ubuntu 10.04(ie. I basicallty used the vmlinuz-2.6.32-25-generic and initrd.img-2.6.32-25-generic files of ubuntu 10.04 located in /boot for booting up the minimal hardy setup on /nfsroot/kerrighed using the PXE bootloader). I assume the NFS service is working fine because I'm able to view the contents of /nfsroot/kerrighed which is setup as / for the minimal hardy installation and I'm also able to ssh into kerrighednode1(ie. the PC). 
The problem arises when I build the kerrighed kernel. I follow the steps given in the guide and build a kerrighed kernel successfully. But when I PXE boot the kerrighed kernel I get the following error:
> Looking up port of RPC 100005/1 on 192.168.1.1
Portmap: server 191.168.1.1 not responding, timedout
Root-NFS: unable to get mountd port number from server, using default mount: Server 192.168.1.1 not responding, timed out
Root-NFS: Server returned error-5 while mounting /nfsroot/kerrighed
VFS: unable to mount root fs via NFS, tyring floppy.
VFS: Insert root floppy and press ENTER

Now the funny thing is that when I modify the /var/lib/tftpboot/pxelinux.cfg/default file and change it to 'KERNEL vmlinuz-2.6.32-25-generic' and 'initrd=initrd.img-2.6.32-25-generic', the system boots into the minimal hardy system, but when I change it back to 'KERNEL vmlinuz-2.6.20-krg', the above mentioned error comes.

Is it a problem with NFS? I cant seem to figure it out! Help!

---

