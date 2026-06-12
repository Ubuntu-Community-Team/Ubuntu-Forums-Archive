---
title: "How to install Adobe Flash Player and Ubuntu can't find flash?"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by FastMady123 on 2008-01-09
When I went to YouTube, it tells me to install Flash. When I try to install it, it pop-up a windows that it can't find it. Next, I went to to Adobe site to install Flash to download the file however I don't know to install it because I'm new to Ubuntu and I know to install software in Windows XP. What should I do?

---

### Post by santiagoward2000 on 2008-01-09
> **FastMady123 said:**
> When I went to YouTube, it tells me to install Flash. When I try to install it, it pop-up a windows that it can't find it. Next, I went to to Adobe site to install Flash to download the file however I don't know to install it because I'm new to Ubuntu and I know to install software in Windows XP. What should I do?

Hi!
First, try opening **Add/Remove...**, look for **Macromedia Flash** and install it. See if this works. If it doesn't, try using this guide to fix it:
[http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397")
Cheers!

---

### Post by eye208 on 2008-01-09
> **FastMady123 said:**
> When I went to YouTube, it tells me to install Flash. When I try to install it, it pop-up a windows that it can't find it. Next, I went to to Adobe site to install Flash to download the file however I don't know to install it because I'm new to Ubuntu and I know to install software in Windows XP. What should I do?
Go to *Places --> Home Folder*, then select *View --> Show Hidden Files*. Find the subfolder *.mozilla* and open it. Make a new subfolder *plugins* inside that folder unless it already exists. Unpack the archive you downloaded from Adobe's site and move the file *libflashplayer.so* into that *plugins* folder. Restart Firefox. Done.

---

