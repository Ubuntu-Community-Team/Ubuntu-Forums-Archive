---
title: "Ubuntu - Windoze networking bug?"
date: 2005-02-26
forum: Networking &amp; Wireless
---

### Post by mira-ceti on 2005-02-26
Hi,
Is this a bug or am I doing something really silly?

I have Ubuntu on my home network with a windoze 2000 machine.  I have created an account on the 2000 box with the same username & password as the Ubuntu box and in the  Networking window I can see the 2000 box.  

When I first created the account on the 2000 box I could access any share on it and create files on the 2000 box from Ubuntu, no problem at all.  I then closed the connection to the 2000 box and later tried to reconnect.  When I did I recieved the following error 

"The Folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "Windows Network: wss001".

As it did previously work just fine there is clearly nothing wrong with the hardware, I even did the windoze thing and restarted both boxes with no effect at all.  I can still no longer access the 2000 box.

By the way I made absolutely no change to any configuration at all during this time.

Any ideas would be much appreciated.

---

### Post by Jad on 2005-02-26
Are you talknig about Networking or file/folder sharing with Samba?

---

### Post by mira-ceti on 2005-02-26
Sorry I didn;t make it clear, its file/folder sharing with samba.   I have not touched the smb.conf file as I am not sharing folders on the Ubuntu box, I am trying to access folders on the 2000 box from Ubuntu.

---

### Post by mira-ceti on 2005-02-26
Just a bit more information;  the smbmount command does not seem to exist 

root@ubuntu:/home/bevan # smbmount //dell/c   /home/mira/share/ -o username=mira,password=1234
bash: smbmount: command not found

also the mount command returns


root@ubuntu:/home/bevan # mount -t vfat //dell/c   /home/mira/share/ -o username=mira,password=1234
mount: special device //dell/c does not exist


root@ubuntu:/home/bevan # mount -t vfat //dell/c$   /home/mira/share/ -o username=mira,password=1234
mount: special device //dell/c$ does not exist


and  samba is running ;)

---

