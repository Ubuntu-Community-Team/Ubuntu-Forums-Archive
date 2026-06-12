---
title: "sharing files from pc to pc"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by Mia1990 on 2010-08-06
Hi all i would like to set up file sharing from one ubuntu pc to another wireless laptop.I found samba on the internet i installed it and i can share files but it's slow a 700mb avi file was going to take 2 hours and from what i read samba is for sharing files from linux to windows.I also found ssh that to is slow also i think it goes over the internet or something like that.So is there any other way to share files that's faster or have i forgot something.I only have 2 ubuntu 10.04 computers and 1 open solaris but the open solaris i will not be putting on the network.Thank you

---

### Post by drdos2006 on 2010-08-07
Try this. You need server files on one machine and client files on all the other machines.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 


regards

---

### Post by Mia1990 on 2010-08-07
nfs that never came up when i did a Google search on sharing files on ubuntu .I'll give it a try.

---

### Post by YesWeCan on 2010-08-07
Hi. Samba is sometimes slow because it is more complicated and has software overheads. Sometimes certain brands of ethernet card work slowly using Samba.

However, SSH ought to be lickety-split fast. If you are using 10.04 you can simply connect to the other computer using "Places/Connect to Server..." and then select SSH and enter your login and password for the other machine. Then drag and drop.

If you are still getting 2hours for 700MB (780kb/s) then something else may be wrong.

SSH doesn't go over the internet if your computers are on the same LAN. SSH will go whatever route you tell it to.

---

### Post by YesWeCan on 2010-08-07
Just now, between my laptop (Puppylinux) and my desktop (Ubuntu 10.04) which are on the same wired LAN I can transfer at 50Mb/s (million bits per second). If you are only getting 0.8Mb/s then there is something about your connection path that is slowing things down. If so, what is your connection path, exactly?

---

### Post by Mia1990 on 2010-08-07
The laptop is a linksys usb card and i am not sure what type the desktop is as it's came with the pc.SSH doesn't go over the internet i just seen the the diagram on a website and assumed it did.I may be able to set that up then because i'm getting nowhere with nfs i'm blond so i guess i need a step by step guide.Lol.How would i go about setting up ssh and can i automount the folder i share?Thanks

---

### Post by YesWeCan on 2010-08-07
Places menu top left
Select "Connect to Server..."
choose service type SSH
Server: put in the IP address of the computer you want to connect to
Click "Connect"
Enter your username and password for the computer you want to connect to.

Please say if any of that is not clear

---

### Post by Mia1990 on 2010-08-07
Clear as a glass of water.Can i automount the folder i share?

---

### Post by YesWeCan on 2010-08-07
I am not sure how to auto-mount a Nautilus share. I'll have to Google it.
You can add a bookmark in the Places menu so it is a one-click to reconnect it.
An NFS share can be mounted at boot by adding an entry to the /etc/fstab file; but this is a bit more tricky and involves some configuration on both PCs and installing some software.

See what the transfer speed is like while I Google.

---

### Post by Mia1990 on 2010-08-07
ok one way it works perfect the other way i get a validation error,Would you know what is causing this?

---

### Post by Bucky Ball on 2010-08-07
If you have static IPs ssh is the way to go. So simple. 

Places->connect to server. Choose ssh and put in the ip of the machine you are attempting to connect with. Speeds, though, are not that great depending how you have it set up. 

I diddled for a few years on and off trying to successfully network our three machines. Samba and NFS were problematic, although both did eventually work. Clunky. This is the simplest by far. Ftp is also good and just use Filezilla to grab and transfer files from one machine to another.

Slightly different from Windows/Samba thinking but, for me at least, better and more efficient. ;)

---

### Post by YesWeCan on 2010-08-07
> **Mia1990 said:**
> ok one way it works perfect the other way i get a validation error,Would you know what is causing this?

I don't recognize "validation error". It may be a permission thing. Make sure that you have write permissions on the folder you are trying to copy a file to.

---

### Post by Mia1990 on 2010-08-07
Ok i have it fixed now.I just deleted the known host file and it let me right in.I guess my ex boyfriend tried ssh out but it's fixed.The speed is still slow 87 mb file and it says 11 min maybe somethings wrong with the network card in that pc.

---

### Post by gpdas on 2010-08-07
Hi, can we do something like  \\IP address as used in MS Windows XP when typed in Start--> Run

---

### Post by YesWeCan on 2010-08-07
So some quick surfing indicates that auto-mounting an ssh connection requires an fstab entry involving the sshfs filesystem type. I am not familiar with this; maybe someone else can help.

I am familiar with NFS. I find it works fine. You have to tell one machine to export a directory tree and tell the other machine to mount this directory tree at boot. The exporting machine needs to have 'nfs-kernel-server' installed (see ubuntu software centre). The exported directory is defined in /etc/exports. The connecting PC has to have an entry in /etc/fstab to mount the nfs share at boot.

---

### Post by Mia1990 on 2010-08-07
> **YesWeCan said:**
> So some quick surfing indicates that auto-mounting an ssh connection requires an fstab entry involving the sshfs filesystem type. I am not familiar with this; maybe someone else can help.

I am familiar with NFS. I find it works fine. You have to tell one machine to export a directory tree and tell the other machine to mount this directory tree at boot. The exporting machine needs to have 'nfs-kernel-server' installed (see ubuntu software centre). The exported directory is defined in /etc/exports. The connecting PC has to have an entry in /etc/fstab to mount the nfs share at boot.

Can you help me with nfs the directory i am trying to export is home/mia/video or any one i can put the files anywhere if i could just get it to work but i have had no luck with it.

---

### Post by Mia1990 on 2010-08-07
I'M thinking it the lan card ssh is slow too i'll go buy one Monday 
> **Bucky Ball said:**
> If you have static IPs ssh is the way to go. So simple. 

Places->connect to server. Choose ssh and put in the ip of the machine you are attempting to connect with. Speeds, though, are not that great depending how you have it set up. 

I diddled for a few years on and off trying to successfully network our three machines. Samba and NFS were problematic, although both did eventually work. Clunky. This is the simplest by far. Ftp is also good and just use Filezilla to grab and transfer files from one machine to another.

Slightly different from Windows/Samba thinking but, for me at least, better and more efficient. ;)

---

### Post by YesWeCan on 2010-08-07
Try this: [https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html)

---

### Post by Mia1990 on 2010-08-07
I'LL give it a go tomorrow

Thank you

---

