---
title: "Solved wireless and printers"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by amurphy96822 on 2009-04-24
HI:  hope this might help someone; was having a terrible time trying to connect the usual way (DHCP) with my Intel Pro 3945 ABG. Finally found this solution and hope it helps others: tried all kinds of DHCP solutions, tried change location of router, changed the range of IPs, etc.  All not work.  Finally changed to a static IP outside of the range (i.e. 192.168.1.220 where range is ...200-210).  Then I went to /etc/boot/ and edited menu.lst to add "pci=noacpi" at the end of the line,i.e after "splash"; now everything works fine.  

As far as my remote HP printer, I find the gui tool only works if I do it this way; go to add remote printer, choose ipp (samba does not recognize my remote server, at least in the smb browser that is included). Then for host, I used the IP, i.e. 192.168.1.201 instead of Main2, then I was able to see and select my printer and it worked fine. 

Hope this helps someone.  Aloha

---

