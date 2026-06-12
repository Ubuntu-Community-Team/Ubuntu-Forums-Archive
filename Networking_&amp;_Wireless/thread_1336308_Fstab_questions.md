---
title: "Fstab questions"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by jessiebrownjr on 2009-11-24
I have sucessfully setup NFS on my laptop and desktop. Both have UFW running and are blocking all non local traffic. 

I now have a few questions about fstab!

The drives I network on my laptop and desktop aren't needed to be on all the time, its only to sync homework or media files, but is there a way to make a shortcut in fstab that will let me type something much shorter then the full IPs and mount locations? 

Also, my desktop has a partition that I think is NTFS format that I share with my windows install too, which has a purpose of just being for Mp3s and AVIs. I want to automatically mount that at boot, how can I accomplish this?

---

### Post by scorp123 on 2009-11-24
Once an entry is in /etc/fstab it's enough to state the mount-point. Let's suppose you have a line that says:
```
...
server:/srv/data/public    /public    nfs   noauto,rw      0       0
...

```

Since the system knows now about the mount-point and the necessary parameters, it would be enough for "root" to issue this command:
```
sudo mount /public
```

So that would be a possibility for you. Define the mount-points, but also add the "**noauto**" parameter as I did above. Result: the system won't try to mount those locations when it starts up. So it doesn't matter if the server is on and reachable or turned off and therefore not reachable. 

To make it even easier for you, you could add yourself to the "sudoers" file and allow yourself to mount that location anytime you wish.

Here is a thread that explains that:
[http://ubuntuforums.org/showthread.php?p=8330156#post8330156](http://ubuntuforums.org/showthread.php?p=8330156#post8330156)

So you could add a line that says e.g.:
```
# let my user mount my NFS shares if I want to
jessie   ALL=NOPASSWD:  /bin/mount  /path/to/nfs/mount/point
jessie   ALL=NOPASSWD:  /bin/umount  /path/to/mount/point

```

Now it will let you mount and umount those locations via "sudo" even without bothering you to ask for your password.

You could nwo write those few commands and their needed parameters into a shell script and then place a launcher icon on your desktop ... or your panel or wherever else you like, e.g.

one icon for a script that contains these lines:
```
#! /bin/bash
sudo /bin/mount  /path/to/nfs/mount/point

```
and another icon for a script that contains these lines:
```
#! /bin/bash
/bin/umount  /path/to/mount/point
```

The final result here would be that you get two icons (or more ... depends on what you do here) that you can easily click on and mount and unmount your NFS shares whenever you wish.

I'd assume that something like this is what you want?

---

### Post by jessiebrownjr on 2009-11-24
This is 100% what I want, but your example entry into fstab confused me I suppose

your ... and server:
the periods im assuming are just... "etcetera"

but the server portion, what is that?

Is that the IP:/serverssharedfiolder /whereitsbeingmountedto then options?
I guess it makes sense now after I typed this out, but I just don't want any problems :-)

Thanks!

---

### Post by scorp123 on 2009-11-24
> **jessiebrownjr said:**
>  the periods im assuming are just... "etcetera"  Yes. Placeholders for other stuff that might be in there as well ...

> **jessiebrownjr said:**
>  but the server portion, what is that?  The hostname of a server. Could also be its IP address. Whatever. If only it's reachable.

See the manual:
```
man 5 nfs
```

They use the same example as I did:
> For NFS file system mounts, a line in the /etc/fstab file specifies the server name, the path name of the exported server directory to mount, the local directory  that  is  the mount point, the type of file system that is being mounted, and a list of mount options that control the way the filesystem is mounted and how the NFS client behaves when accessing files on this mount point. The fifth and sixth fields on each line are not used by NFS,  thus  conventionally  each contain the digit zero. 

For example:

**server:/path    /mountpoint    fstype    option,option,...   0 0**

The  server's  hostname  and  export pathname are separated by a colon, while the mount options are separated by commas. The remaining fields are separated by blanks or tabs.  The server's hostname can be an unqualified hostname, a fully qualified domain name, or a dotted quad IPv4 address. ...

---

### Post by jessiebrownjr on 2009-11-24
I found the location of the sudoers. Might want to post somewhere to edit it in visudo, because I had to google that part but it was easy enough.

Ok my question is this now.. Im up to the part where you said I creat a shortcut launcher. what do I put where on the GUI for that to happen?

---

### Post by jessiebrownjr on 2009-11-25
```
# let jessie mount nfs shares
jessie    ALL=NOPASSWD:    /bin/mount    /home/cookie/desktopmnt
jessie    ALL=NOPASSWD:    /bin/umount    /home/jessie/laptopmnt



```

This is my cat /etc/sudoers portion. I thought I followed your directions, but it still requires a password. Any suggestions to something I might have done wrong?

---

### Post by scorp123 on 2009-11-25
> **jessiebrownjr said:**
>  I thought I followed your directions, but it still requires a password.  You did use the **"visudo"** command to edit **/etc/sudoers**? Because that's the only way. Everything else may have strange side effects.

And to test it: Use a shell at first. So open a terminal (Applications > Accessories > Terminal ...) and issue these commands to test them:
```
sudo /bin/mount /home/cookie/desktopmnt
sudo /bin/umount /home/jessie/laptopmnt
```

BTW, in one line the mount-point is called **"desktopmnt"** and in the other line you call it **"laptopmnt"**.... Are those the same locations? If so they should be named the same. Or else you will able to mount one location but not unmount it, and vice versa: able to unmount but not be able to mount it first. 

And just to make sure: You did already add those mount-points to **/etc/fstab**, right?

---

### Post by jessiebrownjr on 2009-11-25
192.168.0.100:/home/cookie/desktopmnt /home/jessie/laptopmnt nfs noauto,rw 0 0
^
Is the line in fstab.

Desktopmnt is a blank folder on my desktop. Laptopmnt is a blank folder on my laptop.  I use both systems for file transfers depending on where I downloaded something, and where its going. it was just easier to remember it that way.

Edit. The command you typed out does load without me needing to type root for both mount and umount.
Now if I can just learn to make this into easy to use icons ;-p

---

### Post by scorp123 on 2009-11-25
> **jessiebrownjr said:**
>  Now if I can just learn to make this into easy to use icons ;-p [http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en](http://library.gnome.org/users/user-guide/stable/gospanel-34.html.en)

---

### Post by jessiebrownjr on 2009-11-25
I meant more like verbatim, what do I type once I get here:
Type:application/application in terminal/location (what do I pick for a nfs mount command)
Name: Im sure shortcut name goes here
Command: What *exactly* do I type here? This?
sudo /bin/mount /home/cookie/desktopmntComment: Obvious

---

