---
title: "Networking and NAS help please..."
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by suffer1989 on 2009-01-31
Hey, im using a linksys WRT610N router and have a USB 1Tb Hdd attached to it. Basically the router allows you to plug in any USB HDD, and you can access it as a NAS, but i have no idea as to how i could access it. Heres a screenie, if it helps...

[IMG]http://img522.imageshack.us/img522/7936/disk1232898228798bk6.png[/IMG]


Thanks...

---

### Post by suffer1989 on 2009-01-31
Bump?

---

### Post by graysky on 2009-01-31
If your router is indeed sharing the drive (Samba would be my guess) you might try connecting to it.  If you're using gnome, try entering the following into your nautilus window:

smb://ip.address.of.router

See what comes up. I dunno how security is handled on your router.  It may or may not require authentication.

Let's say your router's ip addy is 192.168.1.1 and your share on your 'nas' is exported as 'Harddrive' - you can do the following to mount it to a directory in your home directory called 'share' (you can mount the share to any empty directory on your filesystem, it doesn't have to be in your home dir).

```
$ sudo mount -t cifs //192.168.1.1/Harddrive ~/share -o username=username1
```

Where username1 = the username the router is using.  There are more sophisticated ways to mount a samba export.  Post back if you're interested.

---

### Post by suffer1989 on 2009-02-01
> **graysky said:**
> If your router is indeed sharing the drive (Samba would be my guess) you might try connecting to it.  If you're using gnome, try entering the following into your nautilus window:

smb://ip.address.of.router

See what comes up. I dunno how security is handled on your router.  It may or may not require authentication.

Let's say your router's ip addy is 192.168.1.1 and your share on your 'nas' is exported as 'Harddrive' - you can do the following to mount it to a directory in your home directory called 'share' (you can mount the share to any empty directory on your filesystem, it doesn't have to be in your home dir).

```
$ sudo mount -t cifs //192.168.1.1/Harddrive ~/share -o username=username1
```

Where username1 = the username the router is using.  There are more sophisticated ways to mount a samba export.  Post back if you're interested.



Hey, the first part worked perfectly. I did have problems with authorisation, but those resolved themselves. 

Many thanks...

EDIT : I cant find the mark thread solved, so can someone mark it ? Also, i couldnt find the thank post button either.. sorry...

---

### Post by graysky on 2009-02-01
> **suffer1989 said:**
> Hey, the first part worked perfectly. I did have problems with authorisation, but those resolved themselves. 

Many thanks...

Glad to help.  You might wanna post how the authorization problems resolved themselves for others :)

---

### Post by Iowan on 2009-02-01
> **suffer1989 said:**
> EDIT : I cant find the mark thread solved, so can someone mark it ? Also, i couldnt find the thank post button either.. sorry...Those features got disabled a few weeks ago when the forums were having stability problems.  It'll be interesting to see when/if they come back.

---

### Post by suffer1989 on 2009-02-03
> **graysky said:**
> Glad to help.  You might wanna post how the authorization problems resolved themselves for others :)

Yeah... I basically just looked up the default usernames/passwords in the guide. Its In administration, under the storage tab, for the router that I use.

Yeah, can someone tell me how to make the shared HDD mound, using Command/terminal ?

---

### Post by graysky on 2009-02-03
> **suffer1989 said:**
> Yeah, can someone tell me how to make the shared HDD mound, using Command/terminal ?

:confused:

> **graysky said:**
> Let's say your router's ip addy is 192.168.1.1 and your share on your 'nas' is exported as 'Harddrive' - you can do the following to mount it to a directory in your home directory called 'share' (you can mount the share to any empty directory on your filesystem, it doesn't have to be in your home dir).

```
$ sudo mount -t cifs //192.168.1.1/Harddrive ~/share -o username=username1
```

Where username1 = the username the router is using.  There are more sophisticated ways to mount a samba export.  Post back if you're interested.

Do you want it to auto mount when you boot into LINUX?  If that is the case, add the following to your /etc/fstab:

```
//192.168.1.1/Hardrive /mnt/share  cifs    credentials=/root/.smbpasswd 0 0
```

To make yourself a secure credentials file (which you want to do) simply:

```
$ sudo nano /root/.smbpasswd
```

Make that file read:

```
username=username1
password=password1
```

You'll substitute username1 and password1 for the u/p that your device is using.

Now do this to make that password file only available to root:

```
$ sudo chmod 600 /root/.smbpasswd
```

That should do it - it should auto mount on boot and you can now mount/unmount it at will via:

```
$ sudo mount /mnt/share
```
(or umount).

---

