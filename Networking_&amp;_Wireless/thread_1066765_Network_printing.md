---
title: "Network printing"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by relambert on 2009-02-11
I've got two computers on a home network. One is a dual boot with Windows XP Pro and Hardy. The other has Hardy only. I've got an HP deskjet 5550 connected to the one with Windows. The problem I'm having is sharing the printer. I've set up samba, the computers will see each other on the network, and I've been able to add the printer to the networked pc, (two copies, one for when the host is in Windows, and the other if the host is running Linux). If the dual boot machine is running Windows, I can print without a problem from the networked pc. If it is running Linux, the networked pc will not print. The computer with the printer connected to it is able to print from both operating systems. Any ideas?

---

### Post by b4k4 on 2009-02-11
if you visit localhost:631 on the print server, or ip-of-print-server:631 from the client, what does it tell you about the printer?

do you get any clues from /var/log/cups/error_log

---

### Post by superprash2003 on 2009-02-11
have you shared your printer via samba??
 For reference : [http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html](http://www.prash-babu.com/2008/05/how-to-setup-network-printer-or-share.html)

---

### Post by relambert on 2009-02-11
Here is a screen shot of what comes up in localhost:631 on client pc. Deskjet 55502 is the printer that won't print. The other is the Windows pc, (as you can probably see). The host machine is running Ubuntu while this screen shot is taken.  I've been through superprash2003's tutorials a couple of times. They helped me get network operating correctly, but printer still won't work.
This is what came up in the error log when I tried to print.

E [11/Feb/2009:18:35:34 -0600] [Job 12] No %%BoundingBox: comment in header!
E [11/Feb/2009:18:35:36 -0600] [Job 12] No ticket cache found for userid=0
E [11/Feb/2009:18:35:36 -0600] [Job 12] Can not get the ticket cache for root
E [11/Feb/2009:18:35:38 -0600] [Job 12] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [11/Feb/2009:18:35:38 -0600] [Job 12] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [11/Feb/2009:18:35:38 -0600] [Job 12] Unable to connect to CIFS host, will retry in 60 seconds...

I also cannot save files in a shared folder on host pc from client pc. Can see contents, but cannot save files to folder.

---

### Post by relambert on 2009-02-23
Have recently upgraded both computers to Intrepid. After doing so, printing issue is corrected. Got the option to change the version,( I guess? ), of samba that was installed when the upgrade was performed. Maybe that did the trick.

---

