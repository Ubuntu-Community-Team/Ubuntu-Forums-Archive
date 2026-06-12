---
title: "Setting USERDNSDOMAIN and USERDOMAIN in Ubuntu"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by chiques on 2010-02-16
How do I set my system to log on to the domains 

USERDOMAIN

and 

USERDNSDOMAIN

like in Windows?


In Windows XP, if I open a command prompt and type in 'set', I get these parameters.

USERDNSDOMAIN=
USERDOMAIN=
USERNAME=

---

### Post by Fire_Chief on 2010-02-16
The easiest thing would probably be to install Likewise Open and use that to join your Windows AD domain. It can integrate your Windows domain logon into Ubuntu.

Install it via ```
sudo apt-get install likewise-open
```
or go to [http://likewise.com/products/likewise_open/index.php]("http://likewise.com/products/likewise_open/index.php")

Cheers!

---

### Post by chiques on 2010-02-16
cool, I'll definitley try that. 
Thanks!

---

### Post by chiques on 2010-02-17
Likewise didn't work. I guess I must be missing something.


> 
Resolving 'mydomain' failed. Check that the domain name is correctly entered. Also check that your DNS server is reachable, and that your system is configured to use DNS in nsswitch.


> 
Error code: CENTERROR_DOMAINJOIN_UNRESOLVED_DOMAIN_NAME (0x00080026)

Backtrace:
    main.c:297
    djmodule.c:210
    djfirewall.c:726
    djfirewall.c:652
    djfirewall.c:327




Any suggestions?

---

### Post by Fire_Chief on 2010-02-17
Do you have an Active Directory Domain setup on a Windows Server or is this more for name resolution aspects? It looks as if Likewise tried to connect to the domain named "mydomain" which is not a valid AD FQDN. Can you give more insight?

---

### Post by chiques on 2010-02-19
> **Fire_Chief said:**
> Do you have an Active Directory Domain setup on a Windows Server or is this more for name resolution aspects? It looks as if Likewise tried to connect to the domain named "mydomain" which is not a valid AD FQDN. Can you give more insight?


Hi Fire_Chief,

I do not know if our network is an "Active Directory Domain". Is there any way to check?

I do not know which one I need, 'Active Directory Domain' or 'name resolution'. Is there any way to diagnose this?

I substituded my wx.yz.com with 'mydomain' because I did not want to reveal it. I can assure you, my domain in the format wx.yz.com is valid because my Windows XP Pro machine on my desk is using that domain.

---

