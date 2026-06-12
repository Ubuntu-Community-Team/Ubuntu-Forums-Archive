---
title: "making ubuntu to forget 802.1x authentication credentials on logout"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by shahab.fm on 2010-10-06
Hi guys.

We have some computers at university and we should use IEEE8021X authentication to login to our _wired_ network and get Internet access. I can use networkmanager and go to:

Edit Connection
Wired
Autho eth0 -> Edit
802.1x Security
Authentication : Protected EAP(PEAP)
inner authentication : MSCHAPv2
username = myusername
password = mypassowrd

If I write my username and password and click Apply, then the computer would login to network and there is no problem. BUT these computers are public computers for all students in student community and we would like Ubuntu to prompt a login window in case of new login. Our biggest problem is that now it remembers the password of last successful connection. 

Is there anyway that it forgets the previous authentication and ask again for username & Password ?

We tried wicd, but it won't give any auth-options for a wired conncetion.

Thanks in advance.

Shahab.

---

