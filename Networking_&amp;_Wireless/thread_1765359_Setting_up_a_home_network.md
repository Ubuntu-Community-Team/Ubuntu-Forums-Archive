---
title: "Setting up a home network"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by MOGuy78 on 2011-05-23
I have 4 computers at home: 1 XP, 1 Laptop w/ Win7, 1 Mac, and 1 Ubuntu (hey, I like to try most everything).  Anyway, I'm wanting to set up a home server to save everything on so that I don't have 3-4 copies of one file floating around.

I was planning on using Ubuntu because I've always heard that Linux is a good system for a server and that Ubuntu is one of the easiest to work with.  Anyway, I just installed the Ubuntu OS, and the only software that I installed with it was Samba (I don't have a printer hooked up to this computer).  Is samba the best software to use for this, or is there any other option that would be easier to use?  I've heard that with samba there are a lot of things you have to change using the CLI (something about chmod, whatever that is, and others like it), which doesn't bother me, I've used CLI since the years before Windows, good ol' DOS.  But I've also heard from a few friends and they say that an app called Webadmin works pretty well, and you don't have to make many changes actually using the CLI).  Has anybody heard of it, and is it any good?  Is it an easier way to change settings and create a network with?

---

### Post by boldford on 2011-05-23
You mean Webmin. It allows you to access your (usually CLI based) server from a broswer. It means your server can be headless and tucked away in a cupboard.

That's pretty much what I've put together for a similar mixed environment. I've had some support from users here but, as a newbie to linux, still need more.

---

### Post by MOGuy78 on 2011-05-24
Thanks for the info.  Do you know if you still have to set the attributes to the shared directories through the CLI so they can be accessed by anyone, or can you do it through Webmin?

---

### Post by rbishop on 2011-05-24
You can control and do everything via Webmin.

---

### Post by Bucky Ball on 2011-05-24
Just throwing this in before you get too far ...

You are advised to go for a long-term support release for a server for stability and long support, the current one being 10.04 LTS. Supported until 2015. ;)

Good luck. I am thinking of getting network storage myself in the near future in the form of a couple of raid drives plugged into the router.

---

### Post by MOGuy78 on 2011-06-02
Thanks for the info.  My other question is about access.
Since all I'm going to use it for is a file server, not a web server or anything like that, I only want my home network to be able to access the server.  In fact, after I get everything set up, the Ubuntu Server itself, Webmin, etc., I would like to fix it so that it can't access the internet at all, incoming or outgoing, only accessed from my home network. Is there a way that I can do this?  My connection to the internet is through a DHCP connection, if anyone needs to know.

---

### Post by jhardydj on 2011-06-02
Installing Samba and using the default config will get you well on your way.  edit smb.conf and look at the "shares" section.

Best way for sharing files (IMO) is to have a partition such as /media/files then subfolders Downloads, torrents, Movies etc.. then in your smb.conf have something like

[Files]
comment = File Server
path = /media/files 
browseable = yes
writeable = yes
valid users = someuser

Now you can make it read only or whatever.. just read the help files for Samba. 

That should get you started anyhow.

---

