---
title: "File Sharing- Mac &amp; Xubuntu"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Linux BASHer on 2010-03-10
I want to share files/folders between my Mac (running Snow Leopard) and Xubuntu. I can connect them directly with an Ethernet cable or with a router as an intermediate. What would be the simplest way to share files/folders between the two machines? What type of file sharing would be best and how do I access the content?

---

### Post by johnson.d on 2010-03-10
NFS would be a simpler file sharing method as you are connecting Xubuntu with mac.

1) When you Mac is the NFS server

   You can configure NFS in a Mac using the following link:

   [http://www.behanna.org/osx/nfs/howto1.html](http://www.behanna.org/osx/nfs/howto1.html)

   You can access this share from a Xubuntu machine using the following command

   ```
$ sudo mount -t nfs <ip-address>:/<share-path> /<mount-point in the local machine>
```

2) When your Xubuntu acts as a NFS server

   You can Install NFS server in Xubuntu using the following command:

   ```
$ sudo apt-get install nfs-kernel-server
```

   You can now edit the /etc/exports file to configure the shares. Append  the following lines to the file:

/<share-path> *(rw,sync)

   After adding the line restart the NFS by using the following command:

   ```
$ sudo /etc/init.d/nfs-kernel-server restart
```

   For accessing the share from a Mac the following link would be useful:

   [http://docs.info.apple.com/article.html?path=Mac/10.6/en/8198.html](http://docs.info.apple.com/article.html?path=Mac/10.6/en/8198.html)

---

### Post by Morbius1 on 2010-03-10
First I don't use Xubuntu so keep that in mind. ;) You also stated you wanted the "simplest way".

My wife has a MacBook and I have sharing working in one direction using Nautilus-share ( Samba ). The share is on my linux machine and she has no problem mounting it in Finder.

The package that makes this happen in Gnome is called Nautilus-shares. I believe that for you it's called Thunar-shares. The process of setting up a share on linux is simple enough:

Open Nautilus ( Thunar )
Right click on a folder you own
Select "Sharing Options"
Mark any or all of the 3 boxes
Select "Create Share"

I haven't tried to create a share on the Mac. My wife won't let me anywhere near it. ;)

---

### Post by Linux BASHer on 2010-03-15
Thank you for the replies.

I don't know why I was having so much trouble networking these two, but when I opened a Finder window to do something unrelated, I was surprised to see the Ubuntu share I had created using Shared Folders control panel in the System menu reflected in the window sidebar. Perhaps it simply needed a restart or a plug/unplug. Initially, I still had trouble accessing the share (in spite of seeing it), but deleting and recreating it was the fix.

I gotta admit, I am very happy with this development. It means I can actually share files via the GIU if I wish. I was prepared to get my hands dirty with the terminal (which I still might do), but I'm glad I don't have to for this simple task. It speaks for the growing versatility of the Linux GUI (even in XFCE).

---

