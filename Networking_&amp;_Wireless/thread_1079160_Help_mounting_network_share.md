---
title: "Help mounting network share?"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by Nixie Pixel on 2009-02-24
Hi, I'm trying to mount a network Samba share on my laptop running Jaunty, and having a hard time. 

Here is my fstab entry:
```
//lion/lionsshare /mnt/lionsshare cifs users,auto,credentials=/home/niki/.smbcredentials,noexec 0 0 
```

I used sudo mkdir /mnt/lionsshare to create the mount point, and I created the file .smbcredentials with the user and password entries on separate lines, did sudo chown root .smbcredentials and sudo chmod 600 .smbcredentials.

However it doesn't seem to have worked.  Is there anything I might have missed?  (lionsshare is both the name of the share and the mount point I created)

Thanks!

---

### Post by dmizer on 2009-02-24
What is the output in terminal if you run this command:
```
sudo mount /mnt/lionsshare
```

I'm not sure, but this option "users" is not a valid smbmount option, so it could cause problems.

---

### Post by capscrew on 2009-02-24
Have you tried to mount the share from the CLI?

Be careful here.  The Gnome libs are different from the CLI libs.  As an example the CLI config file is /etc/samba/smb.conf.  The config files created when you use Gnome (Nautilus) are at /var/lib/samba.

Huh? Why is this?  Samba is maintained by a different developer than Gnome and things are done differently.  There is no unified developer for all the Linux packages.

I would suggest learning how to config Samba manually as this should work  across all versions of Ubuntu.  Why izzat you say.  Gnome has been under development and Gnome does not work the same (the Gnome gvfs has changed) from 7.10 to 8.04 and again in 8.10.

Samba should be consistent and backwards compatible.  I have 2 Samba servers (7.10 and 8.04).  the both use the same /etc/samba/smb.conf file I created.

I suggest reading: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

Edit:  To follow up on Dmizer's comments --
The proper command to mount the share from the command line (regardless of whether it is in fstab) is:
```
 mount -t cifs //server/share /mnt/mountpoint  -o user=username
```

It will prompt for your smbpasswd. I don't know at this point if you have created one so I don't know what to say about that.

---

### Post by dmizer on 2009-02-24
> **capscrew said:**
> Have you tried to mount the share from the CLI?
Mounting via /etc/fstab with the line provided is mounting via CLI.

> **capscrew said:**
> <snip>
I would suggest learning how to config Samba manually as this should work  across all versions of Ubuntu.  Why izzat you say.  Gnome has been under development and Gnome does not work the same (the Gnome gvfs has changed) from 7.10 to 8.04 and again in 8.10.

Samba should be consistent and backwards compatible.  I have 2 Samba servers (7.10 and 8.04).  the both use the same /etc/samba/smb.conf file I created.

I suggest reading: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

The OP is simply trying to mount a samba share, not create a samba server. Configuring smb.conf at this point would not be necessary.

---

### Post by capscrew on 2009-02-24
<snip> -- dmizer!  The smb.conf file has nothing to do with whether you are using it for a dedicated machine or in a peer to peer situation.  It's for configuring the smbd (Samba daemon) which is used in both cases.

Edit:  In addition the fstab syntax is different than the CLI.  Not by much but it is different.

On the thought of peer to peer.  The OP should not need to mount samba shares via fstab to begin with.  yes there are instances that require it (that gvfs thing again) but for a casual ad hoc situation it is not mandatory.

---

### Post by Nixie Pixel on 2009-02-24
> **dmizer said:**
> What is the output in terminal if you run this command:
```
sudo mount /mnt/lionsshare
```

I'm not sure, but this option "users" is not a valid smbmount option, so it could cause problems.

Output:
```
mount: wrong fs type, bad option, bad superblock on //lion/lionsshare,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Output of dmesg | tail:
```
[11481.309976]  CIFS VFS: No username specified
[11481.309987]  CIFS VFS: cifs_mount failed w/return code = -22
```

Edit:  I don't *need* to mount this network share permanently any more than I *need* to play Sins of a Solar Empire tonight, but I would very much like to do both.  ;)

---

### Post by capscrew on 2009-02-24
> wrong fs type, bad option, bad superblock on //lion/lionsshare,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might [COLOR="Red"]<--CIFS[/COLOR]
       need a /sbin/mount.<type> helper program)

This is why I sad to try it at the CLI.  The mount command I gave you is form the man (online documentation)pages.  For the cifs doc's try this from the CLI:```
man mount.cifs
```

---

### Post by Nixie Pixel on 2009-02-24
Thanks for trying to help, guys - here is my goal:

I have a computer I am using as a file server, multimedia streaming server, and running LAMP for website testing and such.  I finally found out how to share (and connect to) the file server with Samba.  

This step, creating a permanent mount, is really just one of convenience.  I don't want to have to connect to the server every time.  Plus, I like to learn, and configuring Samba has been an interesting challenge.

---

### Post by dmizer on 2009-02-24
> **Nixie Pixel said:**
> Output:
```
mount: wrong fs type, bad option, bad superblock on //lion/lionsshare,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Output of dmesg | tail:
```
[11481.309976]  CIFS VFS: No username specified
[11481.309987]  CIFS VFS: cifs_mount failed w/return code = -22
```

