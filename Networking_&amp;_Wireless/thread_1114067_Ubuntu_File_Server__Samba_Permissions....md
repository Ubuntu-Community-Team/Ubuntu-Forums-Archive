---
title: "Ubuntu File Server / Samba Permissions..."
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by jcounsel on 2009-04-02
Hi:

We have 6 windows (4 Xp & 2 Vista) computers networked to use an Ubuntu 8.10 File Server (with xfce).

Everyone on the network can browse the Samba share (one folder divided into many folders) that contains about 19GB of data.

Everyone on the network can create files/folders on the Samba Share, access all folders on the Samba Share, read and write to each folder on the samba share, etc.

We use Time & Chaos (from chaossoftware.com) versions 6 (4 comps) and version 7 (2 comps) to coordinate our contacts, to do lists, calendars, etc...

I was gone last week when staff were unable to open another person's data on the network due to

"the paths specified in the configuration file are invalid or  currently unavailable."

However, everyone can still access their data, and all data is stored on a server.  The last folder differs by "name," but the paths, themselves, are similar--//server/companyfiles/timechaosdata/name for example (where the only difference between the location of the data is the last folder "name."

The company tells me that the permissions are not correct since the program can not access the folder/files correctly--yet I can get the data to load in version 7 of the software even though I get the "error" message re: invalid paths.

Ubuntu shows the sambashares have read & write permissions, and the samba configurationfile is set to allow full access.

Anyone have any ideas that might help me?

Thanks in advance...

---

### Post by superprash2003 on 2009-04-02
your samba permissions might be correct.. but you need to check whether the file has read/write access to root, or your username or everyone.. you may need to do a chmod and appropriately change the file/folder permissions..

---

### Post by jcounsel on 2009-04-02
Besides samba, I have set the permissions through the GUI...

I can also chmod a=rwx

The error message remains the same.

I can chmod 777 folder, but I get the same message.

I was thinking it was the way the program is handling something.

Otherwise "something" appears to be between the program and the server that is "limiting," in some way, the communication between the two.

Thanks.

---

