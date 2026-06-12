---
title: "Can't ping computers on local network"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by nothing42 on 2009-11-05
I just moved from an 8.10 to a fresh 9.10 install and can no longer ping computers on my local active directory network.  It seems like all the samba pieces are working correctly, every PC on the domain shows up when i go to browse the network through nautilus.  

Before I could just ping 'pcname.domainname.local' and it would work, I could also connect to rdp sessions this same way.  Any idea what setting I'm missing to get this to work?  I don't remember having to do anything specific before to get this working.  Usually once I configured samba everything worked fine.

Thanks for any help.

-- I remembered what the deal was.  I had to move 'dns' and add 'wins' right after 'files' in the /etc/nsswitch.conf file.

---

