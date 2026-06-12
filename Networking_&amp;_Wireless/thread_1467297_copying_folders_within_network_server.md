---
title: "copying folders within network server"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by speed32219 on 2010-04-30
This is a kinda stupid question, well I answered it, I just checked my wireless router and I was averaging 2MB/s across the network.  When I stopped the disk copy from disk-1 (backup 1.5TB drive in the Ubuntu server) to the raid5 array (Same server) the activity across the network stopped.

So to answer my own question, moving a folder from one disk drive to another within a server using MS XP explorer on the network, the data is copied from the server to my local workstation and back again to the server across the network.  No wonder copying TB's of data has been so dang slow!  

I wonder if the same holds true if I fire up 9.10 workstation on this machine and try and copy the folder from one drive to another on the same machine across the network using nautilus?

Well, I just fired up Putty and ssh'd into the server.  I am copy the whole disk and my network activity is normal, so it is contained within the server environment.  Never really thought about it until I noticed how slow it was, I have been using XP to copy alot of data over the years (I was on a 100Mbps network though) and never thought about how the data was being copied. Until now that is.

---

