---
title: "Samba permission problem"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by BlueMooneke on 2011-03-09
Hey,

recently I installed Ubuntu 10.04 LTS to use it as a server. As I am not really comfortable with the terminal, I used this version because of the GUI.

Now, I'm in a network with only Win 7 computers in in. The server is mostly used as a sharing device. 
Example: I put my Itunes library on the server and everybody on the network loads the same library into his itunes...

Now, I installed Samba and I do think I use a good configuration but apparently not. The folder is visible on the network for all computers and are also accessible for all of them. The problem is when I copy a file to the server (like a .txt file of windows with just plain text), I can edit it on any other Windows machine, but on the server itself, the file is locked. If I check permissions it says:
Owner = nobody
=> read only
Group = nogroup
=> read only
Others
=> read only

But I would like to use some files on the server itself! I got a long way around to eventually access the files (login as root, edit permissions for all files,...) but that should Samba be doing instead!

What am I doing wrong?
Config file of samba:

[ServerFolder]

    comment = Shared files on Homeserver
    path = /home/HomeServer/ServerFolder
    browsable = yes
    guest ok = yes
    read only = no
    public = yes
    force create mode = 0777
    force directory mode = 0777
    writeable = yes
    create mask = 0777

also used chmod on the folder... nothing helps


Any solution?

Thanks in advance!
BlueMooneke

---

