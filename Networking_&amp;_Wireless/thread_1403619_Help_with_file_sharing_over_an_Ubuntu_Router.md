---
title: "Help with file sharing over an Ubuntu Router"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by buenit on 2010-02-10
Hello everyone, I have googled this particular issue can't seem to find anything on it! 
 
I'm running into an issues accessing files shared on a Windows Server 2003  machine through a Windows XP machine that is connected to the Ubuntu router(Ubuntu Server 9.10). Here is what I am getting- "cannot copy (filename)- the specified network name is no longer available".
 
The Ubuntu router is only connecting about 5 computers on a different subnet to our main subnet. Here's where this gets weird- I am able to access and transfer the files fine, if only one computer is doing it at a time. If I try and trasfer a file from the server to a desktop, it starts and appears to be transferring fine, but then if I go to another computer and try and access any shares on the server I get that error message. It's almost like only one XP machine at a time can access any shared files on the Windows Server at a time (through the Ubuntu router of course:P). We do not have any file sharing issues like this on our main subnet, only on the smaller subnet that is connected to the servers through the Ubuntu router.
 
Here's how I set up the router-
 
1.configured eth's, gw, and DNS
 
2. Ran the following commands-
 
echo 1 >/proc/sys/net/ipv4/ip_forward
 
iptables -A POSTROUTING -t nat -j MASQUERADE
[SIZE=2][/SIZE] 
[SIZE=2][/SIZE] 
[SIZE=2]I hope I included everything, but I'm sure I left some details out. Sorry about the long post, just wanted to try and include as much detail as I could. Please let me know if you need more information and thank you for your help! :D[/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

