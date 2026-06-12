---
title: "Creating a Static network mount between Ubuntu systems"
date: 2009-09-20
forum: Networking &amp; Wireless
---

### Post by beastrace91 on 2009-09-20
Hey There,

So I currently have a 32bit Ubuntu VM setup on my 64bit system. My two systems can see each other through my network and I want to easily share files between them. How can I go about creating a static mount point for a Data folder I have shared on my systems?

~Jeff

---

### Post by falconindy on 2009-09-20
Either nFS or smbFS will work. smbFS is probably easier to setup.

[http://www.debian-administration.org/articles/165](http://www.debian-administration.org/articles/165)

---

### Post by beastrace91 on 2009-09-20
EDIT: Solved my own issues, it was listed in the above posted guide link - just needed to add an fstab entry.

~Jeff

---

### Post by beastrace91 on 2009-09-20
Alrighty so this command successfully mounts the share how I want it - ```
mount -t smbfs -o username=jeff,password=APASSWORD //sager-lintop/storage /mnt/Data
```

How ever I cannot get the fstab entry to work, here is the line I added - ```
//sager-lintop/storage /mnt/Data smbfs defaults,user,username=jeff,password=APASSWORD 0 0
```

What am I doing wrong?

~Jeff

---

### Post by tlarkin on 2009-09-20
You could have init.d run that script at start up so it is already mounted exactly where you want it to be.

---

### Post by beastrace91 on 2009-09-20
Everything init.d is run at start up? I guess that will work but I'd still like to know why that fstab entry does not work.

~Jeff

---

### Post by tlarkin on 2009-09-20
> **beastrace91 said:**
> Everything init.d is run at start up? I guess that will work but I'd still like to know why that fstab entry does not work.

~Jeff

Not exactly, you have to tell init.d to run it at start up.  If you google it, you should find some tutorials that are pretty simple and straight forward.

fstab can be fickle, and I have had issues where sometimes I can add entries by UUID and other times UUID would not work and I had to use volume names.

I don't know why your fstab is not working, sorry.

---

### Post by theozzlives on 2009-09-20
If you're talking about a static local IP, most routers have a LAN setup where you can setup the router as a DHCP server and assign an IP to each computer. Like my laptop is 192.168.1.4, and my test box is 192.168.1.3. My ISP has assigned me a static IP that is setup in my router to forward port 80 to my web server (192.168.1.6).

---

### Post by beastrace91 on 2009-09-20
Can't I create a mount based on the name of the system? This is what I would prefer... As I would like to use on multiple networks as this is a laptop.

~Jeff

---

### Post by tlarkin on 2009-09-20
> **beastrace91 said:**
> Can't I create a mount based on the name of the system? This is what I would prefer... As I would like to use on multiple networks as this is a laptop.

~Jeff

Only if you have DNS up and running and it works.

---

### Post by scrooge_74 on 2009-09-20
You need to install nfs-kernel-server on the machine that has the data, then you declare the folder or drive in /etc/exports

From then on you can declare that network drive in the fstab of other PCs so they can mount them at will or automatically

Here is a good thread about it [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)


Rember the server needs a static address so this will work. This way is a lot simpler/secure than using samba which is for interacting with XP

---

