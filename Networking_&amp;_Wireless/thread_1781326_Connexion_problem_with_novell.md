---
title: "Connexion problem with novell"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by sweq on 2011-06-13
**[Connexion problem with novell]("http://forums.linuxmint.com/viewtopic.php?f=157&t=74664#p433136")**

             [[IMG]http://forums.linuxmint.com/styles/linux-mint/imageset/icon_post_target.gif[/IMG]]("http://forums.linuxmint.com/viewtopic.php?p=433136&sid=4beafcdd9a50f4da213df87b1cbc8efd#p433136")by **[sweq]("http://forums.linuxmint.com/memberlist.php?mode=viewprofile&u=60720&sid=4beafcdd9a50f4da213df87b1cbc8efd")** on Fri Jun 10, 2011 12:10 pm 
                            Hi,

I'm having some issue with Ubuntu 11 to connect to a Novell server.

The Novell's server version is 5.1, I know, it's very old, but still, we are on it.

The  issue is : every time I mount the remote disk with this server, I can  access it once, in cmd, then, if I try a second time, it's seem to jam  in a loop or waiting for something that not come...  If I try with  nautilus, nautilus crash.

With windows system, there is no problem.  Also, with Ubuntu 10, it's work like a charm.

I'm wondering what are the change between Ubuntu 10 and Ubuntu 11 about the connexion?

Here the step I do to make it to "work" :
[I]sudo apt-get install libpam-mount
wget [http://archive.ubuntu.com/ubuntu/pool/u ... 3_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/n/ncpfs/ncpfs_2.2.6-4ubuntu3_i386.deb")
sudo apt-get install ncpfs
sudo aptitude hold ncpfs
sudo sh -c 'echo "ncpfs hold"|dpkg --set-selections' [/I]       #We are stuck with this version because newer version don't work.

After that I change all those :
*sudo sh -c "echo '@include common-pammount' >> /etc/pam.d/gdm"*
I create the file /etc/pam.d/common-pammount and I write in : 
[B]auth       optional   pam_mount.so
session    optional   pam_mount.so[/B]

Then I add 
[B]<ncpmount>/usr/bin/ncpmount  -S %(SERVER) -A %(SERVER) -V %(VOLUME) -U [user alias] -y utf8 -o  pass-fd=0,tcp -u %(USER) %(MNTPT)</ncpmount>
<ncpumount>ncpumount %(MNTPT)</ncpumount>
<[authentification password]>Password :</[authentification password]>
<volume user="*" fstype="ncpfs" server=[server name] path=[path] mountpoint=[mount point] options=[some options]/>[/B]


And finally I manually create the directory on my /, change the mode that everybody can use it, then I mount it with that :
[I]sudo mkdir [mount point]
sudo chmod -R ugo=rwx [mount point]
sudo  -S /usr/bin/ncpmount -S [server name] -A [server name] -V [path] -U  [user alias] -y utf8 -o pass-fd=0,tcp -u $currentUser [mount point] -P  $password[/I]


Is there something wrong with all that?

Thanks in advance for your help.

Sweq

---

