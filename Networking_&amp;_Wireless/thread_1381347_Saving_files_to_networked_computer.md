---
title: "Saving files to networked computer"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by Silvertones on 2010-01-14
If I DL something from the Internet It askes were to save. This is normal however even though my 2 computers are nicely networked I can't seem to navigate to the network to save onto the other computer.

---

### Post by elliotbeken on 2010-01-14
yeh i would like to do the same thing just only to a Network attached storage drive. 

i have even tried to type the location (smb://192.168.0.4/media) in the firefox download location..

---

### Post by pricetech on 2010-01-14
Can you download locally and then copy it to the network location ??

---

### Post by elliotbeken on 2010-01-15
yes i can but i just wondered if there was a way or saving it on to the networked device without having to save it locally

---

### Post by Silvertones on 2010-01-15
With Ubuntu it's a 2 step process. When I had Win on both it was a 1 step process.

---

### Post by Morbius1 on 2010-01-15
You actually can do this but you may need to tweak a few things.

When you use Nautilus to mount the NAS device or other computer it actually creates a mount mount - but it's hidden. To "unhide" it in Nautilus:

[B]Nautilus > Edit > Preferences > Views > Show hidden and backup files
[/B] 
The mount point is at **/home/your_user_name/.gvfs**

Now if you're using firefox , for example, after you select "save as" you're presented with a display of your file system. Right click an empty space and select "Show hidden files". You should be able to navigate to the ".gvfs" diectory.

---

### Post by Silvertones on 2010-01-16
Morbius 1
That works fine. Thanks!

---

