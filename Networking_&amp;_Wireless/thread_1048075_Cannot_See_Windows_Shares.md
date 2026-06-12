---
title: "Cannot See Windows Shares"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by rwfnetworking on 2009-01-23
I have seen this posted before, but no real resolve as of yet. I'm running Ubuntu 8.10 Using Nautilus via Places|Network, I see my server and all workstations, but no shares are ever visible on any of them. And yes, I can connect with smbclient command. Seems to possibly be a Nautilus issue as I can get Dolfin and Krusader to connect ok as well as SMB4k. Any ideas on getting things to work correctly? 


Robert

---

### Post by Kobalt on 2009-01-23
Can you connect to the shares using the Places > Connect to server panel ? I know I can't see the shares on my enterprise network but I connect to them this way (I've created a bookmark for quick access).

---

### Post by superprash2003 on 2009-01-23
try connecting to them this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

---

### Post by rwfnetworking on 2009-01-23
> **Kobalt said:**
> Can you connect to the shares using the Places > Connect to server panel ? I know I can't see the shares on my enterprise network but I connect to them this way (I've created a bookmark for quick access).

Yes, I can do it that way. Sort of annoying that I cannot use the Networking option as it is intended.  Like I mentioned, it seems to be an issue with Nautilus. Although I can see my Server and all workstations, it displays no shares. Even if I type smb://x.x.x.x. Looks like it just doesn't get to the point of requesting authentication. I can use other file managers just fine.


Robert

---

### Post by rwfnetworking on 2009-01-23
> **superprash2003 said:**
> try connecting to them this way [http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html](http://www.prash-babu.com/2008/09/how-to-access-windows-shared-folders-in.html)

That is the same steps you do any normally, the problem is it never  requests authentication and just displays an empty window although there are like 15 shares on my server. I can display the shares in other file managers though. And also in a terminal my using smbfs/cifs...


Robert

---

### Post by rwfnetworking on 2009-03-06
This has now been addressed by updates that were released around hte end of February. Isue now resolved. Message me if you want to know my Samba config. Running Windows 2003 as my file server and Ubuntu 8.10 on my Laptop


Robert

---

