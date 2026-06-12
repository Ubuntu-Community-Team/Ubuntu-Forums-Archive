---
title: "Amarok using files over a server"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Victormd on 2008-04-20
I'm trying to find a good mp3 file manager and a lot of people suggested Amarok, my only problem is that all my mp3 files are stored on a server (it's a small home server connected to the same router as my main machine) and I can't (or don't know how to) link my Amarok collection folder to the folder on the server... Is this possible with Amarok or should I try something else?

---

### Post by jcwmoore on 2008-04-20
so you want to point a local folder to folder on your server that is full of music.  One solution is **sshfs**, use this to point your music folder to you server.  I do this with my Documents folder, none of the files in the Documents folder are actually on my PC, but they are on the server.  I see no reason why you couldn't do this with your music.

---

### Post by tvtech on 2008-04-20
yes this is possible with amarok. I have a remote ssh server that I have a significant amount of my collection on and use amarok with it.  I just mount the folder as a local folder and select it in amarok

**settings>configure amarok>collection>select the folder here**

---

### Post by Victormd on 2008-04-20
> **jcwmoore said:**
> so you want to point a local folder to folder on your server that is full of music.  One solution is **sshfs**, use this to point your music folder to you server.  I do this with my Documents folder, none of the files in the Documents folder are actually on my PC, but they are on the server.  I see no reason why you couldn't do this with your music.

Ok... good to know, [COLOR="Silver"]now, what is sshfs and how do I use it?[/COLOR]

Got it installed but have no idea how to use it to mount the server directory, any help?

---

### Post by _oOMOo_ on 2008-04-21
You can share your music directory using nfs or ssh.

This guide looks good for ssh [http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html]("http://www.ubuntugeek.com/mount-a-remote-folder-using-ssh-on-ubuntu.html")

I store videos and music on a server and share both folders over the network using nfs - there is (please correct me if I'm wrong) a slight overhead using ssh I think as the link is encrypted.

There is a guide to install nfs here: [https://help.ubuntu.com/community/SettingUpNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")

The last option is to install amarok on the server and plug a couple of speakers in to it then run it locally with 'ssh -X user@host amarok' but you need an Xserver on the server for that (and to be close enough to it to hear it! :))

---

### Post by Victormd on 2008-04-21
I don't know what I'm doing wrong following the sshfs link, but when I get to
> sudo chmod +x /dev/fusermount
I get an error (non existing file or directory) and when I do
> sshfs username@ipaddress:/remotepath ~/remoteserv (properly modified)
The terminal hangs until I press CTRL C
Going to try to find some other How to...

---

### Post by _oOMOo_ on 2008-04-22
You can ssh into the server ok, but you can't mount the folder?

[https://help.ubuntu.com/community/SSHFS]("https://help.ubuntu.com/community/SSHFS") This documentation seems to indicate you no longer need the command that is failing, simply that you need to be a member of the fuse group.

The error you're getting normally means one or other of the directories you are specifying doesn't yet exist.

---

### Post by Victormd on 2008-04-22
This link tells me why it didn't work...
> Now, assuming that you have an ssh server running on a remote machine
I don't have an ssh server running... I think I misled you guys when I said my files were on a server... actually it's an XP box that I use for data backup and to connect/share printer and scanner that's on all the time...

---

### Post by _oOMOo_ on 2008-04-22
You can access Windows shares with Samba. If in XP you right click on the folder and select "Share this folder" (or something similar), in Ubuntu you should be able to see the share by browsing Places>Network>Windows Network>MSHOME or whatever your Windows box called it.

More here, including some stuff about mounting the share permanently [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")

---

### Post by Victormd on 2008-04-22
Yeah, I have that already. Furthermore, I have a link to the mp3 folder on my ubuntu desktop, the only problem is that I can't direct Amarok to it...

---

