---
title: "nautilus (gvfs) can mount, no way in the shell (mount -t cifs)"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by phibuntu on 2010-09-02
Hi all

My actual problem is the cifs file system. I want to mount a windows network drive to a mountpoint under [FONT="Courier New"]/mnt[/FONT] (eg. [FONT="Courier New"]/mnt/winserver[/FONT]).

Using nautilus under the Ubuntu-Main-Menu (places -> Network) I can find the server and login using my username, the domain and share name and of course my password

eg>
```
server=//OURNETWORK
shareddrive=/ourdata$
username="phi.gre"
domain="OURDOMAIN"
pass="verysecret"
```

It finally mounts to "~/.gvfs".

Using the midnight commander I can work like this.

Now I want to connect to the server using a shell script.
For that I created a .credentials-File ([FONT="Courier New"]/home/me/path/to/.credentials[/FONT]) like this
```
username=phi.gre
password=verysecret
```

using [FONT="Courier New"]>ip route[/FONT] I have found the default gateway ( "192.168.10.8" ) and my script looks now like this (all personal data changed):

```
SB_PARAMS=credentials=/home/me/path/to/.credentials,ip=192.168.10.8,gid=1001,uid=me,dir_mode=0700,domain=OURDOMAIN,iocharset=utf8

mount -t cifs //OURNETWORK/ourdata$  /mnt/winserver/ --verbose -o ${SB_PARAMS}
```

Now the above script always times out after about 30 seconds:

```
mount.cifs kernel mount options: unc=//OURNETWORK\ourdata$,user=phi.gre@OURDOMAIN,ver=1,rw,credentials=/home/me/path/to/.credentials,ip=192.168.10.8,dir_mode=0700,domain=OURDOMAIN,iocharset=utf8,uid=1000,gid=1001,pass=********
mount error(110): Connection timed out
```

Is there a possibility to
a) find out, how nautilus mounts the device?
b) find the errors i my script (/var/log/messages mentions nothing)

Any Idea? Which thread could be helpful?

Thanks in advance

---

### Post by clrg on 2010-09-02
Try without the IP parameter.

---

### Post by phibuntu on 2010-09-02
Thanks for your answer. I have done so before and get the following error:

```
mount error: could not resolve address for OURNETWORK: No address associated with hostname
No ip address specified and hostname not found
mount error: could not resolve address for OURNETWORK: No address associated with hostname
No ip address specified and hostname not found
```

---

