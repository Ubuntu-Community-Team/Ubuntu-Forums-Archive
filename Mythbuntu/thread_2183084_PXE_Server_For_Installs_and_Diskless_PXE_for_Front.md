---
title: "PXE Server For Installs and Diskless PXE for Frontend?"
date: 2013-10-23
forum: Mythbuntu
---

### Post by TheFuzz4 on 2013-10-23
Hey Everyone,

So I followed this guide [https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro) to setup a PXE server at home so I can install VMs and other machines via PXE instead of USB or whatever (also because I wanted to build a PXE server for just because).  I've known for a while that you can run a frontend diskless I just wasn't entirely sure as to how to do this.  Is it possible to setup the PXE server for installing new machines but using syslinux like the other site talks about to have your front ends run diskless and get the PXE image they need based off of MAC address?

```

SYSLINUX
The SYSLINUX Project is a suite of lightweight boot-loaders, for starting up computers with the Linux kernel. It is the work of H. Peter Anvin, and consists of several separate systems, the best-known of which is ISOLINUX.

The PXELINUX bootstrap will be installed when syslinux is installed.

PXELINUX is used in conjunction with a PXE compliant ROM on a network card. The PXE environment uses DHCP or BOOTP to enable basic TCP/IP networking, then downloads a bootstrap program via TFTP. This bootstrap program loads and configures a kernel according to directives that are also downloaded from the TFTP server.

Typically, PXELINUX is used for Linux installations from a central network server or for booting disk-less workstations.

Install SYSLINUX.


sudo apt-get -y install syslinux
Copy the PXELINUX bootstrap to the root of our TFTP server.


sudo cp /usr/lib/syslinux/pxelinux.0 /var/lib/tftpboot
Configuration files for PXELINUX reside in directory /var/lib/tftpboot/pxelinux.cfg/. PXELINUX uses the following method to search for the appropriate configuration file:

The hardware type (using its ARP type code) and address, all in lower case hexadecimal with dash separators; for example, for an Ethernet (ARP type 1) with address 88:99:AA:BB:CC:DD it would search for the file-name 01-88-99-aa-bb-cc-dd.

The client IP address in upper case hexadecimal, e.g. 192.0.2.91 -> C000025B

Continousosly remove one hex digit from the hexadecimal IP address
A file named default
As an example, if the boot file name is pxelinux.0, the Ethernet MAC address is 88:99:AA:BB:CC:DD and the IP address 192.0.2.91, it will try following the files:

/var/lib/tftpboot/pxelinux.cfg/01-88-99-aa-bb-cc-dd
/var/lib/tftpboot/pxelinux.cfg/C000025B
/var/lib/tftpboot/pxelinux.cfg/C000025
/var/lib/tftpboot/pxelinux.cfg/C00002
/var/lib/tftpboot/pxelinux.cfg/C0000
/var/lib/tftpboot/pxelinux.cfg/C000
/var/lib/tftpboot/pxelinux.cfg/C00
/var/lib/tftpboot/pxelinux.cfg/C0
/var/lib/tftpboot/pxelinux.cfg/C
/var/lib/tftpboot/pxelinux.cfg/default

```

If so this would be awesome.  Since 2 of my front ends use AMD Video and the 3rd is Nvidia.  But I'd like to set them all up to be diskless.  Thank you in advance for your help with this.

---

### Post by newbie-user on 2013-10-23
For diskless workstations, you need to install an LTSP server. [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

---

### Post by uteck on 2013-10-26
Yes, you can set it so a system boots an image based off its MAC.  You make a PXE config file to boot just the image you want and name it after the MAC, but with a '-', like 01-88-aa-bb-cc-dd. 
The PXE protocol will look for a config based on the MAC, then versions of the MAC, then use the default config.

---

