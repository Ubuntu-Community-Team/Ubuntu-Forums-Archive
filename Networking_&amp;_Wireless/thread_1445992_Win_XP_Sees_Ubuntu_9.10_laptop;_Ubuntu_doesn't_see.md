---
title: "Win XP Sees Ubuntu 9.10 laptop; Ubuntu doesn't see XP machine"
date: 2010-04-03
forum: Networking &amp; Wireless
---

### Post by tshaffer on 2010-04-03
I have a windows XP machine connected via wired connection to a Liksys Wireless router, then to a cable modem. I also have a Laptop on which I have recently installed Ubuntu 9.10. 
The Laptop is able to connect to the internet wirelessly through the router. I have also, finally been able to get the XP Desktop to see the Ubuntu Laptop, but when I go into Places/Network and click the "Windows Network" I get the error message "Unable to Mount location. Failed to Retrieve share list from server". How do I tell Ubuntu/Samba how to connect to the Windows machine?  I tried setting the workgroup in smb.conf. Apparently I'm doing something right, since the Windows Machine can see the Laptop... I just need to figure out the part I'm not doing right. I tried searching the forum,but none of the posts I found seem to really address my exact problem. I'm new to Linux, although I have had several years of UNIX admin experience... A LONG TIME AGO :-) I appreciate any assistance you can provide.

Thanks in advance

_Update: I just noticed that the Windows machine is able to see the Ubuntu laptop as an Internet place under "My Network Places" Not as a "Local Network" System. Not that I care how they see each other as long as they can :-) Thanks again._

---

### Post by Iowan on 2010-04-04
I've had better luck using the "Connect to Server" option - but that has it's own complications - you need to know server name and path to share.

---

