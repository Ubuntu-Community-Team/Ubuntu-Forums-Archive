---
title: "point me in the right direction please linux to a windows server"
date: 2006-06-30
forum: Networking &amp; Wireless
---

### Post by cleetis562002 on 2006-06-30
I am completely new to linux, but I am learning that I like it.  I am tired of Windows.  I am trying to connect to a shared server in my office.  I use a program called Atrex. it is a pos inventory control app.  its data is saved on our windows server. one other windows machine also needs access to the data.  my goal is to run the app in Wine and link it all the way back to the server.  i understand the basic workings of this process. I know i need to create a connection between my linux machinge and the data on the server.  then set up a link from Wine to the connection in linux via some kind of virtual drive letter.

I am having a problem with getting the right name of the path to the server thru linux.  I know i have to do it thru Samba, but I am unsure of which names and paths to type in.  

I'll deal with the wine part after i get an automatic on boot connection to the server.  the data is already on the server, i just need to setup linux to be able to read and write to and from the data

Could someone help me thru the process and or point me to the right place to figure out my setup

Thnx for the help
Kyle

---

### Post by hda on 2006-06-30
First, check if you have 'samba-common' installed.

Then, check if you can access your Windows shares. In Nautilus choose ```
Go->Network->'Windows Network'
```. If your Windows-Workgroup or Domain shows up, double click on it and it will show all computers offering SMB-(Windows-) Shares. When opening such a share Nautilus asks you for Username/Domain/Password for the share. If you enter it correctly you have access to your windows shares.

If that is working you can create a mountpoint for the share and add the following line to /etc/fstab:
```
//winserver/share /mnt/windata-d smbfs username=xxx,password=xxx 0 0
``` hth,
_hda_

---

