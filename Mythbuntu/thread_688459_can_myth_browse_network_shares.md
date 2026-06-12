---
title: "can myth browse network shares"
date: 2008-02-05
forum: Mythbuntu
---

### Post by onesojourner on 2008-02-05
I am sure myth can do this. Is there a way that myth can browse smb shares? I have a few videos on my laptop That I would like to be able to browse to and play on occasion. The laptop is not always on so I don't want to mount the share.

---

### Post by newlinux on 2008-02-05
Not that i know of. This is a feature I have been interested in too...

---

### Post by Caps18 on 2008-02-05
Would it be ok to copy the files over to the Mythbuntu hard drive (via network or usb hard drive)?  I would think that could be done, and then I would expect MythTV to see them.

At least that is what I hope to do in the next few weeks.

---

### Post by ubnewbie2 on 2008-02-05
> **onesojourner said:**
> I am sure myth can do this. Is there a way that myth can browse smb shares? I have a few videos on my laptop That I would like to be able to browse to and play on occasion. The laptop is not always on so I don't want to mount the share.

Use the gnome file manager,  nautilus. It can browse the network, including Windows network shares.

edit:  oops sorry, I see you want to do it from within myth.  You could try something like   smb://<insert_computer/share_name>.

---

### Post by Archmage on 2008-02-06
Set the SMB-Network-Share as the folder that MythVideo uses.

---

### Post by newlinux on 2008-02-06
> **Caps18 said:**
> Would it be ok to copy the files over to the Mythbuntu hard drive (via network or usb hard drive)?  I would think that could be done, and then I would expect MythTV to see them.

At least that is what I hope to do in the next few weeks.

Yes, you could do that. Just copy to a folder mythvideo scans. 

You could also setup the mountpoint but not set it to mount at boot, but to mount manually (whenever your laptop is on and you want to access it). This is what I do for my laptop. You could make a mount script and unmount miniscript that runs via irexec from your remote, or if you use a keyboard just type in the mount and unmount command wen you want to use it and disconnect it...

---

