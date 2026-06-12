---
title: "Restoring Hosts file (usr/share/vlc/lua/http)"
date: 2012-08-28
forum: Multimedia Software
---

### Post by JauntyJack on 2012-08-28
I've been trying to stream video from my Ubuntu machine to my Nexus 7 using VLC HD Remote. Following instructions for setup, I tried to edit the hosts file that is here:

usr/share/vlc/lua/http

Problem was that I could edit it, but every time I tried to save it, I got told I didn't have permissions. I went looking for a solution and found this Terminal command:

gksu gedit /usr/share/vlc/lua/http/.hosts

However, after editing the file (uncommenting two lines) and saving, I now have an odd situation. My folder list now shows two files: one is a .hosts file, "zero bytes, link to plain text document", and a file .hosts(tilde), "289 bytes, backup file". I can't open the latter. 

Not sure what I've done or how to restore the file from (what I hope is) this backup file. 

Any helpful suggestions?

---

