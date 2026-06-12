---
title: "Ubuntu to Windows 2003 Share Folder Access"
date: 2011-02-19
forum: Networking &amp; Wireless
---

### Post by caseclosed on 2011-02-19
Hello.  Ubuntu 10.10.  I am using Likewise to join a Server 2003 AD.  I can access shared folders within the domain using SMB and entering a user/pw.  Let me use example smb://server2003/data.  I can see everything.  Step two: I have a Windows-based database program that writes files to one of those shared folders.  It is not used as a terminal service, just a storage space for the data and the program resides on the local hard drive.  I've used Wine to install the program and it loads fine.  The interface loads a login window that displays the server path.  Here is where it gets tricky.  The program displays a 'server path' as //server2003/data but also displays the message 'invalid server directory'.  I can ping the server and even access the server just fine using the above-mentioned avenues.  I tried replacing it with smb://server2003/data but since this isn't nautilus, and is instead a native MS program, that fails.  I tried //192.***.*.*/data where * = its the IP address, but that also fails.

I have the AD server also acting as DNS and DHCP functionality.  Everything is a static IP.

My questions are really about how the // string in windows and how this translates to Ubuntu.  For all I know this is just a syntax error on my part.  Any help is appreciated.

---

