---
title: "What do I do after I confirm &quot;ping&quot; between comps"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by TeachThai on 2009-05-09
I have been able to confirm that I am able to "ping" between the two computers that I am trying to network.  My question is this: What do I do next?

 Unable to set up network Xubuntu to Win XP
I have two computers (one running Windows XP and the other running recent install of Xubuntu 9.04). I can't set up the network between them although I had a good network between them when I had Windows 98SE connecting to the Windows XP computer.

One computer has AMD K6 processor - 118 Mb RAM - 6.0 Gb HD

Second computer has X86 Genuine Intel processor - 2393 Mhz - 512 Mb RAM - 28 Gb Free HD space

I have both computers connected to a router. The router is connected to my modem and I have Comcast connection to the modem. As stated above, in the past I didn't have any problems setting up and using the same home network using the same two computers, router connections, and modem.

I have two icons showing up in the top right part of the screen on the computer with Ubuntu 9.04 running on it. Right clicking on the icons reveals a balloon saying I have an active wired connection. Right clicking on the icon gives me stats about the connection such as interface number, hardware address, Broadcast address, subnet mask, default route, primary DNS, and Secondary DNS. I see that the router has given the Ubuntu running computer an IP address with one digit more than the Windows XP computer so I assume this has been assigned automatically by the router.

Using the Windows XP computer, I opened up the Windows XP network connection so I can see the name of the Windows XP based computer and the workgroup name on it.

When I opened up the "Remote Filesystems" (Gigolo) program on the Linux based computer, to set up the connection between the two computers I see that the program has not detected the Windows XP computer. I usually chose the Windows sharing option for the means of connecting. When I try typing in the Windows XP IP address and the folder path in the Windows XP computer the program says it can't find the shared folder. I think this is the point where I am not typing in the correct information in the right places in the program that is supposed to help me set up the network. I don't have much experience setting up networks because I have been able to do it easily in the past.

This is getting a bit frustrating because I have tried at least one other Linux distribution and also an Apple based laptop but I didn't have any trouble connecting to the Windows XP with those other operating systems although admittedly, I had more RAM in the laptop computers I have used in the past.

Thank you for any help you can provide.

---

### Post by Iowan on 2009-05-09
I recently installed Jaunty on a laptop, and had no connection to my Samba Server.  After installing Winbind and editing /etc/nsswitch.conf to include "wins" before "dns"... after a reboot, it could find the server.  I also edited smb.conf to insure my new Jaunty box was in the same workgroup.

---

