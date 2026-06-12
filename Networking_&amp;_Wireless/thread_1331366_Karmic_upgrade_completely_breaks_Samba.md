---
title: "Karmic upgrade completely breaks Samba"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by TheKorn2 on 2009-11-19
Took the plunge last night and upgraded my Jaunty backend server to Karmic.  And now samba doesn't work at all!

I had a share points set up under jaunty, and was happily connecting to it via multiple devices (winXP, vista, minimyth, other ubuntu boxes, etc.).  Now after upgrading *none* of them can connect.  The windows clients act as though I've given a bad password.  The linux boxes say that I don't have permissions.

This doesn't make sense, because I had permission (read and write) *before* I upgraded to Karmic.  Further, when I actually look at my permissions (or try and do something in the affected directory) I have full perms!  Help!!!


Here's my smb.conf:

```

[mythtv]
path = /mythtv
comment = MythTV video files
available = yes
browsable = yes
public = yes
writable = yes
read list = tftp 

[global]
wins support = no
workgroup = WORKGROUP
deadtime = 30

```

Pretty simple smb.conf, worked *flawlessly* in Jaunty.

Just as a sanity check, I decided to go onto the now-karmic box and see if I could self-mount:

```

vince@Mythtery:~$ mkdir tmpmount
vince@Mythtery:~$ sudo mount -t cifs //127.0.0.1/mythtv /home/vince/tmpmount -o username=vince
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
vince@Mythtery:~$ 

```

Just to make sure I actually have permissions to see that directory...

```

vince@Mythtery:~$ cd /mythtv
vince@Mythtery:/mythtv$ ls -l
total 951480
drwxr-xr-x  3 vince vince          4096 2009-11-13 10:48 data_sheets
drwxrwxr-x 46 vince mythtv         4096 2009-11-12 19:09 downloads
(...rest snipped.  Point is I have permissions in that directory.)

```

And as for permissions...

```

vince@Mythtery:/$ ls -l / | grep myth
drwxrwxr-x  10 root   mythtv  4096 2009-11-19 01:32 mythtv
vince@Mythtery:/$ groups vince
vince : vince adm dialout cdrom plugdev lpadmin admin sambashare mythtv

```

So I'm at a complete loss here.  Everything tells me that I have permissions.  I can do file ops locally in the very directory I'm trying to map to via samba.  I haven't changed my smb.conf .  Yet **all** my systems regardless of OS can no longer connect to this share.

***[SIZE="5"]HELP!![/SIZE]***

---

### Post by TheKorn2 on 2009-11-19
Oh, and just for giggles, this fails, too:

```

vince@Mythtery:~$ sudo mount -t cifs //127.0.0.1/mythtv /home/vince/tmpmount -o username=vince,iocharset=utf8,file_mode=0777,dir_mode=0777
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Oh, and just for giggles, I checked and smbd is running...  so it's not as though samba isn't running, it's actively denying requests.

---

### Post by dmizer on 2009-11-19
Why are you trying to mount a localhost CIFS share?

Does the share work from another computer?

Edit:
Never mind, according to your first post the share doesn't work on any computer in your network. So, try this:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

   workgroup = WORKGROUP
   netbios name = Mythtery
   server string = %h server (Samba, Ubuntu)
   dns proxy = no

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d

####### Authentication #######

   security = share
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user

########## Printing ##########

# CUPS printing.  Uncomment these lines to share your printer through CUPS
;   printing = cups
;   printcap name = cups

############ Misc ############

   usershare allow guests = yes

#======================= Share Definitions =======================

[mythtv]
        path = /mythtv
        comment = MythTV video files
        read only = no
        guest only = yes
        guest ok = yes
```

---

### Post by TheKorn2 on 2009-11-20
> **dmizer said:**
> Why are you trying to mount a localhost CIFS share?

FWIW, I was doing that just to show that this wasn't a network connectivity problem.  (I know it doesn't make any logical sense to do it, but was more of a functional test.)

> So, try this:

That worked!  Thank you SO MUCH!

Now I'm going to have to go back and figure out what default setting that my smb.conf was apparently relying on changed in the interim.  (And also figure out how to get read-only access back for the tftp account; "read list" doesn't appear to work anymore.)

---

### Post by TheKorn2 on 2009-11-23
Upon further investigation, that smb.conf above just turns on guest access for the share.  That wasn't what I wanted (and was read-only), so I had to dig in further.

Turns out that the root issue was that upgrading to karmic somehow nuked my smbpasswd entries.  So after re-writing my smb.conf following [this example](http://ubuntuforums.org/showthread.php?t=202605), I still wasn't able to get anything to work...

...until I ran smbpasswd against my own account (to reset its password), and the read-only account (tftp).  Once I did that, samba was returned to its former working self.

(And "read list" still does work to restrict a certain user to read-only status for a share.)

---

