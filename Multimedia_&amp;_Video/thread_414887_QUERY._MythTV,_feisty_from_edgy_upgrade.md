---
title: "QUERY. MythTV, feisty from edgy upgrade"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by bowmanr on 2007-04-20
Hi,

Just wondered ... any advice on updating my edgy based MythTV Combined Backend/Frontend?? System set up following the instructions at <<https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend>>.

There's nothing I can find at <<https://help.ubuntu.com/community/MythTV_Feisty>> that specifically talks about upgrading, just talking about installing.

Is there any word on a recommeded way of upgrading to fiesty please? 

Looking at <<http://www.ubuntu.com/getubuntu/upgrading>> reveals three basic methods :

1) GUI
     -- this box does not have GNOME installed, just OpenBox
     ?? need to '$ sudo apt-get install update-manager-core' and then '$gksudo update-manager'?

2) Server 
     ?? will this do the GUI components aswell as the server components?

3) Via Alternate CD
     ?? will this perform basic upgrade and then complete with standard '$sudo apt-get update' followed by '$sudo apt-get upgrade'

Any tips please? I'm a bit frightened to just try one method in case I break the box (yes, I know, someone has to give it a go!! -- but it's my _only_ MythTV box and the family will kill me if it heads south for several days!!)

Thanks very much for any insight someone may offer

Robert

---

### Post by bnuytten on 2007-04-20
I kind of "upgraded" from Edgy to Feisty yesterday. I installed Feisty beside Edgy. Had to fiddle with the /boot partition but now I can boot both of them. I still have my working Edgy and mythtv. Mythtv works fine on Feisty as far as I can tell. I keep getting crashes from my Hauppauge PVR-500 for the moment...

If you\re interested in this approach, here are the steps in short:
[LIST=1]
[*]make a backup copy of your Edgy /boot
Feisty setup requires you to format the /boot partition for some awkward reason
[*]install Feisty on a different partition
I just used the desktop cd
[*]boot Feisty
[*]copy the Edgy kernel, initrd, config, abi, System.map from the backup location to /boot
```
ls -l /boot/
total 25942
-rw-r--r-- 1 root root  285721 2007-04-19 14:27 abi-2.6.17-11-generic
-rw-r--r-- 1 root root  414210 2007-04-15 10:07 abi-2.6.20-15-generic
-rw-r--r-- 1 root root   74707 2007-04-19 14:27 config-2.6.17-11-generic
-rw-r--r-- 1 root root   83234 2007-04-15 07:33 config-2.6.20-15-generic
drwxr-xr-x 2 root root    1024 2007-04-19 14:30 grub
-rw-r--r-- 1 root root 5722112 2007-04-19 14:27 initrd.img-2.6.17-11-generic
-rw-r--r-- 1 root root 7670147 2007-04-19 23:16 initrd.img-2.6.20-15-generic
-rw-r--r-- 1 root root 7162750 2007-04-19 14:05 initrd.img-2.6.20-15-generic.bak
drwxr-xr-x 2 root root   12288 2007-04-19 13:50 lost+found
-rw-r--r-- 1 root root   94600 2007-04-19 14:27 memtest86+.bin
-rw-r--r-- 1 root root  729932 2007-04-19 14:27 System.map-2.6.17-11-generic
-rw-r--r-- 1 root root  806942 2007-04-15 10:08 System.map-2.6.20-15-generic
-rw-r--r-- 1 root root 1635958 2007-04-19 14:27 vmlinuz-2.6.17-11-generic
-rw-r--r-- 1 root root 1745100 2007-04-15 10:07 vmlinuz-2.6.20-15-generic

```
[*] append this to /boot/grub/menu.1st
check the backup copy of menu.1st for differences!
```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd          /initrd.img-2.6.17-11-generic
boot

```
[/LIST]

---

### Post by bowmanr on 2007-04-20
Just some info, if anyone is interested -- I had a quick try at installing and running 'update-manager' , hoping to leave it going whilst sorting out the garage, no good ...

 I got some strange message about not having an appropriate metapackage installed to allow the upgrade-manager to do it's job. All rolled back ok, no ill effects. Can't remember the message precisely, but I recall it said that the updater needs either the GNOME or KDE metapackage installed.

Been in the garage for a while, back now, thought I'd best post what happened ...  Oh well, some more garage sorting out beckons, so I'll look closely at bnuytten's comments (thank you, bnuytten, for your response) later and see what to do.

Thanks 
Robert

---

### Post by superm1 on 2007-04-20
Using update-manager isn't a good idea if you are not using a desktop install.  It starts putting lots of extra packages you won't need.

You should follow the update procedure that is done non-gui:

```
**Network upgrade for Ubuntu servers (recommended)**

 If you run an Ubuntu server, you should use the new server upgrade system. 
 [LIST=1]
[*] Install update-manager-core:  
 sudo apt-get install update-manager-core
[*] Launch the upgrade tool:  
 sudo do-release-upgrade
[*] Follow the on-screen instructions
[/LIST]
```
I did this on one of my edgy servers during herd5 to go to Feisty, and things went well.
[B]
[/B]

---

### Post by bowmanr on 2007-04-20
Thanks for the tip ... I wonder ...


Please, which repository needs adding? I just get 

E: Couldn't find package update-manager-core

with this sources.list

<snip>
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware
</snip>

Thanks
Robert

---

### Post by superm1 on 2007-04-20
> **bowmanr said:**
> Thanks for the tip ... I wonder ...


Please, which repository needs adding? I just get 

E: Couldn't find package update-manager-core

with this sources.list

<snip>
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://dl.ivtvdriver.org/ubuntu](http://dl.ivtvdriver.org/ubuntu) edgy firmware
</snip>

Thanks
Robert
*Should* be in main.  At the time I did it, it was in edgy-proposed.  I'll poke around and see whats up with this.

---

### Post by bowmanr on 2007-04-20
Ok. As long as I've not got something _really_ silly in my sources file.

Superm1, thank very much for your advice, and prior experience, in using the server method of update. I'll try it again in a few days when the dust has settled a little more.

Thanks
Robert

---

### Post by bowmanr on 2007-04-21
Package now available ...

Here goes...

Thanks for the tips and advice
Robert

---

### Post by bowmanr on 2007-04-23
Just thought I'd better report back for anyone else in a similar situation ... got MythTV hapilly running on Edgy installed using the Ubuntu community HOWTO and now want to upgrade to Fiesty.

The server update method (in my case) is the way to go. Took a while, but, as far as I can tell thus far, all is still fine. 

  $ sudo apt-get install update-manager-core
  $ sudo do-release-upgrade 

Had to rebuild LIRC, but you'd expect that after a kernel change. IVTV was just there, no need to rebuild it. Seem to have acquired an updated nvidia driver too.

SuperM1 .... thanks very much for your help.

A very relieved
Robert

---

