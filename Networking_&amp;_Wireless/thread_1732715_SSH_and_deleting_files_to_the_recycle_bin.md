---
title: "SSH and deleting files to the recycle bin"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by ActionJackson251 on 2011-04-18
[FONT=Arial][FONT=Ubuntu]I'm using Ubuntu 10.04. I have set up a pc to act as remote storage. I connect my desktop pc to it.
I have done the following:

sudo apt-get install sshfs
sudo adduser fuse
sudo mkdir /mnt/remotedir
sudo chown username /mnt/remotedir
sshfs username@remote_computer_ip:/path_on_remote_comp /mnt/remotedir

(obviously replacing the username and paths with my information)

I can connect to the remote computer  however I cannot delete remote files to the recycle bin. What do I need to do in order to delete files to the recycle bin?[/FONT][/FONT]

---

### Post by chili555 on 2011-04-18
Isn't it as simple as:```
sudo rm -rf .local/share/Trash/*
```

---

### Post by ActionJackson251 on 2011-04-18
[FONT=Arial][SIZE=4][FONT=Ubuntu]Thanks for the prompt reply. That command is to delete files using the command line?[/FONT][/SIZE][/FONT]
 [FONT=Arial][SIZE=4][FONT=Ubuntu]This is my setup: I have a pc I use as remote storage. It is automatically logged into when I login on my local pc. I have symbolically linked various folders from the remote pc to my local home folder. Videos, music, documents etc. When I delete a file it deletes without going to the recycle bin. Sorry for the long winded explanation, I hope it helps explain my problem more clearly.[/FONT][/SIZE][/FONT]

---

### Post by chili555 on 2011-04-18
> That command is to delete files using the command line?Yes. I assumed from your original post, that you were connected to the remote machine by ssh and that you want to delete files in the remote machines recycle bin, which the command I suggested does.

It now seems that you want to delete files on the remote machine from your local machine. Your observation that they won't go to the recycle bin on either machine is correct. If you can see the file on some kind of file manager; Nautilus, for example, you should be able to highlight the file and press Shift+Delete and remove them permanently.

---

### Post by ActionJackson251 on 2011-04-18
[FONT=Arial][SIZE=3][COLOR=black][FONT=Ubuntu]I can see the files in nautilus and delete them, permanently. I know, after editing some configuration files, that you can create a recycle bin when using samba. Is there a anything similar  for ssh? Or is it just not possible to delete remote files in Nautilus to the recycle bin when using ssh? I hope it is, I have a desktop and a laptop will be connected to the remote machine and would like to have one central storage location. If I can't get a working recycle bin I'll have to rethink.[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by chili555 on 2011-04-18
I am not aware of a way to do so.

---

### Post by ActionJackson251 on 2011-04-18
[FONT=Arial][SIZE=3][COLOR=black][FONT=Ubuntu]Ok cheers, I won't mark as solved just yet in case anybody does know a way. I did search Google before I posted and didn't see any information.  I'll have to look into Samba or NFS.[/FONT][/COLOR][/SIZE][/FONT]

---

### Post by ActionJackson251 on 2011-04-21
[SIZE=3]Just in case anyone is interested, you can use the recycle bin via Nautilus [/SIZE][SIZE=3]from a client machine [/SIZE][SIZE=3]whilst using SSH. I was mounting the server on my client machine at / (root). I made a mistake and mounted at my home folder and low and behold I could delete files to the bin. Not sure what the problem was, perhaps permissions? For me at least, problem solved.[/SIZE]

---

