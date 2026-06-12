---
title: "Remote Desktop Access Refused"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by kerrydeare on 2010-02-17
I have 4 boxes on a local network: 2 with XP only, 1 with Ubuntu 9.10 only, and 1 with both. All boxes can share folders, set up with share-admin instead of using Nautilus right-click properties for each folder.  I can see and control the remote desktops on all boxes, to all other boxes, from all other boxes,with one exception: I can only access the XP desktop on the dual boot box, not the Ubuntu desktop. When I try I get: "Connection to host 192.168.1.102 was closed." I am refused access to the Ubuntu desktop in this manner from both the other Ubuntu machine, and from both XP machines.
 
My setups are basically plain vanilla with routine installs of Ubuntu 9.10. On the XP machines I am using TightVNC on the XP machines to view both other XP desktops, and the Ubuntu desktop that is accessible. On both Ubuntu setups I am using (I suppose) vino and vinagre, and have completely re-installed what I think is the relevant software. There is no firewall running on the Ubuntu dual boot, when I check ufw.
 
For reasons I cannot determine the inaccessible Ubuntu desktop is not providing its own address but instead in the Remote Desktop config dialogue it identifies itself as 27.0.0.1 which I think is the loopback id.
 
I know so little about this sort of networking that I am not giving all relevant info, but I still thought I'd try. Thanks.

---

### Post by kerrydeare on 2010-02-19
By editing gconf/gnome/desktop/remote access and eliminating listening only to "lo" I can now access the desktop from all boxes.

---

