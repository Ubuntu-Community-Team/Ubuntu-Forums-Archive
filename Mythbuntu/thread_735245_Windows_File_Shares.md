---
title: "Windows File Shares"
date: 2008-03-25
forum: Mythbuntu
---

### Post by EvilTom on 2008-03-25
Hi all
I’m new to Mythbuntu and only a little familiar with Ubuntu so please go easy on me! 
I have been using MediaPortal on my windows XP box for some time and decided to build a dedicated media PC. The parts have been ordered and are arriving shortly. I was going to put XP and media portal on this when it’s built but then I came across the Mythbuntu distro. The features look really good and I’d like to give it a go. 
In the meantime I have installed it in VMware workstation to try it out and have hit a problem.
 I have another Windows box acting as a general purpose server and there is some 500gb of assorted media on it, mostly rips of my dvd collection but some recorded content and a little music as well.  This is shared using windows file shares and media portal used to just connect to these and allow me to browse as if it were the local file system.
I would like to set up MythTV to do the same but I have been unable to find a way of doing so. Can anyone point me to a tutorial or the like?

Many thanks :)

---

### Post by volkswagner on 2008-03-25
in a terminal (exit mythtv> from the desktop >applications>accessories>terminal)

```
sudo apt-get install samba
```

---

### Post by EvilTom on 2008-03-25
> **volkswagner said:**
> in a terminal (exit mythtv> from the desktop >applications>accessories>terminal)

```
sudo apt-get install samba
```

Ah now I though about that but I thought that was just to allow windows machines to read linux shares. Is it the other way around as well?
I'll give it a go.
Thanks

---

### Post by bernied on 2008-03-25
You are right you only need that package to serve files. You can usually access windows shares through your file manager, whichever one you use. 

For instance, in konqueror (in KDE), I click on the system icon, and there's an option for 'samba shares'. If you're network is sensible, then any windows shares that are available should appear. If they don't and you know their (IP) address, try putting that in the address input box, preceded by smb://

In gnome, you can can click 'Places' and 'Network', either in the main menu or in nautilus.

---

