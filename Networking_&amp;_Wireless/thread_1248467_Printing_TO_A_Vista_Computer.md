---
title: "Printing TO A Vista Computer"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by artcarney on 2009-08-24
Hi all.

I'm tired of searching.

I'm running Kubuntu 9.04 on a laptop. I successfully set it up to print to my bluetooth printer (via bluetooth) that's connected to my MAC at home.

All my searching seems to find links for pages that help with sharing printers connected to Linux computers with Windows computers. I want to do the opposite.

I used to have my Linux laptop setup to print to my girlfriends HP PSC 2500 series printer through the wireless network but I forgot to save the config files when I did a fresh install of Kubuntu 9.04. Ooops!

Now I don't remember how to set it up. 

KDE doesn't have a browse function that I can find when setting up my printer. I'm trying to set it up via Samba. The config wants a smb address and I'm at a bit of a loss as to the correct format of this address. Everything I've tried has returned errors.

In a konsole the following:

```
smbclient -L //192.168.1.102
```

... returns ...

```
Domain=[J9JANSEN-PC] OS=[Windows Vista (TM) Home Premium 6001 Service Pack 1] Server=[Windows Vista (TM) Home Premium6.0]

        Sharename       Type      Comment
        ---------       ----      -------
        ADMIN$          Disk      Remote Admin
        C$              Disk      Default share
        D$              Disk      Default share
        HP psc 2500 Series on J9Jansen's PC Printer   HP psc 2500 Series
        IPC$            IPC       Remote IPC
        K$              Disk      Default share
        L$              Disk      Default share
        print$          Disk      Printer Drivers
        Quicken PDF Printer Printer   Quicken PDF Printer
        Send To OneNote 2007 Printer   Send To OneNote 2007
session request to 192.168.1.102 failed (Called name not present)
session request to 192 failed (Called name not present)
session request to *SMBSERVER failed (Called name not present)
NetBIOS over TCP disabled -- no workgroup available
```

Any help or links appreciated!

David

---

### Post by artcarney on 2009-08-24
I was able to solve it by installing Gnome's Printer Assistant (forgot the package name) and browsing.

This gave me the smb:// address of the network printer for KDE.

I also had to reboot the Vista machine after setting the printer for sharing ... go figure. :lolflag:

David

---

