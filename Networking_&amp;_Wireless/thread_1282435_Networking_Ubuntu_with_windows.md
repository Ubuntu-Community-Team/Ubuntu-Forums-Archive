---
title: "Networking Ubuntu with windows"
date: 2009-10-04
forum: Networking &amp; Wireless
---

### Post by skynet2060 on 2009-10-04
Hi everyone, I've been using ubuntu off and one, slowing migrating into it, and thus far, know little things here and there.

There is still a lot to learn and I am planning mastering the linux distribution shortly.
As for now my main focus is on networking. 

I have, 4 machines, 3 running vista and one running windows server 2008 ( very good server I might ad ). I'm want to network my ubuntu 9.04 system to the workgroup an use my linux system as the network control console. When i try to access my network from the network location in ubuntu, I see my workgroup name but unable to see my computers. I did some research on networking with ubuntu and windows based OSes and learned of a program call SAMBA.

After reading some articles, samba is a re-engineered version of SMB that runs on windows. This software is mainly used for windows servers or so it says. I need a software that will allow me to access my windows machines to access shared resources. 

Can anyone help?:guitar:

---

### Post by Iowan on 2009-10-04
Hopefully, [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To can solve some problems.

---

### Post by swerdna on 2009-10-04
Three quick things to look at first:
1: Check that the workgroup name in smb.conf matches the workgroup name on the windows boxes.
2: Change the "name resolve order" in smb.conf to match the windows default; viz: "bcast host lmhosts wins"
3: Test if Samba is allowed thru the firewall by turning it off and on and comparing performance.

This turns firewall off: sudo ufw disable
This turns it on: sudo ufw enable
This shows what's configured in it: sudo ufw status

FFI: [firewall]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")
FFI: [name resolve order]("http://ubuntu.swerdna.org/ubulanprimer.html#client")
FFI: [workgroup name]("http://ubuntu.swerdna.org/ubulanprimer.html#server")

---

### Post by ermeyers on 2009-10-04
In the GNOME DESKTOP, you have Places->Network and Places-Connect to Server, where you select Service Type "Windows share"

---

### Post by jward3010 on 2009-10-04
> **skynet2060 said:**
> windows server 2008 ( very good server I might ad )

I don't agree but however.

---

