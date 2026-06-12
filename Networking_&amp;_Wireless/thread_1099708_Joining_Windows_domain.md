---
title: "Joining Windows domain"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by keelingj on 2009-03-18
I'm having trouble joining my Ubuntu 8.10 laptop to a Windows 2003 Active Directory domain.  I'm using LikeWise (command line or graphical interface) and these instructions:

[http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/](http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/)

Whenever I try to connect to the domain (ies.local or ies0), Ubuntu fires back an error that it cannot resolve the Domain Controller name.  

I'm also having difficulty getting Ubuntu to use the domain controller for DNS.  Internet DNS works, but Ubuntu will not resolve local computer names unless I hardcode the search locations into /etc/resolv.conf.  Whenever I reboot the computer, resolv.conf is wiped out.  Samba is configured and can browse domain computers/shares just fine.

---

### Post by helgman on 2009-03-18
If you are using NetworkManager to manage your connection you might want to change the IPv4 settings on your connection (right click applet -> Edit connections ... -> [select your connection or create a new] -> change Method under IPv4 Settings to "Automatic (DHCP) addresses only -> set DNS server to the DNS-server in the Windows Domain (and set Search Domains if you want to).

Does it help?

Regards,
Helgman

---

### Post by keelingj on 2009-03-19
No, setting IPv4 address-only did not work.  Ubuntu does detect the DNS server and gateway properly when set to Automatic.  

Local computer name resolution does work when I hardcode ies.local as the search domain.  However, Likewise still can't find the domain controller when I use "ies.local", "ies0", or "10.10.10.5" as the domain.

---

### Post by helgman on 2009-03-19
OK ... this might be a silly question but, are you using the domain controller as DNS-server? If so, do you have all the records in the server (did you install DNS at the same time as you promoted the server DC)?

Regards,
Helgman

---

### Post by keelingj on 2009-03-23
Yes, the DC is also the DHCP/DNS server.  It forwards DNS requests for non-local computers.  Works just fine for Windows clients.

Ubuntu doesn't seem to have a place where I can set the Domain Controller or WINS server IP address.  Likewise can't find the domain, but Samba can file share with domain computers :confused:

---

### Post by helgman on 2009-03-24
You can set DNS-server in the file /etc/resolv.conf as you said above. My suggestion to use DHCP address-only and then set DNS manually should give you the ability to point to your DNS-server (DC) without it being changes every time you reboot ... but if the DHCP-server gives you the DNS-server, I don't really see the problem there ...

You could always try this on you Ubuntu machine to see if you can get hold of the record: [http://technet.microsoft.com/en-us/library/cc738991.aspx](http://technet.microsoft.com/en-us/library/cc738991.aspx)

Regards,
Helgman

---

