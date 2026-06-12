---
title: "sharing with Win XP"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by raunhar on 2009-01-17
I have installed SAMBA and am able to access my other computers which are on Win XP, BUT through WinXP i am not able to access the SAMBA Shares on UBUNTU. The shared folders on UBUNTU have both the rights of accessing and writing.

Pl. suggest

---

### Post by Iowan on 2009-01-17
Ubuntu comes with Samba-client installed - the server must be added (I presume that's what you did).  Does the Windows user have an account on Ubuntu AND Samba (created with smbpasswd)?

---

### Post by raunhar on 2009-01-19
How to do it. I did nothing on my Win XP systems

---

### Post by diablo75 on 2009-01-19
Well the way I've done it before is to just create a new folder and share it.  If samba server isn't installed, it prompts me with a box asking if I want to install it and I just click Install...

---

### Post by theozzlives on 2009-01-19
Assuming you got SAMBA setup properly, go to Windows>My Network Places and on the left pane you'll see other computers in workgroup (or something like that). Click it and your Ubuntu computer should be in there.

---

### Post by deadjz on 2009-01-19
i already had SAMBA installed in my computer,
now that i can view my other computer in my network,
but when i access the computer it shows nothing in there.
is there any thing i need to do so that i can view the sharing folders/files from other computers???

---

### Post by DJonsson2008 on 2009-01-19
Using Konqueror helped me sort this out. 

I've found the available Samba gui's Nautilus and other apps weak. Just because you see nothing in the Places>Network can be decieving, because often times even though nothing shows up your Windows LAN drives may actually be accessible.

Nautilus's LAN connecting strength and bottom line seems to be the [Places>Connect to Server] wizard.

Whatever the case now my primary place for accessing Windows LAN drives 
is via Konqueror.

Now I make my drive connections via Konqueror, save them as bookmarks, and save my Konqueror profile settings which saves most of the parameters needed to access the drives again. I open Konqueror access the LAN drives, sometimes i have to log on to the drives, and then the drives are accessible by other apps including Nautilus. Works like a charm for sftp as well.


The only thing I've found that slightly helps is changing the WORKGROUP 
name to the Windows/Lan WORKGROUP name but not sure if even that adjustment
is critical.

---

