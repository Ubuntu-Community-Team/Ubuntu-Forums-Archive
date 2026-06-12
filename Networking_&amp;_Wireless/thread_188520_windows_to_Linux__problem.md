---
title: "windows to Linux  problem"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by xanthorrhea on 2006-06-04
Hi all
  I have a   small  windows  domain  controlled  by  Windows  Small Business  Server 2003 which works  nicely, except for  a  Notebook  running  Ubuntu.
Problem  is ,  it can  access all  windows  machines  including the  server  by  using a domain  username  and  password [ as  is  usual  in a domain]. However no one can  access  the  shares  on the  Ubuntu  Notebook from  the  Windows  machines.
I have tried adding  a user  in  Ubunto  that reflects a user  in the  domain,  no  luck,  Is this achievable  ? if  so , how do I set it up.

rgds
Roberto

---

### Post by Thenotsowyzewun on 2006-07-14
Click on System, Shared Folders and check each of your shares is configured correctly (within the "General Windows Settings" section).
If this is all ok, open a new terminal and type in sudo smbpasswd [username], it'll prompt you to enter a password to use for networking with that username (you can configure it the same if you like).
Also, to reconfigure the ubuntu machine's network name go into network settings and click on the general tab (this is also where you add it to a domain).

Works for me (but then I'm using workgroups not domains), hope that helps :) (I'm no guru tho!).

---

