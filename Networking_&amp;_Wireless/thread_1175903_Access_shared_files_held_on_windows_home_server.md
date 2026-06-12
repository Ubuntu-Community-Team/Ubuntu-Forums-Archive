---
title: "Access shared files held on windows home server"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by jinxy_tj on 2009-06-01
Hi, I have installed xubuntu 9.04 on my playtation 3. I have done this as I have a server in my home which contains all my music, and videos (along with other files that are unimportant for the PS3). I am trying to access these files, but am not able to figure how to do this. The files are all contained in seperate folders, although a second option is that the Windows home server has a media sharing option, which on my Playstation opeating system, shows as a media server. It is enabled on the server, although I am unable to access it through Xubuntu. 

The whole purpose of this exercise is to watch and play my movies and music that are stored on my server, using the playstation booted into xubuntu.  The playstation's operating system is limited to its capabilities of reading video files, especially mkv format. So the end result for xubuntu for me will be a media centre client.

I hope someone can lead me in the right direction.

---

### Post by dmizer on 2009-06-02
Please refer to the 6th link in my sig.

---

### Post by appier on 2009-06-02
> **jinxy_tj said:**
> I have installed xubuntu 9.04 on my playtation 3. 

Someone tell me if I am wrong, but to the best of my knowledge, the Thunar file manager included with Xubuntu as part of the XFCE does not have the capability to mount shared folders.  If there is a way to install the Gnome Desktop on the PS 3, then you can use the Nautilus which easily mounts remote shares.

On a normal machine you would install the Gnome using the following commands:

> sudo apt-get update
sudo apt-get install ubuntu-desktop

---

