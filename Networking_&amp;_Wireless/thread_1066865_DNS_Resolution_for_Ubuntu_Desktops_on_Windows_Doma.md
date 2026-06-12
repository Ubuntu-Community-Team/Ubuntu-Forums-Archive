---
title: "DNS Resolution for Ubuntu Desktops on Windows Domains"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by vahart on 2009-02-11
Hello All,

I am new Ubuntu and I have a question. We have many Ubuntu desktops running in VMs that use static ip addresses. Other than manually adding these machines to the DNS server as entries, is there a way to have these machines auto-register with the windows (AD) DNS server?

Where can I find any articles that resolve this issue.

Domain: Windows 2003
VM: VMWare ESX 3.5 and ESXi 3.5
Ubuntu 8.04LTS

Thanks!

-Vaughn

---

### Post by Fire_Chief on 2009-02-11
Hi Vaughn,

Unfortunately, because they are statically assigned and since Ubuntu does not integrate with Active Directory natively, the Ubuntu systems won't get registered in DNS automatically. This is assuming your DNS and DHCP servers are running on a Windows Server system. You will have to add the entries manually into DNS for the Ubuntu systems to be reachable by name.

You could look into using a third party software to integrate with AD (single sign-on) such as Likewise Open [http://www.likewise.com]("http://www.likewise.com"). It may resolve the issue but I am not certain of this.

Cheers!

---

