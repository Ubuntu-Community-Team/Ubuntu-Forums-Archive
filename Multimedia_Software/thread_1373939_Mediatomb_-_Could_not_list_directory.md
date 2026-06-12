---
title: "Mediatomb - Could not list directory"
date: 2010-01-06
forum: Multimedia Software
---

### Post by 0ak13y on 2010-01-06
Hi All,

I am very new to Ubuntu or any Linux for that matter. I am tring to get Mediatomb to work on my system. I have installed the packages and mediatomb appears to be running fine. The problem is that I have an external hard drive that I want my files to be kept on. When I try to add the folders on the external I get the following error:

Error: Could not list directory /media/TeraByte : Permission Denied.

TeraByte is the name of the volume, I have created shared folders on the Volume, but I can't seem to get anywhere with this. 

Any help would be greatly appreciated.

Thanks

---

### Post by sanderd17 on 2010-01-06
You will have to change the permissions of the folder on the external hard drive. This can be done with nautilus: hit alt+F2 and execute 
```
gksudo nautilus
```, go to the folder you want to copy the files to and change the permissions with a right click -> properties -> rights. Change the owner and the group to yourself and apply it to the other files in the folder.

Now it should work

Alternatively, you can do it with command line. All those things done with command line are very good explaned in the tutorial [http://linuxcommand.org/lts0070.php]("http://linuxcommand.org/lts0070.php") (the link is to the page with the permissions tutorial).

If this doesn't help, could you show me (a short version if it's quite long) of the result of the command

```
ls -al /media/TeraByte
```

---

### Post by 0ak13y on 2010-01-06
Hi sanderd,

thanks for the reply. I tried your suggestion, unfortunately, still not working for me.

This is the result of the comment that you asked for.

drwx------ 4 ryan ryan 16384 1969-12-31 20:00 .
drwxr-xr-x 7 root root  4096 2010-01-06 13:35 ..
drwx------ 2 ryan ryan 16384 2010-01-06 10:01 Movies
drwx------ 2 ryan ryan 16384 2010-01-06 10:01 Music

---

### Post by buntunoob on 2010-01-07
The next problem your going to run in to is that if you start mediatomb before mounting the drive you'll have to reimport again, so if you can now mount the drive at boot.

---

### Post by sanderd17 on 2010-01-07
Ok, lets give it an other try, make your disk acessible for everyone:

```
sudo chmod 777 /media/TeraByte
```

This is not so safe, so if its works try 755 instead of 777.

If it still doesn't work, try 

```
sudo chmod -R 777 /media/TeraByte
```

---

### Post by Mechphisto on 2010-01-07
I have the exact same problem.
But changing permissions doesn't work for me because the external HD is using NTFS format; the changes don't take.

Funny, it used to work just fine before I reinstalled the OS. I did so using the same username, so I have no problem accessing my external HD with the file manager. Just Mediatomb doesn't want to access it.

Thanks for any suggestions!

---

### Post by sanderd17 on 2010-01-08
Maybe it will help if you mount your disk at startup, like buntunoob said. Follow the next steps:

[LIST]
[*]mount your external disk with nautilus (just open it and nautilus will mount it for you)
[*]Check how the partition you want to acces is named (on your hdd it's sda1, sda2,... on an external drive it will be someting like sdb1, sdb2). How can you check it? you can do it with gparted:
```

sudo apt-get install gparted
gksudo gparted

```
In gparted, select the drive you want to mount and read the partition number. (be sure it has a number and not just sdb).
[*]now that you have the name, you have to search the UUID. you can do it with the code
```
sudo blkid
```
[*]remember the UUID of your hdd and add a line to your fstab file:
```
sudo gedit /etc/fstab
```
Add the folowing line:
```
UUID=2713699d-231d-4e8b-9484-5450cededef3 /home/hdd               ntfs    defaults 0       1
```
You can change your location /home/hdd to the location you want your files to appear, off course you have to change the UUID to the one you found with blkid. And you'll have also to change the ntfs to ext3 or ext4 if it's not ntfs you use.
[*]If that is done, do a reboot and see if your external hdd can be read.
[/LIST]

---

### Post by Mechphisto on 2010-01-08
Oh that so worked! Thanks. :)

---

### Post by Maelgwyn on 2010-02-18
I'm actually having the same problem - all my media is stored on the external HDD called My Book.

