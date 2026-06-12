---
title: "access W7 home network PC, how?"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by gychang on 2011-12-20
Like the latest xubuntu for speed but I am having difficulty accessing windows 7 home machine.  Using gigolo, pyneighborhood, I am unable to access the files.

Is there a simple how to?, was able to access fine on the latest gnome version.  usually with local ip address I was able to access...

gychang

---

### Post by LewisTM on 2011-12-20
You should be able to access a Windows network with Gigolo or Thunar as long as you have gvfs-backends installed. 
If you do and still cannot connect, then it would be something specific to your situation and more information would be required about your network setup and the kind of errors you get.

Cheers!

---

### Post by gychang on 2011-12-20
> **LewisTM said:**
> You should be able to access a Windows network with Gigolo or Thunar as long as you have gvfs-backends installed. 
If you do and still cannot connect, then it would be something specific to your situation and more information would be required about your network setup and the kind of errors you get.

Cheers!

trick was to get the gvfs-backends installed and now gigolo works but couldn't get Thunar to work.

thanks,

---

### Post by LewisTM on 2011-12-20
Thunar should work as well, they are both dependent on the gvfs framework.
You can enter network:// in the location bar, or find Network in the Go menu or in the Tree view pane.
That being said I prefer Gigolo for it's ability to mount, unmount and bookmark on-the-fly.

---

### Post by gychang on 2011-12-20
> **LewisTM said:**
> Thunar should work as well, they are both dependent on the gvfs framework.
You can enter network:// in the location bar, or find Network in the Go menu or in the Tree view pane.
That being said I prefer Gigolo for it's ability to mount, unmount and bookmark on-the-fly.

must be doing something wrong on thunar, on location bar typing in //192.168..../ does not link... no Go menu.

---

### Post by LewisTM on 2011-12-20
What menus do you have then? Sorry depending on your language it may be different. 
I have File, Edit, View, Go, Help

For the address try using smb:// instead

---

