---
title: "Shares Access problem with Windows 2003 Server"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by anspectrum on 2013-05-07
Client is Ubuntu 12.04 (32-bit)

Server is Windows 2003 (32-bit with Active Directory)

Connect Method: Places------Connect to Server ---------Selecting Windows Share Service and filling in appropriate values

Also smbclient command has been tested with same results.

Problem: While trying to connect Server from Ubuntu machine Username / Password prompt keeps popping up. Though other Windows (non-server) machines are accessible without any problem.


Diagnosis and Troubleshooting: I used Wireshark to capture actual traffic and see the messages being passed from Ubuntu to Server back and forth. Here's the crux of the matter. ***When I use Windows client to connect to the server then Domain is passed as NULL (No value is passed) and username is passed as "Someuser@Somedomain.com" and Server's shares are accessed. However, I failed to pass these parameters to the server while using Ubuntu client either through "Connect to Server" GUI or through smbclient command***.

Can someone guide, how to do it..???

---

### Post by SeijiSensei on 2013-05-07
Try logging in with "DOMAIN/username" as the user, where DOMAIN is the MS domain the AD server is responsible for.  That may help.

---

### Post by anspectrum on 2013-05-07
> **SeijiSensei said:**
> Try logging in with "DOMAIN/username" as the user, where DOMAIN is the MS domain the AD server is responsible for.  That may help.


Will try it. However, what about the domain value being passed as NULL while accessing through Windows. If I give the username as you have said, what would be the Domain value. If I leave it blank it is automatically parsed by WORKGROUP.

---

### Post by anspectrum on 2013-05-08
Ok. Some interesting results.

This command helped right away

smbclient -U some.user -W some.domain //serverip/sharename    (I wonder what was wrong earlier)

Secondly using "Connect to server" GUI option also worked out once I noticed (using Wireshark) that smbclient command (mentioned above) sends domain in capital letter (yeah, thats really odd 'cause I type it in small letters). Moreover, as mentioned in my first post that Windows clients can access the machine without any problem and in that case domain is sent (checked via wireshark) in small letters.

Anywho, I tried capital letters and Wola, Windows 2003 server shares were successfully accessed.

I'm gonna mark this thread as solved, but would like to know if I diagnosed and solved it correctly or is there something that I'm missing.

Cheers.

---

