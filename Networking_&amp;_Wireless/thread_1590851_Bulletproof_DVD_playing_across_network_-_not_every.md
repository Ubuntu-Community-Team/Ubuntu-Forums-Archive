---
title: "Bulletproof DVD playing across network - not every time"
date: 2010-10-08
forum: Networking &amp; Wireless
---

### Post by zcacogp on 2010-10-08
Chaps, 

I'm posting this as a request for assistance with an ongoing problem I am having with playing DVD's across a network (wireless or otherwise.) 

I a desktop machine, ('desktop') and a laptop ('x61s2'). The desktop is a home-built thing with a Gigabyte S-series motherboard (model GA-MA790GP-DS4H, more details here: [http://www.motherboards.org/reviews/motherboards/1813_1.html](http://www.motherboards.org/reviews/motherboards/1813_1.html)) The laptop is a lenovo X61S2 Thinkpad. Both machines are running 10.04 Lucid. The laptop doesn't have a CD/DVD drive, hence if I want to play a DVD on a laptop I have to do it over the network - usually wirelessly. The router I have is a Netgear DG834GT. 

The issue I am having is that I struggle to get the DVD to play on the laptop. It reliably plays on the desktop (the machine the drive is in), and the drive will always mount (using Samba) OK the laptop. Once the drive is mounted on the laptop then I can open the drive in Nautilus and see the files. 

It tells me that "These files are on a video DVD". I can click "Open Movie Player, but once the Movie Player has opened I am told that "An error occurred. Could not read from resource." 

Sometimes, however, it does work. Usually, I can get it to work by unmounting the drive from the laptop, then from the desktop (using 'sudo umount -a' in each case), then re-mounting it, but it's not 100% reliable. Sometimes I have to do it several times before the DVD will play on the laptop. 

What does seem to help a little is first playing the DVD on the desktop - even just opening it and playing a couple of seconds, before mounting the drive on the laptop, seems to make it more likely to play on the laptop. Even then it's not reliable, but it helps. 

I am pretty sure that the problem lies with the desktop machine. I also have another laptop (an IBM Thinkpad X31s) which is configured the same as the X61, and if the DVD will play on one laptop then it will play on both. This suggests, to me, that the problem is at the desktop end. 

I have tried changing the DVD drive in the desktop - swapping it for one from a friend, but it didn't make any difference. I have also tried changing it from being the master drive to the slave drive and that made no difference. I have tried using different security settings on Samba, and those made no difference at all (including using no security at all). 

I have posted about this problem before, here: 

[http://ubuntuforums.org/showthread.php?t=1532646](http://ubuntuforums.org/showthread.php?t=1532646) ... and I thought I had solved it as I managed to make it play once. However, it wasn't reliable. 

I will put copies of the fstab files from both machines, and the smb.conf file at the end of this post, but if anyone has any suggestions I'll be quite keen to hear. 

Sorry for the long post. All help welcomed. Thank you. 


Oli. 


1. fstab from the desktop machine: 
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0

#Entry for /dev/sda7 :
UUID=4fad3717-fe29-42b2-8092-a278a1a16d1f	/	ext3	errors=remount-ro	0	1

#Entry for /dev/sda5 :
UUID=961030DC1030C4D1	/media/Helena	ntfs-3g	defaults,locale=en_GB.utf8	0	0

#Entry for /dev/sda6 :
UUID=7474436D744330E2	/media/Ianthe	ntfs-3g	defaults,locale=en_GB.utf8	0	0

#Entry for /dev/sda1 :
#UUID=7674DA8C74DA4E8D	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0

#Entry for /dev/sda8 :
UUID=e0c85aa5-92ba-4852-a4d3-e32bce6937e2	none	swap	sw	0	0

/dev/sr0	/media/dvd	udf,iso9660	defaults,noauto,ro,user	0	0

#UUID=7674DA8C74DA4E8D	/media/sda1	ntfs	defaults,nls=utf8,umask=0222	0	0
#Entry	for	/dev/sr0	(CD	ROM	drive)
```

2. smb.conf (with some commented out text removed) on the desktop machine:
```


   workgroup = lbbarnet

   server string = %h server (Samba, Ubuntu)

   dns proxy = no

;   name resolve order = lmhosts host wins bcast

;   interfaces = 127.0.0.0/8 eth0

;   bind interfaces only = yes

   log file = /var/log/samba/log.%m

   max log size = 1000

#   syslog only = no

   syslog = 0

   panic action = /usr/share/samba/panic-action %d


   security = user

   encrypt passwords = true
   username map = /etc/samba/smbusers

   passdb backend = tdbsam

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

   pam password change = yes

   map to guest = bad user

;   domain logons = yes

;   logon path = \\%N\profiles\%U

#   logon path = \\%N\%U\profile

;   logon drive = H:
#   logon home = \\%N\%U

;   logon script = logon.cmd

; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

; add group script = /usr/sbin/addgroup --force-badname %g

   load printers = yes

;   printing = bsd
;   printcap name = /etc/printcap

   printing = cups
   printcap name = cups

;   include = /home/samba/etc/smb.conf.%m

;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

#   domain master = auto

;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

;   winbind enum groups = yes
;   winbind enum users = yes

;   usershare max shares = 100

   usershare allow guests = yes

;[homes]
   comment = Home Directories
   browseable = yes

   read only = no

;   create mask = 0700

;   directory mask = 0700

;   valid users = %S

;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

;   write list = root, @lpadmin

# Drive sharing bit.

[dvdromdrive]
   comment = DVD on desktop
   read only = yes
   locking = yes
   path = /media/dvd
   guest ok = yes

[Helena]
   comment = Helena on Desktop
   read only = no
   locking = no
   path = /media/Helena
   guest ok = no

[Ianthe]
   comment = Ianthe on Desktop
   read only = no
   locking = no
   path = /media/Ianthe
   guest ok = no

#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0

;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom 
```

3. fstab on the X61 laptop: 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda8    /    ext3    errors=remount-ro    0    1
/dev/sda5    /media/Horatio    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/sda6    /media/Ieuan    ntfs-3g    defaults,locale=en_GB.utf8    0    0
/dev/sda7    none    swap    sw    0    0

//192.168.10.3/Ianthe /media/Ianthe cifs credentials=/etc/samba/user,noexec 0 0

//192.168.10.3/Helena /media/Helena cifs credentials=/etc/samba/user,noexec 0 0


//192.168.10.3/dvdromdrive /media/cdrom cifs credentials=/etc/samba/user,defaults,ro,user 0 0
```

---

### Post by chaanakya_chiraag on 2010-10-08
Have you tried using VLC instead of Totem?  I'm not sure, but it may work better...just a thought.

---

### Post by zcacogp on 2010-10-08
Chaanakya_chiraag - Thanks for your reply. 

VLC doesn't seem to do any much better than Totem. If I try and open a non-playing disk on the laptop using VLC (when started from the command line), I get the following messages: 

```

ogp@ogp-X61s:~$ vlc
VLC media player 1.0.6 Goldeneye
[0x91ab668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device //192.168.10.3/dvdromdrive mounted on /media/cdrom for CSS authentication
libdvdread: Could not open //192.168.10.3/dvdromdrive with libdvdcss.
libdvdread: Can't open //192.168.10.3/dvdromdrive for reading
libdvdread: Device //192.168.10.3/dvdromdrive inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ogp/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f50000. Regions: 2 4
[0xb7420ef8] main input error: ES_OUT_RESET_PCR called
[0xb7420ef8] main input error: ES_OUT_RESET_PCR called
[0xb7420ef8] main input error: ES_OUT_RESET_PCR called
[0xb7420ef8] main input error: ES_OUT_RESET_PCR called
ogp@ogp-X61s:~$ 

```

... and nothing displays in the VLC play window. 


Oli.

---

### Post by chaanakya_chiraag on 2010-10-08
Hmmm...so you are mounting the remote DVD as /media/cdrom, right?  Are you pointing VLC/Totem to /media/cdrom or to the remote path?

---

### Post by zcacogp on 2010-10-08
What's the difference? I'm not quite sure that I understand how you would do one or the other ... sorry for being slow. 

I double-click on the "cdrom" icon on the desktop of the computer, and it opens Nautilus. I then click on the "Open movie player" button, Totem opens and a second or so later I get a window opening saying "**An error occurred.** Could not read from resource."

Did that make sense? 


Oli.

---

### Post by chaanakya_chiraag on 2010-10-08
Okay...hmmm...I understand what you are doing, but I'm not exactly sure what the problem is...if I had a similar setup, I'd test it , but unfortunately, I don't :(

I'm assuming you're doing a similar thing with VLC?  That is, you're opening VLC and clicking on open Disc and pointing it to the cdrom folder?  If so, I'm sorry I can't help you :(

---

### Post by chaanakya_chiraag on 2010-10-08
Reading the VLC output, it may be an authentication problem???  I'm not sure, but that's what it looks like to me...

---

### Post by chaanakya_chiraag on 2010-10-08
Also, have you tried sharing the /dev directory and opening /dev/cdrom directly on the remote computer?  Again, just another thought...not sure if it will work, but it's worth a shot...

---

### Post by snappy90 on 2010-10-08
Silly question have you enabled DVD support.
If not this should do it

sudo aptitude install libdvdcss2 && sudo /usr/share/doc/libdvdread4/./install-css.sh

---

### Post by zcacogp on 2010-10-10
Chaps, 

Thanks for your answers. I'll go through them one by one. 

chaanakya_chiraag - thanks particularly. Your input to this thread is appreciated. No, I haven't tried sharing /dev directly, I'll give it a shot. 

I don't understand enough about the output from VLC to know whether it is an authentication problem - it's possible. Why would it not authenticate reliably, and how would I investigate this? And, yes, I am doing the same with VLC; opening VLC, opening the disc and trying to play it. 

snappy90 - yes, I do have those packages installed. Good try tho' - thanks. 

Two new things that I have found with a bit more playing around: 

1. If I open the DVD on the desktop machine (the one with the DVD drive in it) **before **opening it on the laptop then it works pretty much every time. (I think I said otherwise in my first post, in which case I was wrong!) So it almost feels as if the DVD needs to be 'verified' or 'proved' on the desktop before it can be played elsewhere. 

2. If I don't first open the DVD on the desktop (i.e. so it won't play on the laptop) and open the DVD share on the laptop using Nautilus then I can see the files on the disk - as before. However, if I try and copy one of those files directly to the laptop (not play it, just copy a file from the DVD across the network to the laptop), I get an error saying "There was an error copying the file. Error splicing file: Input/output error". Does this suggest that there is simply a problem accessing the file across the network? 

All input welcome - thanks. 


Oli.

---

### Post by chaanakya_chiraag on 2010-10-10
That is what it seems like.  Can you try using ```
scp
``` or ```
ftp
``` to try copying it WITHOUT mounting it at all on the remote machine?  That could tell us whether it's an authentication problem or some other problem.  If you don't know how to use scp or ftp, just post here and I can try to walk you through it.

---

### Post by chaanakya_chiraag on 2010-10-10
Also, just a thought, but have you also done the second part of snappy90's post?  That is, have you run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
I know I thought I was done just by installing the package, but maybe that second step is required for stuff like what you are trying to do to work properly.

---

### Post by zcacogp on 2010-10-13
chaanakya_chiraag, thanks again. I'm not getting as much time to play with this as I would like, so apologies for taking a while to reply to your posts. 

I have tried that which Snappy90 suggested, and it made no difference; the DVD is still not reliably accessible. (Same as before - it isn't accessible, with the error message "could not read from resource", unless the DVD has been opened on the desktop machine beforehand.) 

Using instructions here: 

[http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

... I set up the desktop as an FTP server (installed vsftpd), and then tried accessing it from the laptop using "Places > Connect to server". I'm not sure whether it worked or not; it opened Nautilus and I could see I was logged in as 'FTP as ogp on desktop', and I could see files in there, but I wasn't sure what I was meant to do from there. (I would post a screenshot, but there is no 'print screen' button on this machine!) I could see a number of directories (bin, boot, cdrom, dev, etc and so on) if that's any help. If you can give me some more directions I'll have a go and let you know the outcome. 

Thanks again for your help. 


Oli.

---

### Post by chaanakya_chiraag on 2010-10-13
I'd recommend using ```
scp
``` instead like this:
```

cd ~
mkdir testdvd
cd testdvd
scp -r 192.168.10.3:dvdromdrive .

```
I think that should work.  If you get errors, post back here.

---

