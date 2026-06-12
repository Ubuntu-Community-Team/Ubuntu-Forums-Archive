---
title: "How can I get my Ubuntu PC to show up on a Windows Workgroup?"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by grs on 2008-12-21
I'm having trouble getting my Ubuntu Studio PC to show up on my Windows XP PC under:

My Network Places-Entire Network-Microsoft Windows Network-MSHOME

I don't have any Samba shares setup on the Ubuntu PC, should there be an icon to show the Ubuntu PC is at least connected to the workgroup?

---

### Post by untappedpilot2 on 2008-12-21
You need to setup Samba to share files between Ubuntu and Windows. Open Applications > System > Shared Folders (This might be a little different for you, I use Xubuntu.) and it will prompt you to install Samba and NFS. You can install NFS as well if you want but for networking with Windows you only need Samba. Then setup a shared folder so Windows can see it. You're also going to need to edit your smb.conf file and use: 
```
smbpasswd -a
```
...to setup your username and password for accessing your shared folder from Windows. Here are some links to get you going:

[http://samba.netfirms.com/]("http://samba.netfirms.com/")

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")


-I think this first one is the one I used when I first setup Samba. It does a pretty good job of walking you through the entire process to get you networked with your Windows machine. I put the other one as well because it does a better job of explaining certain aspects of getting Samba setup. (I think it was the smbpasswd portion.) Good Luck!

---

### Post by grs on 2008-12-21
Thanks.

Can it be done without having to setup users and passwords? I have a Samba server setup running Clarkconnect (Red Hat) I know I can setup it up so that the Pc shows on the network even though there maybe no share active.

---

### Post by untappedpilot2 on 2008-12-21
As far as my Samba experience goes you need to setup the shared folder and then at least setup a username. Basically you do: 

```
sudo smbpasswd -a
```
...and enter a username then leave the password blank. (Hit enter twice.) Then when you try to access your shared folder from Windows it will prompt a login screen where you enter your username and password. So you might as well setup a password.

---

