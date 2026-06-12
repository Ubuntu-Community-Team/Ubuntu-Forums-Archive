---
title: "Linux to Linux networking"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by timZZ on 2009-03-14
Hi,

So I am using one Ubuntu to box as my file share and I want to convert my 3 other machines to Ubuntu possibly as well.

I can't seem to find how to create a non-GUI method of creating a linux to linux network connection.

I have seen for other distros its /etc/exports

Can anyone send me on the right path?

I had a samba share but I took it down, since I won't have any windows machines connecting to the file server any longer.

---

### Post by jelle_ on 2009-03-14
if you need no gui, you can try ssh. it is installed by default on ubuntu and gives you access to everything on your computer. i heard the computer is accessible trough file manager 

just type ssh hostcomputersip and give your username and password to use it

---

### Post by timZZ on 2009-03-14
Perhaps I am looking for a GUI to handle file transfers

but I am looking for the network config file.

---

### Post by timZZ on 2009-03-14
Basically ... to re-cap

I am just looking to administrate my network options myself to learn rather then using the right click create share option.

the end result is I just want to be able to pass information to and from my linux (ubuntu hardy herion) server to my linux (ubuntu hardy herion) desktop.

Anyone have information on this?

---

### Post by ugm6hr on 2009-03-14
Not a big networking expert, but ebox might make things easier for you:
[http://ebox-platform.com/community/installation-guide/](http://ebox-platform.com/community/installation-guide/)

It does use SMB, but there is nothing wrong with that...

---

### Post by timZZ on 2009-03-14
What about NFS?

People not using this?

---

### Post by ugm6hr on 2009-03-14
If you want to do it with NFS:
[https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html)

---

