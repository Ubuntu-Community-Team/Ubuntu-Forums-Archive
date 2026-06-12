---
title: "amarok issue over network &amp; Is it possible to mount a smb windows share to a folder?"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by BlakeEM on 2006-07-08
Here's why I'm looking to do this.

I have my laptop with ubuntu 6.06 and I installed amarok to play music.

I have a shared folder on my windows PC with all my music (mp3s) and I want to listen to it on my laptop.

I can see everything fine, however when I try to play something in amarok it pops up with an error saying that it's unable to find my mail client (kmail, I'm not sure why kmail) and then amarok crashes and I have to force close.

I'd make a guess that this is because of the smb: path because I play local mp3s just fine.

I'm guessing the way around this is to mount the smb folder so that amarok won't be confused about the path. Is this possible? I did some searching and it seems like it is but when I tried to mount it from the console I get various errors.

As it is now I'm unable to play any music directly off the smb share on any player unless I copy it over. Movies however play great over the network as do viewing images.

Any help would be appreciated.

---

### Post by raldz on 2006-07-08
I'm using Amarok in Kubuntu combined with Smb4k to play MP3 files across the network.. I don't know if Smb4k will work seamlessly with Gnome, but here is how I did it..

>install Smb4k from synaptic or adept
>invoke smbmnt as root: 
```
sudo chmod u+s /usr/bin/smbmnt
```

>check if the permissions have been correctly set by typing:
```
ls -l /usr/bin/smbmnt
```

you should get a result similar to this:
```
-rwsr-xr-x 1 root root 10520 2006-07-07 06:05 /usr/bin/smbmnt
```

note that the -rwsr-xr should be small letter S. if not, try to invoke it again..

---

### Post by BlakeEM on 2006-07-08
I got it working, I had to install smbfs and I was able to do an smbmount and worked great.

---

### Post by raldz on 2006-07-08
cool.. enjoy.. ;) ;)

---

### Post by Tass on 2006-11-02
Hey

I've been having a similar problem, which I've solved 99%.  As you've mentioned, I had to install smbfs from the repositories.  Once I'd done that, I could mount the windows shares I needed from the terminal with :

sudo mount //machinename/sharename /media/windowsshare

I added a similar line to fstab :

sudo mount //machinename/sharename /media/windowsshare smbfs

Now, when I run 'sudo mount -a' from the terminal, I get prompted for my root password for each share in the file, and each share is mounted.  All good.

However, if I restart, the shares don't mount automatically.  All the other devices specified mount on restart - just not my network shares.

Any ideas?

Thanks,

Tass

---

### Post by thegnu on 2006-11-12
I've had trouble mounting samba shares (it causes crashes, and other anomalies), so I just use the smb:// path.  To enable support in amarok for smb:// URLs, install package:

kdebase-kio-plugins

Then I typed in to the amarok path field smb://titan/share/music, and I was there!

---

### Post by [d3v] on 2006-12-20
To mount the shares at boot time try something like the following in your fstab file:

> 
# My mounts
//vb-2nn7h1s/music      /mnt/music      smbfs credentials=/path/to/credentials_file,uid=USER_NAME,gid=GROUP_NAME 0 0


This will try to load the credentials to use for the mount from the file you specify. The USER_NAME and GROUP_NAME just make the mounted files belong to the user/group specified. This means they are not owned by root:root.

An example credentials file is (if in a domain):
> 
username=DOMAIN/user
password=pa$$w0rd

or 
> 
username=user
password=pa$$w0rd


A good place to put the credentials file is ${home}/.smb/credentials so the line in fstab would be in my case:
> 
credentials=/home/shane/.smb/credentials


Once you have created this file, set it to only be accessible by you unless you want others getting your password ;-)

> 
chmod 600 /home/shane/.smb/credentials


Now you should have your share already mounted at boot time! You can then mount your shares without the prompt for password. Just remember the credentials file must contain a valid login with access to the share. You can also have multiple credentials files if you need different user names to access different shares. Just name them appropriately and link to them for the share that needs it.

---

### Post by total wormage on 2007-01-21
i've got two tiny problems with amarok over the network so i thought posting it here instead of making a new thread of it, 'cause it's not worth it ;]

case one: i can play files succesfully with amarok over the network, but i can't skip within the files, i figured this would be because amarok somehow makes a stream or something from my files and only makes a buffer for a few seconds, but doesn't know how long the tracks are.
not very annoying for me (everyone should listen to whole albums, the way music is meant to be! :p) but my roommates want to skip for some reason.
so help would be appreciated, even if i have to ditch amarok for another media player (not rhytmbox!)

two: i have made a last.fm account for that computer and i thought it would be fun to see the stats of my house. i'm living with 7 roommates with different music tastes. but amarok doesn't seem to submit to that account (i think for the same reason as the above)
i have configured amarok the way it should be and nothing is blocking it's connection with the internet, i'm also not getting 'amarok wasn't able to submit tracks' errors

as i said, these are not very big problems, but it would be nice if they were solved :D
:KS

---

