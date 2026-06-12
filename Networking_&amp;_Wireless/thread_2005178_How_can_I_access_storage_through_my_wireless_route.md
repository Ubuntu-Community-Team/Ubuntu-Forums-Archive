---
title: "How can I access storage through my wireless router?"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by ambient007 on 2012-06-17
My laptop, running Ubuntu 12.04 & WinXP, is connect though wifi to a logitec router (the model of which might only be available here in Japan).
The internet connection is fine and I can get into the router interface through 192.168.2.1

The router has a USB port and I'm pretty sure it can act as a host to the USB device.  This shows up in the router interface with the harddrive connected:

[IMG]http://i1147.photobucket.com/albums/o560/MySoapbox/Internetting/Screenshotfrom2012-06-17164800.png[/IMG]

How can I access this? 

I don't know how to mount it so I can browse/use/edit the files.

Once I get this sorted, I also wanna try and access the drives of other devices connected to the network - an windows laptop and 1 or 2 android phones.

I'm assuming this is all possible, but I have no idea how - I'm still somewhat of a n00b.

Help?

---

### Post by ambient007 on 2012-06-17
Bump...

Anything? Nothing?

I'll settle for being able to access the harddrive of the windows laptop that's connected via ethernet to the same router if I can't get the USB drive to work.

---

### Post by steeldriver on 2012-06-17
Well I have a similar feature on my Netgear router, I imagine all these consumer grade devices are pretty much the same

Once enabled in the router web admin page, it is likely exported as a CIFS (Samba) share - so for example on your XP machine it should appear in 'Network places' (provided you set the workgroups the same)

On the Ubuntu machine, with client-side Samba services installed, you should be able to poll the router for its share list, e.g.

```
$ smbclient -L wndr3800.local
Enter steeldriver's password: 
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

    Sharename       Type      Comment
    ---------       ----      -------
    IPC$            IPC       IPC Service (NETGEAR WNDR3800)
    USB1            Disk      
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.24]

    Server               Comment
    ---------            -------
    READYSHARE           NETGEAR WNDR3800

    Workgroup            Master
    ---------            -------
    MSHOME               

```and I can access it in the (thunar) file manager as smb://wndr3800.local/usb1/

Hope this gets you started - you will need to look into your router's docs for complete instructions on how to enable the share and set the workgroup.

---

