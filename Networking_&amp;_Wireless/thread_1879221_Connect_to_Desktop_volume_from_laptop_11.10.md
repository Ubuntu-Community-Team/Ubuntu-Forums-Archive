---
title: "Connect to Desktop volume from laptop 11.10"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by TriumphGuru on 2011-11-11
I have a desktop PC running Ubuntu 10.10 with a mounted volume called "ServerData".
Until earlier this week, my laptop was also running 10.10, and I was able to connect to a shared directory on ServerData called "Work".  This had been set up through the dialog box "Connect To Server".  It had been bookmarked with login credentials, so I didn't need to use "Connect to Server" every time, only select "ServerData" from the "Places" menu.

This week, I rebuilt my laptop with 11.10, now I am unable to connect to "ServerData" to access the files on it.
I can ping the desktop PC, no problems, and I can print to the printer which is connected to the Desktop PC (the "Find Printer" function in the "Add Printer" dialog box worked perfectly when I put in the IP address of the Desktop PC.)
My wife's laptop (running 110.04, upgraded from 10.10, not rebuilt) continues to be able to access "ServerData".

Using the "Connect to Server" dialog box, choosing the likely options (SSH, FTP with login, and Windows Share) all fail, regardless of whether I put in the "server" name as servername, or its corresponding IP address.  Messages are "Failed to Connect" or "Failed to mount Windows share", depending upon option chosen.

Because I had a full backup of my Home directory, I was able to check in .local/share/gvfs-metadata to ensure that all fields were entered correctly and consistently with previous configuration.

I've searched the forums (both this one and others) but haven't found an answer that works.  Many questions related to linking between a MS-Windows computer and an Ubuntu one, and therefore proposed solutions around samba, with either smbfs or cifs.  Trying these didn't work.

Perhaps related, when I now click on "Browse Network", no other computers are listed.  It used to previously.

---

### Post by nothingspecial on 2011-11-11
Do you get any errors if you try to connect with a terminal.

```
ssh username@ip_address
```

Run that from the laptop and use your username and the ip address of the desktop.

---

### Post by TriumphGuru on 2011-11-11
Hi nothingspecial,

Thanks for giving some guidance so promptly.

Response to ssh command is:
ssh: connect to host 192.168.0.151 port 22: Connection refused

Don't know if it is worth mentioning, but all disks are formatted as ext3/ext4.

---

