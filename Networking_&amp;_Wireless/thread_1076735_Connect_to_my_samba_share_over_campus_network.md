---
title: "Connect to my samba share over campus network"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by cchase88 on 2009-02-21
I have setup a network share on my computer and would like to access it from across my campus. I am able to access it from other computers in my dorm, but not from outside.

When I ping my computer from another location on campus, it is successful. However, I am unable to connect to it as if it was a workgroup computer. I tried looking for ways of mapping a network drive in windows using only my ip address, but had no luck.

I would like to know if it is possible to somehow do a lookup on my computer and find the full network path so I could enter this in windows and connect to my folder.


In summary:

-I am able to successfully ping my computer from anywhere on campus.

-If I were to browse the networked computers from a different dorm on campus, the only computers that would be listed are the computers in that dorm.

-If I am able to ping my computer, this leads me to think that I can somehow connect to my computer and access my shared folder.

---

### Post by capscrew on 2009-02-21
I don't think you will be successful at connecting over a WAN connection with the protocol SMB (Samba).  Samba is really a LAN (local) protocol.  The TCP/UDP ports are known security risks and are blocked on most networks.

Ping is another protocol (e.g ICMP) and is not blocked as a general rule.  Being able to ping your computer does not always mean you can connect via another protocol.

---

### Post by cchase88 on 2009-02-22
Hmm.. so the best way to access my files would be to allow myself ssh access to my machine?

---

### Post by capscrew on 2009-02-22
Yep.  But you can do more than you think with ssh.  

You can use sFTP or scp to access the files through the ssh tunnel.  If you have a Windows hosts you can use WinSCP for both sFTP and scp.  I have remote clients that use WinSCP for sFTP.

Here is a good place to start with SSH SCP and sFTP for Ubuntu:
[https://help.ubuntu.com/community/SSHHowto]("https://help.ubuntu.com/community/SSHHowto")

---

### Post by cchase88 on 2009-02-23
Thanks, I'll be sure to read over that.

The only problem I have with using SSH and SFTP is that I would have to transfer the files onto the computer I would be accessing from. I'm more interested in being able to play my music from anywhere without having to download it.

---

### Post by capscrew on 2009-02-23
I would look for a player you can use with the ssh tunnel, or better yet, mount the remote directory to your local host via ssh.

See here for a good starting point for sshfs:
[http://www.google.com/search?hl=en&q=mount+remote+directories+ssh&btnG=Search]("http://www.google.com/search?hl=en&q=mount+remote+directories+ssh&btnG=Search")

---

