---
title: "Help mounting windows share on network ??"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by mojo82379 on 2011-01-01
Can someone please help?  I have a network PC running Win7 that u use for storage of all my media; movies, music and pictures.  I can connect and use the share just fine using the "connect to server" option under places menu.  I think i need to modify the fstab file but I am not familiar enough with it to do this.  Have searched other threads for help but I am doing something wrong.

HP Laptop running Ubuntu 10.10 connecting to a win7 share through a router.

---

### Post by mojo82379 on 2011-01-01
sorry left out some info, the problem I am having is that I cannot open any of the remote files when connected to the server.  I does not show in the "open file" dialog when tring to open a file using amarok or mplayer?  TIA :-)

---

### Post by MrDetermination on 2011-01-01
What does not show?  The file or the directory?

Can you open a file explorer window and type:
\\Server\directory

in the address bar and get somewhere?

Can you write files in there from Windows?

---

### Post by mojo82379 on 2011-01-01
I can access files, read\write in file explorer, I am trying to setup my music collection in amarok.  there is no address  bar to type in. so the share must need to be mounted in the filesystem right?

---

### Post by Morbius1 on 2011-01-01
> **mojo82379 said:**
> sorry left out some info, the problem I am having is that I cannot open any of the remote files when connected to the server.  I does not show in the "open file" dialog when tring to open a file using amarok or mplayer?  TIA :-)
I may be misinterpreting you post but ....

When you connect to the  remote windows share using Nautilus or "Connect to Server" the share is mounted in a "hidden" directory because the developers are cruel and heartless creatures. The "hidden" directory is here:
```
/home/mojo82379/.gvfs/share_name on server_name
```In order to see the hidden directory in mplayer etc.., you need to right click on an open space in the "open file" dialog box and select "Show hidden files".

---

### Post by mojo82379 on 2011-01-01
ok, that does help, but i still can't access it in amarok because it is hidded.  can I change it to not be hidden?  or is there a way to mount it in the media folder or something?

---

### Post by Morbius1 on 2011-01-01
You can create a symbolic link from the hidden folder to a "real" folder:

Create a directory called say ... WinShare
```
mkdir /home/mojo82379/WinShare
```THen create a symlink to that folder:
```
ln -s /home/mojo82379/.gvfs/"share_name on server_name" /home/mojo82379/WinShare
```

---

### Post by mojo82379 on 2011-01-01
Were getting closer :-)  That does put  a symbolic link in-to the dir, but when i click on it it says it's broken :-(  I also tried making a link using Nautilus and it wouldn't let me do that either..

---

### Post by Morbius1 on 2011-01-01
Did you "connect to server" first? It's a two step process.

---

### Post by mojo82379 on 2011-01-01
I "connect to server" at boot, so it is always connected.  I've seen many posts referring to mounting it using fstab, but I don't know enough syntax to get the job done...

---

### Post by Morbius1 on 2011-01-01
And how do you "connect to server" on boot.

---

### Post by mojo82379 on 2011-01-01
OOOPPS!! I wrote the command wrong the first time.  I forgot one of the " .  Retry and works good!! Amarok is setting up my library now.  THANK YOU for all the help!!!  fantastic!! :-)

---

### Post by mojo82379 on 2011-01-01
> **Morbius1 said:**
> And how do you "connect to server" on boot.

I run a .bat that has the gvfs command in it from the startup applications, i had to add sleep 20 previous to that to allow the wireless network to connect first though. Kinda backwards but it works :-)

---

### Post by PatchesTheCaveman on 2011-01-01
The correct method would be to add a line to your /etc/fstab file:
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by Morbius1 on 2011-01-01
When you've got nothing else to do you might want to check out Gigolo:
[http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

It's a GUI front end to gvfs-mount smb:// that can be used to automount. One nice thing about it is that it can be set to probe the network at user defined intervals and mount the remote share when it's available. So if covers those kinds of situations where the network is not up yet or the remote machine is not turned on yet.

If you only have one remote share then the script method works well enough and there's no point in using other methods but if you have a lot Gigolo may come in handy.

---

### Post by Morbius1 on 2011-01-01
> **PatchesTheCaveman said:**
> The correct method would be to add a line to your /etc/fstab file:
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)
You know, I used the fstab method forever then things got messy. The line in fstab would be executed before the network was up for example ( and _netdev no longer worked ). On the shutdown side of things the network would go down before the remote share would unmount and the system would stall on shutdown.

I started using gvfs-mount scripts and then I found Gigolo and that's pretty much all I use these days.

---

