---
title: "Cant Mount a Network Share in Karmic"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by sir_robert007 on 2009-12-22
Ok let me first say that I am currently studying for CompTIA Lunix certification. One of the things we did in my computer class was mounting a network share via command line. I tried do the same on my Ubuntu box, (as that is the linux distro we used). The command I used was sudo mount -t cifs //ipaddress/share /mnt, where /mnt is the folder that I am trying to mount the share in. I tried to execute the command, but the share would not mount. Is it something that has to do with the computer the share is on, or am I not using the proper command syntax?


An answer ASAP would be much appreciated
Oh I'm using Karmic on both machines btw

---

### Post by ankur1990 on 2009-12-22
sudo mount -t cifs //ipaddress/share /mnt, where /mnt
i think the syntax is wrong
 sudo mount -t cifs username=name (from where u r sharing) //ipaddress/share /mnt, where /mnt

---

### Post by sir_robert007 on 2009-12-23
> **ankur1990 said:**
> sudo mount -t cifs //ipaddress/share /mnt, where /mnt
i think the syntax is wrong
 sudo mount -t cifs username=name (from where u r sharing) //ipaddress/share /mnt, where /mnt

Ah ok I had a feeling I was doing something wrong. I shall give this a try and post back on the results.  

Oh what if there is a password on the account of the computer where the share is? Is there a "password=" field like with the username?

---

### Post by Iowan on 2009-12-23
[This]("http://ubuntuforums.org/showthread.php?t=288534") How-To may be overkill, but probably has your answer.

---

### Post by AlexDBall on 2009-12-23
i use this kind of command on each login to mount shares from my ubuntu server (samba)

```
smbmount "//*ipaddress*/*share*" "/*mnt/sharenam*e" -o credentials=*/home/username/.smbpass*
```note that i am using a file for the credentials, this is just a text file with the following lines:

```
username=*username*
password=*password*
```i hope this helps!

---

### Post by Morbius1 on 2009-12-23
It's quite likely I'm confused about your description but you can't mount anything to /mnt.

You can mount something to /mnt/mount_point.

Me thinks you need to create a mount point first:

sudo mkdir /mnt/mount_point

Then alter your mount command to change **/mnt** to **/mnt/mount_point**.

---

### Post by sir_robert007 on 2009-12-23
> **Iowan said:**
> [This]("http://ubuntuforums.org/showthread.php?t=288534") How-To may be overkill, but probably has your answer.

ok heres what ive tried based on that guide you provided. First a created a folder called netest in the /media directory. Then i typed in the following command 

sudo mount -t cifs //10.0.0.4/test /media/netest/ -o username=(username of account share is on), password=(password of account).

I executed the command but its saying i am not using the proper command usage. Other variations of the command that i have tried include:


sudo mount -t cifs //ip_address/test/ 

sudo mount -t cifs //ip_address/test/ /mnt/mount_point
(test is the name of the share)

on that last command it asked for a password, so I entered the password of the account of the computer the share was on, but when I executed it I got the following error: "mount error(13): Permission denied"




edit: i finally managed to mount the network share by typing the following command: "   	 	 	 	 	 	  sudo mount -t cifs //ip_address/test /media/netest/ -o username=(username of computer share is on)". It asked me for a password, i entered it and i was able to mount the share

---

### Post by Iowan on 2009-12-24
So the successful version left off the password (which was supplied later)?
Did you happen to try using the credentials file?

Another thing I noticed: looks like your "password" version has a space before "password" - the How-To has no spaces in the options. Dunno if they're critical, but might be another permutation to try.

---

### Post by dmizer on 2009-12-24
> **Iowan said:**
> Dunno if they're critical, but might be another permutation to try.

Yes, it is quite critical to pay attention to where there are and are not spaces.

---

### Post by sir_robert007 on 2010-01-11
Ok I have one last question. Now that I have figured out how to mount a share via command line, how can I accomplish the same result via the Gnome interface?

---

### Post by Iowan on 2010-01-11
Not exactly via Gnome, but check **dmizer's** signature, link #2 (happens to be the same one I "borrowed") -the permanent mount section.

---

