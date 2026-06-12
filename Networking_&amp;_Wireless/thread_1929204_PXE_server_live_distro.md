---
title: "PXE server live distro?"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by alexan on 2012-02-21
Does exist such thing?
Basically I need a minimal distro capable (to put on usb) of running a PXE server so I can use any PC in a network to install other distro.



I DO NOT WANT a distro capable to *boot* on pxe server; but THAT IS a pxe server (bonus point if it come with a graphical DM and network-manager: so I can directly download live iso and install on other machines "on fly")

---

### Post by Perkins on 2012-02-21
There are a number of ways you could do this, especially since you're planning to put it on a thumb drive anyway.  The simplest would likely be to use the Ubuntu alternate installer and tell it to install an LTSP setup.  That will have all of the DHCP, PXE, and TFTP stuff configured.  Then all you'd have to do would be to add whatever images you wanted to be able to boot.  The documentation is fairly comprehensive, and not too complicated.


If you want a bit more control, use DRBL.  Its not built into Ubuntu, but doesn't pester you with any of the terminal server stuff.  Its installer is pretty well automagic, and it comes bundled with a couple of useful utility images (like clonezilla), along with instructions for adding your own and setting which machines get which images.  I have a copy I carry around on a portable hard drive for imaging machines.

---

