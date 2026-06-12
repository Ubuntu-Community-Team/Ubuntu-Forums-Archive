---
title: "Commands for &quot;Connect to Server&quot;"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by jamesclish on 2009-04-30
Hi all

For the last few months, I've been connecting to a shared documents folder on my mac through ubuntu's "Places>Connect to Server..."

My options are as follows:
Service type: Windows share
Server: mymacsip
Share: documents
User Name: myusername
Workgroup: WORKGROUP (I never bothered to change it...)

A prompt then comes up asking for my password, which shall be "mypassword".

I have to configure these options every time I log in, in order to mount my mac's documents folder.

Does anyone know the commands for this setup that I can put into a shell script that I can run at logon? Any other ways I can do this?

I tried creating an alias (sorry, "*link*" in ubuntu...) to the networked folder, but Ubuntu so kindly informed me that links are only for local files and folders...

I hate to tell you, but Windows was much more cooperative on this one... Just had to "Map network drive" and it's assigned a drive letter!

Thanks in advance!

---

### Post by bladeswords on 2009-04-30
Yeah, you can put this in a shell script and have it exeute at startup.  This will also mount the share as if it is local, so you will be able to go to /mnt/document/ and use it as if it were local.

You could follow this guide...if you feel like it, but it seemed like too much hassle [https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

What I prefer though is...

```
sudo mkdir /mnt/documents

gksudo mount -t cifs //192.168.1.102/documents /mnt/documents --verbose -o user=username,password=Password
```

You can also make a file to contain your credentials.  

Simply make that a script and add it to your login scripts and you should be fine.

---

### Post by coutts99 on 2009-04-30
Why not put it in /etc/fstab and have it mount on boot?

---

### Post by bladeswords on 2009-05-06
Either way.  I was just thinking if you have multipul users on the system, or that you don't need it mounted at all times.

---

