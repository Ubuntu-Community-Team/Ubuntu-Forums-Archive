---
title: "Help mounting windows network folders"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by cardsfan12 on 2010-07-10
I am trying to configure MPD (music player daemon) to work on my headless ubuntu server. Everything works well, but MPD cannot see the music files stored on my windows XP main computer. These files are stored at **smb://LASTNAME/share/music**

Is there a way to directly mount this drive, so it is accessible at something like **/mnt/music**, in order that they work with MPD?

---

### Post by bytbox on 2010-07-10
Yes. Install the package 'smbfs' - it will let you mount samba as a filesystem.

---

### Post by cardsfan12 on 2010-07-10
> **bytbox said:**
> Yes. Install the package 'smbfs' - it will let you mount samba as a filesystem.

How exactly do I make this work?

```
mount -t smbfs //LASTNAME/share/music /mnt/music
```

returns

```
mount error: could not resolve address for LASTNAME: No address associated with hostname
No ip address specified and hostname not found

```


However, 

```
/usr/bin/smbclient -L LASTNAME/share/
```

returns a list that sees /share/

---

### Post by bytbox on 2010-07-10
LASTNAME is not the hostname or ip address of the computer you're trying to connect to - as I understand it, for use with the smb:// format, you must use either the IP address or the hostname of the samba host. You can figure that out by poking around on the host (on windows, try typing 'ipconfig' into the command line).

---

### Post by cardsfan12 on 2010-07-10
> **bytbox said:**
> LASTNAME is not the hostname or ip address of the computer you're trying to connect to - as I understand it, for use with the smb:// format, you must use either the IP address or the hostname of the samba host. You can figure that out by poking around on the host (on windows, try typing 'ipconfig' into the command line).

the ip of the windows box is static, but ```
mount -t smbfs //192.168.1.3/share/music /mnt/music
``` returns the same error. Any ideas? Is there different syntax to mount samba that works better?

---

### Post by bytbox on 2010-07-10
Try -o ip=12.34.56.78 (whatever the IP is)

---

### Post by cardsfan12 on 2010-07-10
> **bytbox said:**
> Try -o ip=12.34.56.78 (whatever the IP is)

This doesn't work either, and whenever I add -o to the line, it just prints some kind of help/options list.

From what I've read online, something like 

```
root@mystery:~# mount -t smbfs -o username=Administrator,password=Password //LASTNAME/share/music /mnt/music
```

should work. However, the windows drive has no username or password (afaik), so I would expect 

```
root@mystery:~# mount -t smbfs //LASTNAME/share/music /mnt/music
```

to work. I don't understand why it doesn't. This is especially odd considering that samba sees the drive; for example smb://LASTNAME works.

---

### Post by capscrew on 2010-07-10
> **cardsfan12 said:**
> This doesn't work either, and whenever I add -o to the line, it just prints some kind of help/options list.

From what I've read online, something like 

```
root@mystery:~# mount -t **[COLOR="Red"]smbfs [/COLOR]**-o username=Administrator,password=Password //LASTNAME/share/music /mnt/music
```

should work. However, the windows drive has no username or password (afaik), so I would expect 

```
root@mystery:~# mount -t smbfs //LASTNAME/share/music /mnt/music
```

to work. I don't understand why it doesn't. This is especially odd considering that samba sees the drive; for example smb://LASTNAME works.

The use of smbfs (see above in red) is not used anymore.  Yes the "package" is smbfs, but you should use **[COLOR="Green"]cifs[/COLOR]**.  This is due to the updates to the CIFS/SMB protocol.  See ```
man mount.cifs
```.

I have not really looked at your specific problem, but ***cifs ***should be used none the less.

---

### Post by cardsfan12 on 2010-07-11
ok, after many hours of sweat, blood, and tears, I have managed to get this working.

As it turns out, neither smbfs or cifs like the -o command without specifying user name or password. I don't know whether this is a bug or a feature that I don't understand (probably the latter, I'm a linux noob), but in order to get it working, I finally settled on 

```
root@name:~$ mount -t cifs -o password=Hunter2 //123.456.78.90/share/music /mnt/music
```

For whatever reason, using the ip instead of the hostname was key. Also, kudos capscrew for pointing out that cifs is the newer, more acceptable way to go.

EDIT: hope this helps you out some Pi-rat. I'm an expert on this now (well...) so gimmie a shout if you want some help.

---

