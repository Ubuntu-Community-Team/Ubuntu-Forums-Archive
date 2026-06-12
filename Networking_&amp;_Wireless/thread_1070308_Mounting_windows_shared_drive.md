---
title: "Mounting windows shared drive"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by sa125 on 2009-02-15
Hi - 

I work in an office environment where most of the machines have WinXP installed. We have a few shared drives on our server that are mapped using the windows UNC path of \\server\drivename, which can than be mapped to a drive in the windows OS (like K:\, H:\, etc). 

I am probably the only person around running ubuntu, and I need to be able to easily access these drives with some form of mounting. Right now, I can access them with the long smb address of the form:
```
smb://domain;username@server-ip-address/drivename/...
```
but I wanted to see if there's any way to mount it so that the access will be simpler - something like /server/drivename or similar. This is mostly so I can have better access in programs and scripts that read from these drives. The server, I believe, is actually running Ubuntu 6.06 (linux 2.6.15-26).

Thanks.

---

### Post by graysky on 2009-02-15
Might be a limitation of the version of Gnome in Dapper - get the latest release (8.10) since it'll be using the latest (as of the time of my post) stable version of Gnome which will be much better than the one you're using!  So long as you put the name and IP addresses of the XP boxes in your office into your /etc/hosts file, you can simple connect to them like this from any nautilus window:

```
smb://windows_name
```

Further, you can add a bookmark to a share of interest which will add that share to your nautilus panel which you can now single click.  Again, I dunno of the version of Gnome in Dapper has this feature - Intrepid comes with Gnome 2.24.1 and this is included.

Alternatively, mount the shares from a shell, I use a script similar to the following:

```
#!/bin/bash
sudo mount -t cifs -o credentials=/root/.smbcreds,uid=1003,gid=1003 //192.168.1.5/share /media/share
```

Save and make it executable.  In my example, I called it "mount.sh":
```
$ chmod a+x mount.sh
``` 

Make sure that your Ubuntu user's id (uid) and group id (gid) are sync'ed up to the numbers you add to the script.  Verify this as follows:

```
$ cat /etc/passwd
```

This will output all the users on your system.  Look for your username and use the two numbers (the 1st is uid, the 2nd is gid).

Example from mine: 
```
toolshed:x:1003:1003:toolshed,,,,:/home/toolshed:/bin/bash
```

Also, you'll create a credentials file that stores the username/password for this particular share as follows:

```
$ sudo nane /root/.smbcreds
```

Make this file two lines as follows:
```
username=windows_username
password=windows_password
```

Replace "windows_username" with your actual windows xp user name and likewise for the "windows_password" entry.  Save the file.  Now let's make it accessible only to the root user as follows:

```
$ sudo chmod 600 /root/.smbcreds
```

The 192.168.1.5/share is the IP address of the windows machine and the /share part is the name of the windows share I'm mapping.  Finally, the /media/share is the directory where the share will show up on my LINUX machine.

That's it.  If your username/password in windows is the same for other xp machines in your office, you just have to change the IP address that you're pointing to obviously.

To unmount a given share, simply issue the following:

```
$ umount /media/share
```

---

### Post by sa125 on 2009-02-15
Wow, that's really thorough - thanks.

I tried your suggestion with writing the bash script to mount the shared drive. I changed the mounting to look something like this:
```

sudo mount -t cifs -o credentials=/root/.smbcreds,uid=1002,gid=1002 //192.168.20.10/sharedata /mnt/sharedata
```
But got the following error:```

mount: mount point /mnt/sharedata does not exist.
mount: wrong fs type, bad option, bad superblock on //192.168.20.10/sharedata, missing codepage or helper program, or other error...
```

Of course, I did all this on my local machine (as root) and not on the server. I'm running intrepid, but upgrading the server is out of my hands.

As for your first methods, I'm not sure I follow - what exactly should go into the /etc/hosts file?

Thanks for your help.

---

### Post by sa125 on 2009-02-15
Ah, I see about the smb://windows_path in nautilus now, and it works great.

This is probably a long shot, but I'll ask - I tried using it in python/ruby scripts (which are 80% of why I need this in the first place), and it wouldn't recognize that path:

in ruby:
```
irb> Dir.chdir('smb://server/sharedata')
```

in python:
```
>> os.listdir('smb://server/sharedata')
```

Both give me no such file or directory error... Any chance you know how to access that from there?

thanks again!

---

### Post by graysky on 2009-02-15
> **sa125 said:**
> Wow, that's really thorough - thanks.

I tried your suggestion with writing the bash script to mount the shared drive. I changed the mounting to look something like this:
```

sudo mount -t cifs -o credentials=/root/.smbcreds,uid=1002,gid=1002 //192.168.20.10/sharedata /mnt/sharedata
```
But got the following error:```

mount: mount point /mnt/sharedata does not exist.
mount: wrong fs type, bad option, bad superblock on //192.168.20.10/sharedata, missing codepage or helper program, or other error...
```

Of course, I did all this on my local machine (as root) and not on the server. I'm running intrepid, but upgrading the server is out of my hands.

As for your first methods, I'm not sure I follow - what exactly should go into the /etc/hosts file?

Thanks for your help.

I'm assuming you did make a directory on your machine called /mnt/sharedata (made it under your normal user)?

In the /etc/hosts you just put the windows name you want and it's ip addy.  Example:

```
popcorn    192.168.1.1
bucket     192.168.1.2
redbull    192.168.1.3
```

You can then use one of the names in place of the ip addy in a mount statement, or a ping, etc.

> **sa125 said:**
> This is probably a long shot, but I'll ask - I tried using it in python/ruby scripts (which are 80% of why I need this in the first place), and it wouldn't recognize that path:

in ruby:
```
irb> Dir.chdir('smb://server/sharedata')
```

in python:
```
>> os.listdir('smb://server/sharedata')
```

Both give me no such file or directory error... Any chance you know how to access that from there?

thanks again!

Sorry dude, I dunnno sh*t about python/ruby.  I'm still struggling through basic BASH scripts :)

---

