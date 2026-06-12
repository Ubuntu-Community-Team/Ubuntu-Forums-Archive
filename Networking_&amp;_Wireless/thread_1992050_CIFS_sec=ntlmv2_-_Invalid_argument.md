---
title: "CIFS sec=ntlmv2 - Invalid argument"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by CrioStage on 2012-05-31
Hello,

I been looking around the internet, forums and other sources like mail listing for an solution for my problem however i was unable to find any conclusion. This is my situation.

I have 2 computers one is an Windows 2008 Server the other is an Ubuntu Server 12.04 LTS witch were connected using fstab's on the Ubuntu machine. Some of the users would add files on the Windows 2008 and the remaining would consult them as read only on the linux machine using an web front end. This worked fine until 2 days ago when the system administrator of the Windows 2008 changed the authentication of the OS for "NTLMV2 Only" and here the problems on ubuntu started.

this is what i had in my fstab file:

```

//servername/share /mnt/mountpoint/ cifs username=someuser,password=somepass,ro,auto 0 0

```

Researching arround i changed the line to:

```

//servername/share /mnt/mountpoint/ cifs username=someuser,password=somepass,sec=ntlmv2,ro,auto 0 0

```

and did:

```

mount -a
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

Since it didnt worked, trying to do an manual mount i would get this error:

```
 
sudo mount.cifs //servername/share /mnt/windows/ --verbose -o username=someuser,sec=ntlmv2
Password:
mount.cifs kernel mount options: ip=192.168.0.1,unc=\\192.168.0.11\share,sec=ntlmv2,ver=1,user=someuser,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

the syslog:

```

May 31 12:55:31 SMBFS kernel: [ 8504.071635] Status code returned 0xc000000d NT_STATUS_INVALID_PARAMETER
May 31 12:55:31 SMBFS kernel: [ 8504.071653] CIFS VFS: Send error in SessSetup = -22
May 31 12:55:31 SMBFS kernel: [ 8504.125023] CIFS VFS: cifs_mount failed w/return code = -22

```

Without the sec=ntlmnv2 option and correct credentials i get:

```

mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

At first i tough maybe the sec argument is not valid but doing man mount.cifs the sec argument sec with the ntlm is really there. At this point i have no idea what todo, have anyone ever came across this issue with an Windows 2008 server?

---

### Post by CrioStage on 2012-05-31
Well it's solved, we lowered the ntlmv2 to ntlm and didnt worked right away but after doing the mount this way now works:

```

sudo mount -t cifs //computer/share/ /mountpoint/ -o user=user,pass=somepass,sec=ntlmssp

```

---

