---
title: "ltsp remote desktop"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by darkblack on 2009-08-20
I was scouring and searching everywhere regarding the ltsp project, but couldn't get clear answer for this question.

1) Is it possible for multiple users, simultaneously, be able to use their remote desktop client (in their windows or linux computers)and connect and work in a ltsp server, just like how they would do in a windows terminal server?

Each of the remote desktop users will have their own instances, desktop and home folders etc 

It is explicitly mentioned everywhere that multiple thin clients can boot out of a ltsp server, but the answer to my above question is no where clearly mentioned. 

2) Also if answer to question #1 is yes, then is it possible for install virtually (using vmware or similar) an windows xp instance in the lstp server, which each of the remote desktop users can also use?

Kindly let me know

Thanks a tonne!

---

### Post by darkblack on 2009-08-26
Any help on this? I hope i did not post this in the wrong section of the forum.

Basically i am looking for linux terminal server where multiple users can use remote desktop and login and use applications installed in the server. Any suggestions?

Thanks
Timothy

---

### Post by alapisco on 2009-10-09
I am actually looking for the same, Any luck yet?

---

### Post by lykwydchykyn on 2009-10-09
LTSP is not the same thing as Windows Terminal Services. LTSP is a system for booting thin clients to a desktop using a combination of network services (PXE, NFS, SSH, TFTP, etc).

If you want a setup where multiple windows users can remote into a Linux machine from their desktops, you probably want to look at NX ([www.nomachine.com](www.nomachine.com)), VNC, or XDMCP combined with a win32 X11 server.

AFAIK there is no RDP server for Linux, which is the only protocol windows remote desktop client supports.

To answer the OP's second question, AFAIK this can be done, though it'd require a substantial piece of hardware.  I don't think there's an "out of the box" solution for this sort of thing, but if you know a bit about X sessions and kvm/virtualbox/vmware commands, it should be doable.

---

