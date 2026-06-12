---
title: "How to mount shares on boot-up"
date: 2005-03-13
forum: Networking &amp; Wireless
---

### Post by rookie on 2005-03-13
Hello

I have a ubuntu-pc and 3 windows xp pc's. the ubuntu machine should become the main computer, while the windows-pc's provide shares for storage reasons etc.

I'm able to mount my windows shares using this command:

sudo mount //192.168.105.13/videos /media/videos -t smbfs

I'd like ubuntu to mount this share on boot-up. I tried the way which is mentioned at ubuntuguide.org, but it didn't work. The thing is, don't need a username nor a password to access those shares. Do I still have to alter the .smbcredentials and do I have specifiy the .smbcredentials in fstab?

Or is there another way to make ubuntu mount those shares? The goal is to have short-cuts on the desktop so I can access those shares quickly

Thanks for any help

---

### Post by rwabel on 2005-03-13
[QUOTE=rookie]Hello

I have a ubuntu-pc and 3 windows xp pc's. the ubuntu machine should become the main computer, while the windows-pc's provide shares for storage reasons etc.

I'm able to mount my windows shares using this command:

sudo mount //192.168.105.13/videos /media/videos -t smbfs

I'd like ubuntu to mount this share on boot-up. I tried the way which is mentioned at ubuntuguide.org, but it didn't work. The thing is, don't need a username nor a password to access those shares. Do I still have to alter the .smbcredentials and do I have specifiy the .smbcredentials in fstab?

Or is there another way to make ubuntu mount those shares? The goal is to have short-cuts on the desktop so I can access those shares quickly

Thanks for any help[/QUOTE]
try the following entry in your /etc/fstab
//192.168.105.13/videos /media/videos smbfs auto,username=whatever you want,password=whatever you want,uid=your username 0 0

---

### Post by rookie on 2005-03-13
Thanks for your reply (auf die Berner kann man eben zählen...)

What do I do if I don't need a username and a password? Do I just leave it out? Or do I have to write something like

//192.168.105.13/videos /media/videos smbfs auto,username=0,password=0uid=your username 0 0

or

//192.168.105.13/videos /media/videos smbfs auto,uid=your username 0 0

---

### Post by rwabel on 2005-03-13
you're welcome (bisch dämfau o bärner?)

try the second one. But I'm not sure, if it doesn't just put sth as as a username and sth as a password.

---

### Post by rookie on 2005-03-13
Nei, bin an Zürcher (aber scb fan)

I tried the this:

//192.168.105.13/videos /media/videos smbfs auto,uid=myusername 0 0

result: during boot-up, I asked to type a password. Since I don't have one, well...

then I tried this:


//192.168.105.13/videos /media/videos smbfs auto,username=sth,password=sth,uid=your username 0 0

result: during boot-up, I get the message "Line 11 in /etc/fstab is bad"

I am out of ideas. Why the hell won't this work??

---

### Post by rwabel on 2005-03-13
:-)
the problem is the following uid= your username
Let's asume your username on ubuntu is rookie then uid=rookie

you need to put it like that

 //192.168.105.13/videos /media/videos smbfs auto,uid=rookie 0 0

if the above doesn't work try this one
 //192.168.105.13/videos /media/videos smbfs auto,username=sth,password=sth,uid=rookie 0 0

---

### Post by rookie on 2005-03-13
I did that. My username is pascal.  I first tried:

 //192.168.105.13/videos /media/videos smbfs auto,uid=pascal 0 0

result: see above

then I tried:

 //192.168.105.13/videos /media/videos smbfs auto,username=sth,password=sth,uid=pascal 0 0

result: see above

no matter what, it doesnt work

---

### Post by rwabel on 2005-03-13
that's very strange
for me it works also like that
//wabel/g       /mnt/wabel/g    smbfs   auto,uid=rwabel         0 0

do you have smbfs installed?
try sudo apt-get install smbfs

---

### Post by rookie on 2005-03-13
did the apt-get, smbfs is installed already

here is a strange thing

