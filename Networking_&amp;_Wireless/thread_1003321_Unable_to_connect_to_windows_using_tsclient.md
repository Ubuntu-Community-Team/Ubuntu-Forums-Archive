---
title: "Unable to connect to windows using tsclient"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by bargi on 2008-12-06
Hi,

I am unable to connect to the windows system using tsclient.
The way I follow are:

1: I enter the computer name and try to connect but it give error that host not found.

2: Then I just enter the IP of windows system ,it take it with no error but after some display an error that connection time out.

Can anybody help me to solve this problem.

Thanks

---

### Post by jmoorse on 2008-12-07
It it a Vista / Server 2008 Terminal Server?  tsclient (to my knowledge) does not support the RDC 6.1 extensions needed for mutual computer authentication.

Try rdesktop, let me know how that works

---

### Post by jancelis on 2009-10-04
Tsclient can connect to Windows 2008 server (RDP6.1).
You should configure Terminal Server with  "Do not require Network Level Authentication" and "Client compatible" encryption

---

### Post by thefish123 on 2009-10-24
> **jancelis said:**
> Tsclient can connect to Windows 2008 server (RDP6.1).
You should configure Terminal Server with  "Do not require Network Level Authentication" and "Client compatible" encryptionI'm sorry but this is not a good suggestion for a business environment.  Your suggesting that we lower the security on a Windows Server (presumably a production server doing something important) so that we can connect from a Linux client.

No one would ever recommend lowering security settings on a Linux box so that a Windows client could connect to it.

The Linux client needs to get up to speed with the latest security enhancements.  In the meantime I would suggest running Windows XP inside VirtualBox and using the latest native Windows mstsc.exe from there.

I really love Linux.  I particularly appreciate the polished and professional appearance of Ubuntu.  But lowering the security on our Windows boxes so that our Linux boxes can talk to them is not a good option.

Just my two cents worth...

Best regards,
The Fish

---

