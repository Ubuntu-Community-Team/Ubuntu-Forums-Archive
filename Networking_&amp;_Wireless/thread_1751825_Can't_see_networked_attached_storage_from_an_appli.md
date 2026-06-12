---
title: "Can't see networked attached storage from an application"
date: 2011-05-07
forum: Networking &amp; Wireless
---

### Post by XEtedBear on 2011-05-07
I have an Iomega network media storage drive on my home LAN which I use as backups from all the computers on that LAN. I prefer to do backups by hand (can't understand how to properly control many available automated software backup packages!). I use a very capable file/folder comparison app. called 'Beyond Compare' under both Linux & Windows. It has one difficulty in the Linux environment -it can't see the Iomega drive in order to specify one 'half' of the comparison source. This is what I see when trying to select a source:
[IMG]~/tony/beycomp-ss-1.png[/IMG]

AS you can see, I can specify any folder which is mounted to my system, but nothing that is on the LAN. 

How do I do this?

Clearly there is also a prior question: How do I include a screenshot in a post? Pressing the relevant icon in the 'post new thread' toolbox asks me for a URL of the image - how do I specify that?

---

### Post by sanderj on 2011-05-07
Can you see the NAS via Places -> Network?

If not, do you know which protocols the NAS speaks (SMB, FTP, etc), and what the IP address is?

---

### Post by sanderj on 2011-05-07
> **XEtedBear said:**
> 

[IMG]~/tony/beycomp-ss-1.png[/IMG]

AS you can see, I can specify any folder which is mounted to my system, but nothing that is on the LAN. 

How do I do this?

Clearly there is also a prior question: How do I include a screenshot in a post? Pressing the relevant icon in the 'post new thread' toolbox asks me for a URL of the image - how do I specify that?

Click on the button "Manage Attachment", select the file, and then click on Upload.

---

### Post by XEtedBear on 2011-05-07
> **sanderj said:**
> Can you see the NAS via Places -> Network?

If not, do you know which protocols the NAS speaks (SMB, FTP, etc), and what the IP address is?

Yes, I can access the NAS via the netwrok - that's what I am doing instead of using BeyondCompare.

---

### Post by XEtedBear on 2011-05-07
> **sanderj said:**
> Click on the button "Manage Attachment", select the file, and then click on Upload.


Thanks for this. Hopefully the screen shot is now attached. Is it legible?

---

### Post by Morbius1 on 2011-05-07
When you connect to the NAS from "Network" it creates a mount point at :
> /home/user-name/.gvfs/share-name on server-name

Notice that this is a "hidden" directory - ".gvfs". You will need to "show hidden files" in Nautilus and your application to see this directory or create a symlink to a "non-hidden" directory.

---

### Post by XEtedBear on 2011-05-07
> **Morbius1 said:**
> When you connect to the NAS from "Network" it creates a mount point at :


Notice that this is a "hidden" directory - ".gvfs". You will need to "show hidden files" in Nautilus and your application to see this directory or create a symlink to a "non-hidden" directory.

Great, that does exactly what I want. Thanks for the advice

---