You just need to install the smbfs package:
```
sudo aptitude install smbfs
```
That should get you working.

---

### Post by capscrew on 2009-02-24
> **Nixie Pixel said:**
> Thanks for trying to help, guys - here is my goal:

I have a computer I am using as a file server, multimedia streaming server, and running LAMP for website testing and such.  I finally found out how to share (and connect to) the file server with Samba.
A server eh?  so this is not an ad hoc situation at all.
>   

This step, creating a permanent mount, is really just one of convenience.  I don't want to have to connect to the server every time.  

The difference between mounting the share via fstab (or the mount command) or using Nautilus (and bookmarking the share) have more to do with whether you are using the kernel libs or the user-land libs.  CLI is kernel-land where as Nautilus uses gvfs which is a user-land lib.  BTW smbfs is user-land and is updated to include cifs enhancements.

Both are mounted and available for your use at any time. Bookmarking is like mapping a drive in Windows.  There are differing advantages to both ways. 
> 

Plus, I like to learn, and configuring Samba has been an interesting challenge.

I'm not going t get into a flame war with dmizer.  You need only one person to guide you at this time.  If you need me just ask.

---

### Post by dmizer on 2009-02-24
As an afterthought, I also suggest you look at your credentials file. It should look like this:
```
username=winusername
password=winpassword
```
It is important to have no space before or after the "=".

---

### Post by Nixie Pixel on 2009-02-24
Well, that would do it...I had spaces before and after the = in my credentials file.

I will update that and confirm it is fixed.  Thanks everyone!  And why get into a flame war over this?  It isn't worth it ;)

---

### Post by Nixie Pixel on 2009-02-24
Nope, not fixed.  =(  While the spaces were definitely a problem, they were not the only problem, apparently.

By the way, is there a way I can re-load fstab without rebooting, to test any changes I make?  Rebooting every time can be annoying...

Or at least a way to test using the CLI?

Thanks!

---

### Post by dmizer on 2009-02-24
You can mount the lines in fstab with this command:

```
sudo mount mountpoint
```
Unmount with this command:
```
sudo unmount mountpoint
```

have you tried removing the "users" option? Does "sudo mount /mnt/lionsshare" have a different error now?

---

### Post by Nixie Pixel on 2009-02-24
I tried removing the users option, it didn't make a difference.  I created the line by copying the example in [Understanding fstab, here]("http://ubuntuforums.org/showthread.php?t=283131").  

The error messages are still the same when I try sudo mount.  Perhaps I have the wrong path.  I have .smbcredentials in my home directory - what is the correct way to reference this path?
credentials=~/.smbcredentials
=/home/user/.smbcredentials
Or something else?

Thanks!

---

### Post by dmizer on 2009-02-24
Are you sure you have smbfs installed? Smbfs is a metapackage with all the necessary tools for mounting Windows shares, and includes the CIFS package. If this package is not installed, you may get this error.

I would suggest moving your credentials file to your root directory as outlined in my CIFS howto under "Permanent mount" (second link in my sig).

---

### Post by Nixie Pixel on 2009-02-24
Well, I guess I didn't have smbfs properly installed.  I installed the package and a new error message (about my path) showed up, and when I fixed that I was able to mount the network share.

Thanks for all your help!

---

### Post by dmizer on 2009-02-24
> **Nixie Pixel said:**
> Well, I guess I didn't have smbfs properly installed.  I installed the package and a new error message (about my path) showed up, and when I fixed that I was able to mount the network share.

Thanks for all your help!

No problem! Glad we got you going!

---

### Post by Obsolete Zero on 2009-02-25
I'm having the exact same problem and ended up at the permission denied mount error 13 of doom.

Checked the pw and user and everything seems to be in order.
I assume I am allowed to use the admin account to login.......

I'll keep working on the problem and let you guys know if I find the solution. 

PS. hijacking your thread here Nixie Pixel :D ;-)

EDIT: Ok, found the problem. Needed to add username=**DOMAIN**/username in the credentials file instead of only the username :D

Now i got the error 6 no such drive thingy but i'm sure to figure it out

---

### Post by dmizer on 2009-02-25
Obsolete Zero, please see the second link in my sig. There should be enough information there to get you going.

---