I start ubuntu. the folder /media/videos is empty (because it's not mounted)

I start a root terminal and type 'mount -t smbfs //192.168.105.13/videos /media/videos
I'm asked to type a password (???). I type my ubuntu log-in pw

result: /media/videos is mounted !!!!

The strange thing is: if I type the very same pw during boot-up, In get an 'tree connect error. Access denied.' Same thing if I write the pw down in fstab.

how can this be?

---

### Post by rwabel on 2005-03-13
doing the mount in a root terminal or with sudo like this
mount -t smbfs //wabel/g /mnt/wabel/g
asks me also for a password. there you can just type whatever you want as password

just try to use no username and password in fstab. As long as you don't have one on the windows side you should be ok

---

### Post by rookie on 2005-03-13
no matter what I type in fstab, I either have to type a password  during boot-up or I get the "Line 11 in /etc/fstab is bad" error

I noticed something else: when I type sudo gedit /etc/fstab, the fstab does open, bur in the terminal window, there is this message

While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

I don't know if this could have something to do with the mounting problem

another thing: how can I get rid of samba, smbfs etc? I'd like to do the whole network thing again from the start

---

### Post by rwabel on 2005-03-13
When I mount it without username and password in fstab I also get asked at boottime. I just put my username and password init. maybe you could also just put sth different. Didn't test that.

About your error message, I've no idea what it means.

sudo apt-get --purge remove samba and the same for smbfs should do the job. --purge means he also removes the configs.

But maybe this isn't the whole procedure

---

### Post by rookie on 2005-03-13
Thanks for all your efforts rwabel

I beliebe I have a password problem of some sort.

example:

If I use Terminal to

sudo mount //192.168.105.13/videos /media/videos -t smbfs

I'm asked for my password. I type it in and the mounting works, but only with the right password.

If I use Root Terminal, I'm asked to type my password, then the Terminal opens. I type

mount //192.168.105.13/videos /media/videos -t smbfs

Then I get asked for a password. It doesn't matter what I type, So why ask in the first place?

Also, If I access my Windows Share via smb://192.168.105.13/scores,  a window pops up asking me about user, domain and password. I can either type in whatever I want, or I can just hit 'Enter'. 

IMHO, it doesn't make any sense

---

### Post by osde.info on 2005-06-01
First verify samba is working

# smbclient -L winsvr -U winuser

it should prompt you for your password and then list all available samba shares

To create a more secure fstab entry

# vi /etc/fstab-winsvr

insert

username=winuser
password=winpass

save it

Edit fstab

# vi /etc/fstab

append

//winsvr/winshare /mnt/winsvr smbfs credentials=/etc/fstab-winsvr,uid=ubuuser,gid=ubugroup

(on a single line)

# mount /mnt/winsvr

# ls /mnt/winsvr

# umount /mnt/winsvr

Finally # shutdown -r now

---

### Post by osde.info on 2005-06-01
have a look at [http://ubuntuforums.org/showpost.php?p=195128&postcount=14](http://ubuntuforums.org/showpost.php?p=195128&postcount=14)

---

### Post by rwabel on 2005-06-01
[QUOTE=osde.info]First verify samba is working

# smbclient -L winsvr -U winuser

it should prompt you for your password and then list all available samba shares

To create a more secure fstab entry

# vi /etc/fstab-winsvr

insert

username=winuser
password=winpass

save it

Edit fstab

# vi /etc/fstab

append

//winsvr/winshare /mnt/winsvr smbfs credentials=/etc/fstab-winsvr,uid=ubuuser,gid=ubugroup

(on a single line)

# mount /mnt/winsvr

# ls /mnt/winsvr

# umount /mnt/winsvr

Finally # shutdown -r now[/QUOTE]
 thanks for that one. just to clarify most of the commands needs to be done with sudo!

---

### Post by osde.info on 2005-06-01
very good point I should have mentioned I used "$ su -" before running these commands

---

### Post by DoorOpener on 2005-06-10
Hello.  I also have been trying to a) mount a folder through samba in general & b) mount the folder automatically on startup.  In my search I learned to enter the following to mount without a password:
```
mount -t smbfs //SERVERNAME/DESIREDFOLDER /home/username/desiredfolder -o "guest,fmask=0777,dmask=0777"
```
In this forum thread, I learned that I need to enter something into /etc/fstab to have it mounted on startup.  So, I tried the following format with success:
```
//SERVERNAME/DESIREDFOLDER /home/username/desiredfolder smbfs guest,fmask=0777,dmask=0777
```
Of course, I had to make sure that the desired destination folder had been created before this was run.  I hope this helps solve rookie's problem.

---

