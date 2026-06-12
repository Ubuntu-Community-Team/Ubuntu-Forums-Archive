---
title: "Vista shared folder access please"
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by knottshawk on 2009-09-18
I've got Ubuntu 8.10 on a network with Vista. I've shared folders in Vista and the only ones I can access are the "Public" folders in Vista. If I set others to be shared, like my Users directory, I can see it in the Ubuntu networking section, but no matter what I do I cannot gain entry. 

So far I've tried adding a new connection every which way I can think, but I get "cannot display location smb://my-pc/users connection timed out".

I've also tried the following, which I've seen in other threads:

```
sudo mount -t cifs //my-pc/Users/me /home/me/MyMountedVista
```

Which seems to work, but then when I try to access the mount it says 'You do not have the permissions necessary to view the contents of "MyMountedVista"'

What gives?

---

### Post by knottshawk on 2009-09-18
..

---

### Post by badger_fruit on 2009-09-18
Try this ...

```
sudo mount -t cifs //my-pc/Users/me /home/me -o VistaUsername -p VistaPassword
```Mounts the share as the VistaUsername using the Vistapassword; should give you all the access that Vistausername enjoys locally on the machine.

```
sudo apt-get install samba
```
If i recall correctly, should update your SMB to the latest version available in your package repos.
I think ;)

---

### Post by knottshawk on 2009-09-18
I don't have a Vista username/password... :S

I'm not sure how to update SMB... any tips? This is a new install of ubuntu, so I assumed we'd be all updated already. I think my Samba is 3.2.3 or something.

---

### Post by prasad.bh1 on 2009-09-18
first search the window partition, #fdisk -l
in my case, it is /dev/sda2
make directory here like windrive under /mnt
and run this command


[#mount -t ntfs /dev/sda2 /mnt/windrive -o “umask=022&#8243;]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

---

### Post by knottshawk on 2009-09-18
> **prasad.bh1 said:**
> first search the window partition, #fdisk -l
in my case, it is /dev/sda2
make directory here like windrive under /mnt
and run this command


[#mount -t ntfs /dev/sda2 /mnt/windrive -o “umask=022&#8243;]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

I don't really know what you mean... more specifics please.

Also, on some shares I don't get the aforementioned error, but rather just get a black directory when I browse to the mounted windows share.

---

### Post by badger_fruit on 2009-09-18
> **prasad.bh1 said:**
> first search the window partition, #fdisk -l
in my case, it is /dev/sda2
make directory here like windrive under /mnt
and run this command


[#mount -t ntfs /dev/sda2 /mnt/windrive -o &#8220;umask=022&#8243;]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")


According to the original post, the Vista machine is on a seperate PC all together (\\my-pc\) .  The commands I quote above will only show any Windows partitions on the SAME computer as Ubuntu is installed.  This is why your newly mounted folder is blank. It does not exist

As for not having a Vista username and password, perhaps this is why it is failing!
I would check by (on Vista machine) Right click My Computer > Manage > Users and Groups > Users

Or check in the C:\Users folder for folder names (again, on the Vista machine).

There will be at least one user in there (Administrator) which you may be using to log in to Vista (auto logon?)  Try

```
sudo mount -t cifs //my-pc/Users/me /home/me -o VistaUsername
```If asked for a password by terminal, just leave blank and hit enter.



Oh wait, I also notice you're trying to mount a folder not a share .... "**//my-pc/users**" instead of "**//my-pc/users/username/**"  may work

---

### Post by knottshawk on 2009-09-18
BRILLIANT! Badger, you were right on... I assumed I didn't have to include my vista username since I don't use logons or require passwords for folder access. It works like a charm now! Thanks so much! ;)

---

### Post by badger_fruit on 2009-09-18
> **knottshawk said:**
> BRILLIANT! Badger, you were right on... I assumed I didn't have to include my vista username since I don't use logons or require passwords for folder access. It works like a charm now! Thanks so much! ;)

You're very welcome! I am pleased that my advice has helped!
/dons "hat of pride" and goes back to the dark place ...


By the way, this will create the mount only until you reboot (or perhaps log out).
For a permanant solution, add the line to your /etc/fstab

```
//my-pc/user  /folder/to/mount/into cifs    auto,uid=local_ubunutu_username,gid=users,_netdev    0    0
```

I can never remember what the 0 0 at the end means lol but the rest should be pretty self-explanatory!

---

### Post by knottshawk on 2009-09-18
> **badger_fruit said:**
> You're very welcome! I am pleased that my advice has helped!
/dons "hat of pride" and goes back to the dark place ...


By the way, this will create the mount only until you reboot (or perhaps log out).
For a permanant solution, add the line to your /etc/fstab

```
//my-pc/user  /folder/to/mount/into cifs    auto,uid=local_ubunutu_username,gid=users,_netdev    0    0
```

I can never remember what the 0 0 at the end means lol but the rest should be pretty self-explanatory!

Yep... I had already done that... it was just getting the initial connection working that was a bear!

---

