---
title: "Incoming local network connections fail"
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by ardvark on 2010-05-24
I have recently done a fresh load of Ubuntu 10.4 coming from 8.04. At this point on my home network, the linux PC can access shares on 2 Windows PCs, However the Windows PCs cannot connect nor can my Roku media player. The Roku is showing "Port 139 closed", Ettercap shows "Port 139 killed".

On Launchpad there are several cases of Samba not actually running, even though it was loaded. So first I would like to know if I'm looking in the right spot to see if smbd and nmbd are actually running. I checked first the system monitor, they don't show there. I then went to terminal and did the "top" command, they do not show there either. Stopping and restarting make no difference, I see a PID assigned but when I immediately type top, that PID does not show up.

If, indeed, these processes are not running, has anyone got things running by removing and re-installing? I believe on Launchpad I also someone having problems reloading Samba.

---

### Post by Iowan on 2010-05-24
To see if **smbd** and/or **nmbd** is running: ```
 ps -ef |grep mbd

```

---

### Post by ardvark on 2010-05-25
Ok, I get this resilt:

root       664     1  0 09:13 ?        00:00:00 smbd -F
root      1134     1  0 09:13 ?        00:00:00 nmbd -D
dalew     2008  1990  0 11:14 pts/0    00:00:00 grep --color=auto mbd


What brought up the question of whether it was running or not is if I try to mark a folder as shared I get this:

*'net usershare' returned error 255: net usershare add: cannot convert name "Everyone" to a SID. The connection was refused. Maybe smbd is not running.*


If I run GADMIN-SAMBA I never see users listed even though I tried adding them with smbuser. So at this point nothing is connecting inward to my linux PC, so perhaps something is still not setup in Samba. I'd try NFS, but I'm not sure how the Roku HD1000 is set up for that.

---

### Post by ardvark on 2010-05-31
In case someone finds this thread, I did get things running enough to meet my needs. I had to do several things:

(1) Removed and reloaded Samba, if you look at my old process list and the one I have now:

root       744     1  0 08:04 ?        00:00:00 smbd -F
root       805   744  0 08:04 ?        00:00:00 smbd -F
root      1802     1  0 08:04 ?        00:00:00 nmbd -D
root      2658   744  0 10:57 ?        00:00:00 smbd -F

 you can see quite a difference. Before I couldn't add a share name to a folder.

(2) Per a trouble shooting procedure I found, I checked that I could ping between each PC with both IP and name. (that wasn't working completely)

(3) Per another setup procedure I found. Threw out the default smb.conf file that gets loaded with the program. There's something in that file that kept my media player from connecting. Here's the simple smb.conf file I'm using:

[global]

workgroup = HOME
netbios name = linux1
encrypt passwords = yes

[homes]
path = /home
read only = no
browseable = no

[media]
path = /home/roku
browseable = yes
read only = yes
public = yes

This is not perfect, at least once I've got the infamous "Can't find network share file" message. and couldn't connect to my Windows PC's.

---

