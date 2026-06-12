---
title: "Win98 can't access samba shares"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-03-24
Moved from this thread: [http://ubuntuforums.org/showthread.php?t=815382](http://ubuntuforums.org/showthread.php?t=815382)

Here is my smb.conf, I think it's different

> [global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

What do I edit?

I also get an error:

> mpg@MIKED6:~$ sudo smbpasswd -a incoming
New SMB password:
Retype new SMB password:
Failed to modify password entry for user incoming

---

### Post by dmizer on 2009-04-12
As the OP suggests, you just need to add the "client lanman auth = yes" option to your smb.conf like so:
```
[global]
; General server settings
netbios name = MIKED6
server string =
workgroup = WORKGROUP
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

passdb backend = tdbsam
security = user
null passwords = true
[COLOR="Red"]client lanman auth = yes[/COLOR]
username map = /etc/samba/smbusers
name resolve order = hosts wins bcast

[COLOR="Red"]wins support = no[/COLOR]

printing = CUPS
printcap name = CUPS

syslog = 1
syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = yes
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
path = /var/lib/samba/printers
browseable = yes
guest ok = yes
read only = yes
write list = root
create mask = 0664
directory mask = 0775

[printers]
path = /tmp
printable = yes
guest ok = yes
browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = yes
;read only = yes
;guest ok = yes 
```

Also, you need to change wins support to "no" unless:
[LIST]
[*]you're hosting samba shares across multiple subnets, AND
[*]your samba server is the domain controller, AND
[*]your local network is static.
[/LIST]

---

### Post by RealG187 on 2009-04-13
> [global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    client lanman auth = yes
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes
It still doesn't work :(

---

### Post by dmizer on 2009-04-13
What doesn't work about it? Are you just trying to share a printer? If not, where is your share definition?

---

### Post by Iowan on 2009-04-14
> **RealG187 said:**
> I also get an error:Does "incoming" already exist as a Linux (Ubuntu) user?

---

### Post by RealG187 on 2009-04-14
When I try to connect it asks for a password and no matter what I put it says it's wrong!

---

### Post by dmizer on 2009-04-14
> **RealG187 said:**
> When I try to connect it asks for a password and no matter what I put it says it's wrong!

This is possibly because you have no share configured. In the smb.conf file you have posted there is no share definition at all. You'll need to include the directory you'd like to share at the bottom of your smb.conf file like so:

```
[NameOfShare]
    path = /directory/you/want/to/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = UBUNTU_USERNAME
```

---

### Post by RealG187 on 2009-04-15
I have one called incoming Windows 2000 and XP see it. I added that share by right clicking it's properties in Nautilus.

Funny when I added the share via the smb.conf file I couldn't add new shared by the properties window in Nautilus.

---

### Post by dmizer on 2009-04-15
> **RealG187 said:**
> I added that share by right clicking it's properties in Nautilus.
You'll have to configure your "incoming" share in your /etc/samba/smb.conf file in order to allow your Windows 98 computer to see it.

---

### Post by RealG187 on 2009-04-16
If I use the properties sheet doesn't it already add it to smb.conf?

The last time I manually added the share to my smb.conf file I could no longer use the propery sheet to share a folder. Now I am able to use the propery sheet and I don't wanna change anything...

But even if I just type \\miked6 and specify no share it asks for a password, it won't even let me see the shares.

---

### Post by dmizer on 2009-04-16
> **RealG187 said:**
> If I use the properties sheet doesn't it already add it to smb.conf
No, it does not.

> **RealG187 said:**
> The last time I manually added the share to my smb.conf file I could no longer use the propery sheet to share a folder.
Yes, this is by design.

> **RealG187 said:**
> Now I am able to use the propery sheet and I don't wanna change anything...
Then you will be unable to view your share with Windows 98.

At this point, all I can say is that you'll have to weigh your options. What's more important to you: viewing the share with Windows 98, or being able to configure shares in folder properties?

---

### Post by RealG187 on 2009-04-17
How come it's design? That's why samba in Ubuntu is such a pain to setup.

I could just have one share and should I need to share a file I could move it there, or make a Symlink if it can't be moved.

---

### Post by dmizer on 2009-04-18
> **RealG187 said:**
> How come it's design?

For the same reason that two people can't drive a car at the same time.

You can't control the same protocol (samba) with two different samba servers.

This is true of many protocols in Windows as well, it's not a peculiarity of Linux. You don't see this exact issue in Windows, because in Windows, there's only one way to share files over samba.

---

### Post by RealG187 on 2009-04-18
They should just make it that when you use the property sheet it does the exact same thing as if you edited smb.conf

---

### Post by dmizer on 2009-04-19
> **RealG187 said:**
> They should just make it that when you use the property sheet it does the exact same thing as if you edited smb.conf
That would be an extreme security hazard.

Folder properties runs in user space with GVFS (not samba). However, /etc/samba/smb.conf runs on the system as a service. If GVFS were given access to /etc/samba/smb.conf, it would be a huge security hole through which someone could easily gain root access to your computer.

---

### Post by RealG187 on 2009-04-20
How would someone get access to GVFS though?

They should make it when you create a share from the folder properties it asks for the password and then adds it to smb.conf

---

### Post by dmizer on 2009-04-20
> **RealG187 said:**
> How would someone get access to GVFS though?
According to Iowan in this thread: [http://ubuntuforums.org/showthread.php?t=1125330](http://ubuntuforums.org/showthread.php?t=1125330) the configuration files are in /var/lib/samba/usershares, but I know nothing beyond that.

> **RealG187 said:**
> They should make it when you create a share from the folder properties it asks for the password and then adds it to smb.conf
Why? Because you need it in this single case? GVFS provides simple file share functionality for most situations. It works well with Gnome's network-manager utility, and it's dead simple to configure. Doing more adds complexity and increases the chances that it could be used maliciously.

Sure, you could have two people drive the same car if one sat on the other's lap, but that would be dangerous and the police would pull you over for it.

---

### Post by RealG187 on 2009-04-20
The properties Window wouldn't be sitting on GVFSes lap, it would be a "backseat driver"

---

### Post by dmizer on 2009-04-20
> **RealG187 said:**
> The properties Window wouldn't be sitting on GVFSes lap, it would be a "backseat driver"

Back seat drivers have no actual control. At best, they have suggestive power which can be ignored if so desired. If you allow GVFS to edit smb.conf, you're giving GVFS real and actual control to Samba. That's dangerous.

Either way, it comes down to this
> **dmizer said:**
> At this point, all I can say is that you'll have to weigh your options. What's more important to you: viewing the share with Windows 98, or being able to configure shares in folder properties?

Edit, moved this to its own thread as it was fairly well off topic.

---

### Post by RealG187 on 2009-05-01
I think I got it!!

```
[global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    client lanman auth = yes
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[incoming]
    path = /home/mpg/Desktop/Incoming
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = mpg
```

Upon changing it from "User" to "Share" I was able to view "\\MIKED6" (before it would ask for the password. I seen the name of the share "Incoming" but it asked when I double clicked. I then changed guest ok = no" to yes!!!

---

### Post by Cool Javelin on 2010-09-27
Hello, I have been trying to get my windows (win98 and XP) to access a new server 10.04.1 install.

I have another xubuntu, 8.04, that my windows can access.

I note all references to workgroup show uppercase group name ie.

workgroup = WORKGROUP

I know linux is case sensitive, does 10.04 need upper case workgroup name?

The 8.04 Linux has a lower case name (workgroup = workgroup)

I have searched the forums and I don't see an answer.

Thanks,
Mark.

---

### Post by dmizer on 2010-09-27
Microsoft typically uses an all uppercase workgroup name by default. I believe that even if you send a lower case workgroup to the server, it still is read as upper case, but I am not positive about it. The default smb.conf file in 8.04 has an all upper case workgroup, so if it is not all upper case in your system, it's been manually changed.

Convention is to use all upper case, so that's what I would suggest.

---

