---
title: "unable to see samba share from client machines"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by badperson on 2010-02-15
Hi,
I just set up an ubuntu 9.10 server (no desktop environment, command line only) and I'm unable to see my samba share. 

I followed [these instruction]("https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html")s. 

Here are the relevant parts of my smb.conf file: 

>    workgroup = JASONGROUP
# I un-commented this
   security = user 

## I created this at the bottom
[share]
        comment = Ubuntu Server Shared Files
        path = /media/shared-files/root
        browsable = yes
        guest ok = yes
        read only = no
        create mask = 0777






The instructions say to enter these commands: 

sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/


but when entering the "chown" command, I get this:
> sudo chown nobody.nogroup /media/shared-files/root
chown: changing ownership of `/media/shared-files/root': Operation not permitted



The client machines (a desktop with an ubuntu and windows partition and a mac laptop) are able to see that a shared folder exists, but are unable to open it or write to it. From the ubuntu desktop machine I enter smb://<ip address>/ but when I double-click on the "share" folder, I get "Unable to Mount Location -- Failed to Mount Windows share"

ideas? 

thanks,
bp

---

### Post by Iowan on 2010-02-15
What are results of: ```
ls -al /media/shared-files
```
I presume you first did: ```
sudo mkdir -p /media/shared-files/root
```You restarted the Samba server afterward?

---

### Post by badperson on 2010-02-15
> jason@jason-server:/$ ls -al /media/shared-files
total 36
drwx------ 3 jason root 16384 1969-12-31 19:00 .
drwxr-xr-x 5 root  root  4096 2010-02-15 15:16 ..
drwx------ 2 jason root 16384 2010-02-15 17:25 root
jason@jason-server:/$ 



I did do the mkdir....and I restarted the samba server. 

thanks!
bp

---

### Post by Iowan on 2010-02-15
I'm curious why the **chown** didn't work - check */etc/passwd* and */etc/group* (you'll probably need **sudo**) to verify **nobody** and **nogroup** exist.

---

### Post by ant2ne on 2010-02-15
try the link in my sig.

---

### Post by badperson on 2010-02-15
> **Iowan said:**
> I'm curious why the **chown** didn't work - check */etc/passwd* and */etc/group* (you'll probably need **sudo**) to verify **nobody** and **nogroup** exist.

hi,
they're both there. 
bp

---

### Post by capscrew on 2010-02-16
> **badperson said:**
> ...
The instructions say to enter these commands: 

sudo mkdir -p /srv/samba/share
sudo chown nobody.nogroup /srv/samba/share/


That has to be a typo.  From the [FONT="Courier New"]chown [/FONT]man page:```
The owner and group operands are both optional; however, at least one
must be specified.  [COLOR="Navy"][B]If the group operand is specified, it must be 
preceded by a [COLOR="Red"]colon (``:'')[/COLOR] character[/B][/COLOR].

```

I believe this command will work:```
sudo chown nobody:nogroup /srv/samba/share/
```

---

### Post by badperson on 2010-02-16
still getting this: 
> jason@jason-server:/$ sudo chown nobody:nogroup /media/shared-files/root
chown: changing ownership of `/media/shared-files/root': Operation not permitted


the shared folder is on a newly installed hard drive...is it possible I didn't format it correcty? I can create new folders and files on the drive from within the server...

bp

---

### Post by badperson on 2010-02-16
I was able to get the share to work when I changed the shared folder to /srv/samba/share. 

But I want to have the shared files on their own dedicated drive...so it sucks that I cant't do that. Any help would be appreciated. 
bp

---

### Post by Morbius1 on 2010-02-16
Um ...... by any chance is /media/shared-files a FAT32 or NTFS partition?

Can't use chown on a windows filesystem - has to be done in fstab.

---

### Post by badperson on 2010-02-16
it's fat32, as per the reccomendation of the docs. 
bp

---

### Post by Morbius1 on 2010-02-16
Well, here's how I see things. If you want to have  /media/shared-files with owner=nobody then you're going to have to mount it that way in fstab.

For example:

```
 /dev/sdb1 /media/shared-files vfat defaults,utf8,uid=65534,gid=65534 0 2
```[COLOR=Blue] To make sure that nobody = 65534 issue the following command in a terminal: **id nobody**.[/COLOR]

The second thing is this:
> [share]
        comment = Ubuntu Server Shared Files
        path = /media/shared-files/root
        browsable = yes
        guest ok = yes
        read only = no
        [COLOR=Blue]create mask = 0777[/COLOR]
That's not going to have any affect since you can't change permissions on a FAT32 partition either. So you're going to have to add one more thing to the fstab entry for that partition: umask=0000

So the final entry would look something like this:

```
 /dev/sdb1 /media/shared-files vfat defaults,utf8,umask=0000,uid=65534,gid=65534 0 2
```You'd have to change the /dev/sdb1 to the appropriate value

---

### Post by Iowan on 2010-02-16
FWIW, I tried the example and successfully "chown'ed" using nobody.nogroup.> **Morbius1 said:**
> Um ...... by any chance is /media/shared-files a FAT32 or NTFS partition?
Can't use chown on a windows filesystem - has to be done in fstab.Good point! All my Samba servers share directories from Linux filesystem - probably why my test worked. 

@bp
Can you link to the instructions calling for FAT32 file system?

---

### Post by badperson on 2010-02-16
I think I should reformat the drive as ext3...vista has no problem connecting to the main drive on the server which is formatted that way. 
bp

---

### Post by Iowan on 2010-02-16
If it's a new installation (only thing to lose is time), it might be worth the effort.

---

### Post by badperson on 2010-02-19
solved. I deleted the partition, created a new one and formatted the drive as ext3. That seemed to do the trick. 
bp

---

### Post by rje_nc on 2010-02-19
I find that when I want to mount to Samba shares I need to install smbfs.  This is not installed by default in Ubuntu but for me it allows me to mount and connect to samba shares without problems.

---

### Post by Iowan on 2010-02-19
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by badperson on 2010-02-19
sorry...stupid question...how do you mark a post as solved? I didn't see a button or a way to do it by editing...

---

### Post by Iowan on 2010-02-19
The [link]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") *should* explain it - only wish they'd had screenshots of the "Thread Tools" pulldown and the "Mark this thread as solved" option.

---

