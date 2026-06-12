---
title: "Playing music from network in ubuntu"
date: 2009-10-24
forum: Multimedia Software
---

### Post by tjock on 2009-10-24
Hi!

I have a server with all my music on it, it is running windows server 2003.

I wish to play this music on my desktop-pc running ubuntu 9.04. I can acces the files and play them seperately with the normal player but when trying to add the music to a music-library such as Amarok I cannot add the tracks. I have also tried using Banshee and Rhythmbox.

Is there anything I need to do in these to add the music?

Thanks!
//Tjock

---

### Post by AutoStatic on 2009-10-24
Hello Tjock, how do you mount the Windows share? Through fstab or from within a Gnome session?

---

### Post by naftali on 2009-10-24
Hi

I also have a similar issue with rhythmbox. I mounted a nas using the "connect to server" option in nautilus (I used the windows share option), and it worked like a charm, I can access files with no problems.
in rhythmbox, however, when I try to import a file or folder from the nas, I get: "could not open resource for reading" error.
I don't know if this matters, but in a terminal typing mount won't show me the nas.

Thanks in advance!

p.s. the nas needs a username and password, but I told nautilus to remember them.

---

### Post by tjock on 2009-10-24
Hey,

I have mounted the files via within gnome and can access them. Do I need to do anything else?

//Tjock

---

### Post by AutoStatic on 2009-10-25
Yes, it's best to mount the share by adding it to your /etc/fstab.
You could also try browsing to your share, it's in your home in the directory .gvfs/

---

