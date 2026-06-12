---
title: "trouble sharing files"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by Pro$pect on 2012-02-24
I have Ubuntu 11.10 running on my desktop and laptop. I installed samba and selected some folders I wanted to share, but when I go to browse network on my desktop nothing shows up. On the laptop it shows an Ubuntu network but only shows the files i'm sharing on that computer. Both computers can ping each other so I don't understand what the problem is?

---

### Post by Morbius1 on 2012-02-24
See how far this gets you: [http://ubuntuforums.org/showthread.php?t=1930381](http://ubuntuforums.org/showthread.php?t=1930381)

In addition to the steps I mentioned in that thread you might want to add one more:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section - under the workgroup line so you remember that you did it :
```
name resolve order = bcast host lmhosts wins
```Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```

Do all these things on both machines.

---

### Post by JRV on 2012-02-24
See my tutorial on how to set-up networking between two Ubuntu systems using ssh and SFTP.

[http://ubuntuforums.org/showthread.php?t=1900551](http://ubuntuforums.org/showthread.php?t=1900551)

You don't need to do anything with samba unless you need to share a folder on your Ubuntu system with one running Windows.

This works if you have not messed this samba at all, I don't know if it will work if you have.

---

### Post by Morbius1 on 2012-02-24
> You don't need to do anything with samba unless you need to share a folder on your Ubuntu system with one running Windows.I've never quite understood why ssh comes up when discussing file sharing on a LAN. I use SSH myself when I want access to another machine on my lan and that user allows that sort of thing to happen. And it certainly can be used for file transfer but it's not in the same category as Samba or even NFS.

I can create a share of one solitary folder and only one folder using samba. I can restrict who can read and write to that folder. I can prevent an otherwise credentialed user from accessing that share unless he is trying to access it from a specific ip address or host.

In this particular topic the 2 machines in question could very well be owned by the same user so it really doesn't matter what protocol he uses - and there is no denying it - ssh is easier to set up. But in a setting where there are different users on different machines on the LAN, SSH gives the client at a minimum read access to your entire box. Two different protocols used traditionally for two different purposes.

---

