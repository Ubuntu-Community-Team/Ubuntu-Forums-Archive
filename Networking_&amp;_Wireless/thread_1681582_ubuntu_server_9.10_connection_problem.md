---
title: "ubuntu server 9.10 connection problem"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by mjc7373 on 2011-02-04
I'm baffled. I set up my file server with Samba shares for the PCs in my house, and all was well for about a month. 
Then yesterday things started getting weird.

First I discovered I could not make one shared directory writable, or change ownership, even using sudo. I would get an "operation not permitted" error. Some Googling suggested that since the folder in question resided on a FAT32 partition, some permission attributes would not work. I decided to copy the data to another drive, with the intention of wiping and re-formatting the FAT32 partition since I didn't need it anyway. 

Today, when attempting to copy a file from my Windows 7 PC to my server over LAN via Samba shares, it says it cannot connect to the host. WinSCP didn't work with the message that the host had failed to communicate. I logged in with Putty and had no problem copying a file from one server directory to the target folder, but I'm still not sure how to try remote transfer from Windows 7 to the server via ssh from the server. 

The permissions of the target folder are set to 777 and the owner is root. Any thoughts?


Any thoughts?

---

