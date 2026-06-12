---
title: "File sharing from Ubuntu box to Mythbuntu box"
date: 2010-06-06
forum: Mythbuntu
---

### Post by PhoenixDream on 2010-06-06
Hi, I have 2 boxes at home which I had ubuntu installed on and had file sharing via samba set up no problem, I decided to change ubuntu on one of them to mythbuntu to have more media centre functionality. I have since lost the shared files on the mythbuntu box but on my other ubuntu box the shares are still there and it can also see the mythbuntu box as well.

Ive been told I should be able to have exactly the same set up as I did before but I cant see 'Places>Network' on the desktop.

Would anyone be able to help?

---

### Post by williammanda on 2010-06-07
Have you ever considered using NFS instead of samba? It is faster and easier to setup in my opinion. Use this url as a guide to get you going.

[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs")

---

### Post by newlinux on 2010-06-07
Did you have these shares mounted using fstab? Have you tried mounting them? Is it that your mythbuntu box can't access shares setup with Samba on your ubuntu box, but your ubuntu box can see shares setup on your mythbuntu box? how did you install mythbuntu? Also, have you confirmed samba is running on your ubuntu box?

---

### Post by Erlander on 2010-06-08
I use ssh for this between my 2 Ubuntu/Myth boxes.  TYou need to install the ssh server and client on both boxes.

Then use Places/Connect to server.

Rob

---

