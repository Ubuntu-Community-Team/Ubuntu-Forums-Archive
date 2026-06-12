---
title: "how to save directly to network drive?"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by Psion23 on 2011-01-05
Hi,

I have a WD My Book World Edition network drive and I'm using Ubuntu 10.10. I'd like to be able to save media directly to the drive, but I can't seem to do this. I can find it, mount it, and read/write to it with no problems from nautilus, but it does not appear in the save dialog in either Firefox or Chrome if for example, I try to save one of the smiley gifs to the right of this entry box.

I'd rather not have to save it hard disk, and then copy it over later. This would save wear and tear on my SSD laptop, and keep files from taking up too much space on the not very large Ubuntu partition. I do this all the time from Windows 7, so I imagine that there is a way to do it here.

Any work arounds or fixes would be very helpful here.

What I've tried:

I've tried adding a bookmark- it shows up in nautilus but again not in the save menu.
I can open the location with Firefox, but that doesn't help me save there.
Copy/paste didn't work either.

Thanks!

---

### Post by dandnsmith on 2011-01-05
If you can mount it and write to it and navigate to it, then there shouldn't be any problem.
It must be somewhere in the permissions or the precise place you try to save - it works for me (sorry about that).

---

### Post by Psion23 on 2011-01-06
Hmm, I guess I need to explain it better.

Try to save an image in your browser (right click -> save as).

In the dialog that pops up, the network drive does not show up,even though it is mounted and I can browse to it normally. (I'd provide screenshots of this, but PrtScrn doesn't seem to do anything for me in Ubuntu.)

While I can just save it somewhere in one of my home folders and move it later, this is a poor solution. I'm sure there's a more elegant one out there.

---

### Post by Project84 on 2011-01-06
I see what you are saying.  It only gives you local disk locations as your options to save files.  I have Ubuntu 10.10 on my laptop wiFi to the router, a WD My Book World Edition NAS and  Windows Vista desktop wired lan to the router.  From the laptop I can access all shares on the NAS and desktop, but when I do "Right click, save as..." in Ubuntu, the network locations don't show up as a place to save files.   Didn't notice it until you brought it up so I don't have a solution for ya.  I still have to manually mount my NAS when I turn it on because I use DHCP and the NAS doesn't always have the same IP address.

As far as screen shots, go to the top left and click Applications>Accessories>Take Screen Shot.  Its built in to Gnome.

---

### Post by kaiseris on 2011-03-18
I have same problem with my Buffalo NAS on my home network. I can access the NAS through file manager. I browse through home network, find windows workgroup ant find my NAS there, then it mounts as Samba share. I can then copy, delete files etc. through file manager. But for example if I want download some files through Jdownloader and save them straight to my NAS I can't see it in the dialog window. Other example: I want to put some new music to my iPod with help of special software. I can upload music from internal drive, but again NAS won't show up in dialog window when choosing folder to upload music from. In other words I can access NAS through file manager but most of other apps won't see it.
How can I change that?
Thanks in advance.

---

### Post by Vger.x1 on 2011-03-20
I found this maybe it will help, It worked for me. [http://ubuntuforums.org/showthread.php?p=7583174](http://ubuntuforums.org/showthread.php?p=7583174)
> **daveinlaguna said:**
> Here's an easy way to open and save files to your network drives from Firefox.

1. Mount the drives that you want to access. (If you want to mount them permanently, see the Ubuntu documentation for that)

2. Using your file  browser, go to your home folder. Under "view" select "show hidden files."

3. Scroll down to the folder .gvfs, and right click on it. Select "make link."

4. Drag and drop the folder "link to .gvfs" to your desktop.

5. When saving a file to a network drive in Firefox, navigate to the .gvfs link folder on your desktop.

The .gvfs link folder will show your network drives. The Firefox "open"  and "save as" boxes can see this folder and access the drives through  it. You only have to put this link on your desktop once. It will stay  there when you reboot.

---

### Post by captainseabag on 2012-03-20
Brilliant! Thanks guys. I'm a somewhat experienced Ubunter and just sold my Mac... taking a leap of faith of using Ubuntu full-time now instead of just on testing machines. That helped a TON. Cheers.

:popcorn:

---

