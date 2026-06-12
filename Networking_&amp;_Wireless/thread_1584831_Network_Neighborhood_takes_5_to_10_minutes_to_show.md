---
title: "Network Neighborhood takes 5 to 10 minutes to show computers in network"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by norland on 2010-09-29
Is that normal for Ubuntu Linux to take 5 to 10 minutes for computers to show up in the Windows Network Neighborhood in Nautilus after startup.  It also takes 5 to 10 minutes to show Samba shares on my windows computer using NetBios (not however by entering ip).  Is there a lag because of a set time of netbios network broadcasts to exchange netbios information to resolve by WINS.  Is there any way this can be sped up so I can use my network immediately?  Is there any way to force these broadcasts?

---

### Post by capscrew on 2010-09-29
> **norland said:**
> Is that normal for Ubuntu Linux to take 5 to 10 minutes for computers to show up in the Windows Network Neighborhood in Nautilus after startup?
It can be normal.> 
It also takes 5 to 10 minutes to show Samba shares on my windows computer using NetBios (not however by entering ip).  Is there a lag because of a set time of netbios network broadcasts to exchange netbios information to resolve by WINS?
Usually it is due the the host that is working as the **master Browser** has been turned off.  It can take 10-15 minutes to go through the election amongst the still operating hosts to elect a new master browser. 

WINS is a name server for NetBIOS names, but it does not directly impact *network browsing*.  The browse operation is a distinctly different operation.>  

Is there any way this can be sped up so I can use my network immediately?  Is there any way to force these broadcasts?
The correct way manage the browsing is to manage which host is designated as the maser browser.  This can be any host, but it should be a host that is (for the most part) up all the time.  This can be a server that you have up or a desktop that is running most of the day.

See [**_here _**]("http://www.google.com/search?q=designating+a+master+browser&btnG=Go!")for ideas.

---

