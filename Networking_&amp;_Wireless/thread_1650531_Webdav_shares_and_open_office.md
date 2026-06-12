---
title: "Webdav shares and open office"
date: 2010-12-21
forum: Networking &amp; Wireless
---

### Post by tjolley on 2010-12-21
Hey all. I am cross-posting this from the Open Office Forums, as I have not received any replies over there. I mapped to various WebDAV shares via 'Places' , 'Connect to Server'. 
___________________________________________
Hey all. I have been trying to find a solution to the following issue using Open Office on Linux (Ubuntu specifically) 
 
When trying to open a document stored on a WebDAV share, I receive the  message "General input/output error while accessing 'file  path/filename'" 
 
When trying to save a document I receive the message" Error saving the document: 'Document name'" 
 
To rule out WebDAV and the OS, I installed Abiword and I was able to  both access and create/save/modify documents on a WebDAV share. In addition, I have  tried this on both my personal WebDAV server and using Apple's idisk  WebDAV server. This seems to eliminate the OS and WebDAV as the issue. 
 
For additional testing I have tested OpenOffice and NeoOffice on a Mac,  and OO on Windows XP. Both implementations are able to access and save  files on WebDAV shares. This further tightens the focus as this  eliminates OO on both the Mac and Windows OS. 
 
The issue appears to be specifically related to the Linux implementation of Open Office.  
 
Any ideas? I m stumped.

---

### Post by kg4wih on 2010-12-22
I never could find a solution to this either. I believe it is a problem with nautilus. I installed dolphin and konqueror, open dolphin and use webdav(s)://server/directory

---

### Post by tjolley on 2010-12-28
And this is the problem with Open Source. Massive issues with a major program not functioning with Standard web protocol, and no one to call, no single company to contact about the issue and get it resolved.

---

### Post by tjolley on 2010-12-28
This is definately an Ubuntu specific issue. I fired up Fedora 11 and installed OpenOffice and it works fine. Reinstalled OpenOffice using apt-get on Ubuntu, and it is staill failing to access WebDAV shares at all.

Anyone?

---

### Post by tjolley on 2011-01-02
Bumbp. Anyone know anything about how Ubuntu works with WebDAV?

---

### Post by wheelerthomas on 2011-02-23
I know this is an old post but it seems to still be an issue with OpenOffice opening documents on a webdav share. The way I got it to work is to mount the share via mount.davfs and when I do this there is no problem. SO it may be a gvfs issue

---

### Post by sbhatia on 2011-02-23
I am also having problem with WebDav for copying files. It opens file in browser instead of copying into selected folder of browser.
 
Are you able to copy files?

---

### Post by lokutus25 on 2011-07-20
> **wheelerthomas said:**
> I know this is an old post but it seems to still be an issue with OpenOffice opening documents on a webdav share. The way I got it to work is to mount the share via mount.davfs and when I do this there is no problem. SO it may be a gvfs issue

No news, same problems on Ubuntu 10.04 LTS x64 and 11.04 x64 (client and server).
I need look for something else. Any suggestion on alternatives to WebDav on Ubuntu?

---

