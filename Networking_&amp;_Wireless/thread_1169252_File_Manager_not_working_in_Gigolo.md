---
title: "File Manager not working in Gigolo"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by TeachThai on 2009-05-25
It appears to me that Gigolo is showing that I have a working connection with my Windows XP based computer but when I try to "open" the connection to view the shared files from the Windows XP machine nothing happens. 

I have recently installed Xubuntu on my computer so now I have a dual boot system with Windows 98SE. I had a connection between my computer using Win 98SE and the other computer using Win XP before I installed Xubuntu so I don't see why the connection isn't working as well at this point. 

Following the directions from another thread, I edited the defaults.list in the ~/.local/share/applications folder by setting the default-handler variable to nautilus, inode/directory also equal to natilus, and the directory/normal to natilus.   I also tried setting these variables to thunar.desktop but that didn't result in anything happening either.  I haven't come across any "workarounds" yet. 

Thanks in advance for any suggestions that will work.  Other than this issue and the fact that my sound card does not work, I am happy with the Xubuntu installation distro.

---

### Post by slashtact on 2009-06-03
For your sound issues you may want to try the following:

Open up Terminal (Applications > Accessories > Terminal)

Type: alsamixer

Use the arrow keys to turn up the volume on Master and Front, and press 'm' to unmute both channels. You can tell that a channel is muted because it will have MM at the bottom of the volume bar. If this doesn't help, I'm sure there are more answers on the way.

As for connecting to a samba share on another linux machine on the network, I'm having the same trouble. It was much easier typing smb://servername/folder when I ran gnome. I'll let you know what I come across.

---

### Post by pourya on 2010-07-21
I had the same problem. What you need to do is to install gvfs-fuse and reboot your machine...
here is how to do it:

[HTML]sudo apt-get install gvfs-fuse[/HTML]


once you do this you will be able to browse your network file system.

---