I've added the UUID to fstab, and it's automagically mounting when I boot - yet MediaTomb is still refusing to list the directory >.<

ls gives me this
```

nik@ochre:~$ ls -al /media/My\ Book/
total 193
drwx------ 1 nik  nik   4096 2010-02-18 18:40 .
drwxr-xr-x 4 root root  4096 2010-02-18 20:06 ..
-rwxrwxrwx 1 nik  nik    504 2009-07-31 21:58 desktop.ini
drwx------ 1 nik  nik   4096 2009-11-22 11:00 Downloads
drwx------ 1 nik  nik   4096 2009-11-08 13:21 From Jules
drwx------ 1 nik  nik   8192 2010-02-18 18:43 Jarrod's backup
drwx------ 1 nik  nik   4096 2010-02-08 06:08 Misc
drwx------ 1 nik  nik  28672 2010-02-10 10:34 Movies
drwx------ 1 nik  nik  98304 2010-02-16 10:51 Music
drwx------ 1 nik  nik   4096 2010-02-17 18:59 Nik's backup
drwx------ 1 nik  nik   8192 2009-12-10 20:21 $RECYCLE.BIN
-rwxrwxrwx 2 nik  nik    173 2009-12-29 08:43 SBSettings.xml
drwx------ 1 nik  nik      0 2009-10-31 10:34 System Volume Information
drwx------ 1 nik  nik  28672 2010-02-18 09:33 TV Shows

```

---

### Post by watsoncj on 2010-02-24
For my setup I had to modify /etc/fstab to allow mediatomb access to read the files. The umask=000 is the magic piece. The uid and gid shouldn't be necessary, but if you use them make sure to use the right ids. You can get them by running the linux 'id' command.

/dev/sdb1       /media/win      ntfs    defaults,umask=000,uid=1000,gid=1000,noatime   0       0

---

### Post by moominpapa on 2010-04-05
> **watsoncj said:**
> For my setup I had to modify /etc/fstab to allow mediatomb access to read the files. The umask=000 is the magic piece. The uid and gid shouldn't be necessary, but if you use them make sure to use the right ids. You can get them by running the linux 'id' command.

/dev/sdb1       /media/win      ntfs    defaults,umask=000,uid=1000,gid=1000,noatime   0       0


Thanks for this, I changed this and it enabled my media server to access my external drive straight from boot, thanks alot.

---

### Post by WTBCompPro on 2010-07-29
Much Easier than this... to be able to add your files from a media source using the web UI simply run mediatomb as root in the terminal window

```

sudo mediatomb

```

Access the web UI and you shouldn't get that error. Worked for me but I did try changing privelages and what not, but it never worked until after I ran as sudo.

---

### Post by arst06d on 2010-08-11
I had the same problem but now sorted thanks to the info in this thread - cheers guys.

I have added my music folder on an external drive to the mediatomb server and it seems to have accepted it OK.  However, I'm trying to connect to the upnp server from a wireless internet radio which has upnp capability.  However, when I "Scan for PCs" none are found.

Is there anything else I need to do to start mediatomb serving, or to make the pc or designated music folder visible to the external upnp client?

Thanks in advance.

---

### Post by rshel on 2010-08-20
I'm getting the same error when trying to use mediatomb to access something in my home folder.  Why would it not be able to access the home folder for gods sake?

---

### Post by Mickafromparis on 2010-10-28
> **WTBCompPro said:**
> Much Easier than this... to be able to add your files from a media source using the web UI simply run mediatomb as root in the terminal window

```

sudo mediatomb

```

Access the web UI and you shouldn't get that error. Worked for me but I did try changing privelages and what not, but it never worked until after I ran as sudo.

it worked! thanks
but can start MT as a service...

---

### Post by yunone on 2011-04-19
> **rshel said:**
> I'm getting the same error when trying to use mediatomb to access something in my home folder.  Why would it not be able to access the home folder for gods sake?

did you ever sort out the permission issue? i am having the same issue with MT

---

### Post by Elilhrairrah on 2012-03-06
For the love of Ubuntu I cannot make my External or my internal HD for that matter, viewable by mediatomb. I have tried every fix in this thread. What the french toast?

Please help. 

(note - mediatomb is working just fine with my default HD, just not my slave, my 2TB HD, or any other USB drive)                        :confused:

---

