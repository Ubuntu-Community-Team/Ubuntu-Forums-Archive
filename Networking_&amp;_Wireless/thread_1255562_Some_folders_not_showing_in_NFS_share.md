---
title: "Some folders not showing in NFS share"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by w00ly on 2009-09-01
Ok I've got NFS setup and my share mounts without giving any errors. When I go to the mount directory I can see the files in / that I've shared but I cant see any folders on an externally mounted or anything in the home directory. Anybody know why? I set chmod 777 to the external HD's directory but that didnt help:
/etc/exports:
[quote=/etc/exports]/ 192.168.2.0/24(rw,no_root_squash,async,no_subtree_check)[/quote]

client:
> root@woolybox:/mnt# mount 192.168.2.100:/ /mnt/nfstest
root@woolybox:/mnt# cd nfstest/media/NewHD/
root@woolybox:/mnt/nfstest/media/NewHD# ls
root@woolybox:/mnt/nfstest/media/NewHD#
root@woolybox:/mnt/nfstest/media/NewHD# cd ../../home/
root@woolybox:/mnt/nfstest/home# ls
root@woolybox:/mnt/nfstest/home#
How do I fix this? Thanks in advance!!

---

### Post by scorp123 on 2009-09-01
> **w00ly said:**
> 
/etc/exports:
```
**[COLOR="Red"]/[/COLOR]** 192.168.2.0/24(rw,[COLOR="Red"]**no_root_squash**[/COLOR],async,no_subtree_check)
``` *That* is **_[COLOR="Red"]extremely unsafe[/COLOR]_** ... are you *sure* you know what you're doing?

> **w00ly said:**
>  but I cant see any folders on an externally mounted or anything in the home directory.  NFS doesn't cross filesystem boundaries. You shared "/" (**extremely unsafe** in my opinion!!) and that's where the export stays.

If you want access to other file systems too, you'd have to create separate exports for them as well.

But may I ask what it is that you're trying to achieve?? The way you're using NFS is begging for trouble to happen ...

---

### Post by w00ly on 2009-09-01
There's media that i'm sharing both on an external hard drive and in the home directory. I also want to share devices such as dvd burners and seamless integration within the OS so that my devices appear as they're local on either system

Thanks for answering my question though! Since the external drive is VFAT I wont be using NFS. Am I stuck with samba? What about SSHFS? Is it faster than samba?

---

### Post by scorp123 on 2009-09-01
> **w00ly said:**
>  Since the external drive is VFAT I wont be using NFS. Am I stuck with samba? What about SSHFS? Is it faster than samba? I fail to see the correlation between NFS (network layer) and whatever filesystem is on that harddisk ???  If you can mount it you can export it via NFS. To the other end of the network it's NFS. And just that. 

But I highly recommend NOT doing what you're doing. One accidental drag & drop in the wrong places, one glitch, one small crash, and your installation is hosed.

I fail to see any sane reason why anyone would ever need to export "/" with that "no_root_squash" option turned on??? ](*,)

But hey, it's your system ... Just don't come crying, OK? :D

As for SSHFS: I'd clearly recommend that one over NFS or SAMBA. It's secure, it's safe, it's encrypted and you can easily operate it from your "Gnome" desktop if you so wish (remote SSHFS locations appear as folder icons on your desktop). And it's far less complicated to configure. All you need is a valid system user account + password on the remote end (SAMBA requires a lot more and has its own password back-end which for the average user usually has more disadvantages than advantages ... it's confusing to most).

---

### Post by w00ly on 2009-09-01
> **scorp123 said:**
> I fail to see the correlation between NFS (network layer) and whatever filesystem is on that harddisk ???  If you can mount it you can export it via NFS. To the other end of the network it's NFS. And just that. 
lol I misinterpreted what you said about nfs not being able to cross file system boundaries..most of this is over my head.. :oops:

> **scorp123 said:**
> But I highly recommend NOT doing what you're doing. One accidental drag & drop in the wrong places, one glitch, one small crash, and your installation is hosed.

I fail to see any sane reason why anyone would ever need to export "/" with that "no_root_squash" option turned on??? ](*,)

But hey, it's your system ... Just don't come crying, OK? :D

I dont know what no_root_squash does...it was just in there because it was in the guide I was reading. The only reason I used / is because I wanted to be able to access the whole system remotely

> **scorp123 said:**
> 
 As for SSHFS: I'd clearly recommend that one over NFS or SAMBA. It's secure, it's safe, it's encrypted and you can easily operate it from your "Gnome" desktop if you so wish (remote SSHFS locations appear as folder icons on your desktop). And it's far less complicated to configure. All you need is a valid system user account + password on the remote end (SAMBA requires a lot more and has its own password back-end which for the average user usually has more disadvantages than advantages ... it's confusing to most).
Yea it definitely seemed much easier to configure...what about speed, is it faster than samba? Thanks for the recommendation :D

---

### Post by Warren Watts on 2009-09-01
> **w00ly said:**
> lol I misinterpreted what you said about nfs not being able to cross file system boundaries..most of this is over my head.. :oops:


Here's a link to an explanation of how path names are evaluated with NFS.


[Using symbolic links with NFS]("http://ou800doc.caldera.com/en/SDK_sysprog/_Using_Symbolic_Links_with_NFS.html")

Perhaps that will explain it a little better for you

---

### Post by scorp123 on 2009-09-02
> **w00ly said:**
>  I dont know what no_root_squash does... Why did you configure it then that way???

[B]Always know *[COLOR="Red"]what[/COLOR]* you're doing and *[COLOR="Red"]why[/COLOR]*!!  Don't follow guides blindly!! _[COLOR="Red"]THINK.[/COLOR]_
[/B]


Read the explanation regarding "no_root_squash" here please:
[http://ubuntuforums.org/showpost.php?p=4184680&postcount=122](http://ubuntuforums.org/showpost.php?p=4184680&postcount=122)


"no_root_squash" may make sense if you are operating a server that has home directories stored on it .... But you definitely never ever export "/" with that option turned on!!

Anyone posing as super-user "***root***" on the network could now *_easily_* gain full control over that system and manipulate it in whichever way he wishes.

If you want to be able to easily and safely browse your remote computer, why not simply use SSH from within your file browser?

Open Nautilus (the file manager) (***Places > Home Folder***), click that "Pencil" icon in the upper left corner, underneath the "***File***" menu. Now you should see the "Location" text field and you should be able to type in adresses ... So now, simply type a SSH URL into this, e.g.

***ssh://youruser@remote-server***

Taddaaaaa .... Your browser will display the contents of the remote machine.

Just don't do this as "root" (same problem as above: one accidental click in the wrong places and strange things happen).

The advantage of this method:
[LIST]
[*]It's easy. Nothing to export, nothing to configure. Just install "openssh-server", that's it
[*]It just works
[*]It's easy to use
[*]It's safe for as long as you don't do this with the "root" account
[/LIST]

---

