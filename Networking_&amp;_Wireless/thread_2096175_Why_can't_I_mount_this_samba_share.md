---
title: "Why can't I mount this samba share?"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by wagoner on 2012-12-19
I have two desktop computers connected by a router on a home network.  Samba is working beautifully and I can browse the network shares with dolphin.  The names resolve to the netbios names and when I access the share, I am prompted for a username and password.  I am trying to mount the share with this command.

```
adam@adam-Dell16:/mnt$ sudo mount -t cifs \\\\LINUX-HIHN\\adam /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:/mnt$ 

```

This is what I get with smbclient.  Seems to work fine.
```
adam@adam-Dell16:~$ smbclient -NL LINUX-HIHN
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Sharename       Type      Comment
        ---------       ----      -------
        profiles        Disk      Network Profiles Service
        users           Disk      All users
        groups          Disk      All groups
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386)
Anonymous login successful
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386]

        Server               Comment
        ---------            -------
        ADAM-DELL16          Samba 3.5.11
        LINUX-HIHN           Samba 3.6.10-146.1-2889-SUSE-SL11.4-i386
                                                                                                
        Workgroup            Master
        ---------            -------                  
        WORKGROUP            LINUX-HIHN

```

What is wrong?:confused:

I read in another post that the user resolved a mount problem by changing the password on the samba server to something different from the one on the samba client.  I happen to use the same username and password on both computers.  Could that be the problem?

---

### Post by redmk2 on 2012-12-19
> **wagoner said:**
> ... I am trying to mount the share with this command.

```
adam@adam-Dell16:/mnt$ sudo mount -t cifs \\\\LINUX-HIHN\\adam /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:/mnt$ 

```
...

What is wrong?:confused:

I read in another post that the user resolved a mount problem by changing the password on the samba server to something different from the one on the samba client.  I happen to use the same username and password on both computers.  Could that be the problem?

I believe the correct incantation is ```
sudo mount -t //SERVER_NAME/share_name /path/to/mountpoint -o <options>
```
[COLOR="Blue"]Edit:  I have updated this to include the mountpoint.[/COLOR]
[COLOR="Blue"]Edit 2:  Yes I missed adding the FS type.  It shuld have been cifs The smbfs package is depricated. The package points to cifs now anyway. [/COLOR]

The two passwords can be the same.

---

### Post by wagoner on 2012-12-19
redmk2, I think the mount command that you provided is missing a mount type.  It needs to be
 ```
mount -t cifs
```or
```
mount -t smbfs
```or something.  Perhaps it would work without the -t.  

Anyway I tried it again, changing the slashed like you suggested.  This time I defined a share named LaundrySink, instead of relying on the automatic homes share that opensuse configured for me.  (LINUX-HIHN is using openSUSE 11.4)  Didn't help, I'm still stuck.:sad:

```
adam@adam-Dell16:~$ sudo mount -t cifs //linux-hihn/LaundrySink /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:~$ sudo mount //linux-hihn/LaundrySink /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by bfmetcalf on 2012-12-19
> **wagoner said:**
> redmk2, I think the mount command that you provided is missing a mount type.  It needs to be
 ```
mount -t cifs
```or
```
mount -t smbfs
```or something.  Perhaps it would work without the -t.  

Anyway I tried it again, changing the slashed like you suggested.  This time I defined a share named LaundrySink, instead of relying on the automatic homes share that opensuse configured for me.  (LINUX-HIHN is using openSUSE 11.4)  Didn't help, I'm still stuck.:sad:

```
adam@adam-Dell16:~$ sudo mount -t cifs //linux-hihn/LaundrySink /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
adam@adam-Dell16:~$ sudo mount //linux-hihn/LaundrySink /mnt/sink -o username=adam
Password: 
mount error(115): Operation now in progress
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

You could try using the IP of the box instead of linux-hihn and see if it gets you anywhere.

---

### Post by steeldriver on 2012-12-19
I'm wracking my brain because I'm sure I've encountered the mount.cifs 'Operation now in progress' error quite recently - but I can't remember what the solution was

I believe your original syntax was fine - although according to the mount.cifs man page the preferred form is 'user' not 'username' (the latter is apparently retained for compatibility with smbfs)

```
$ sudo mount -t cifs \\\\nas-01.local\\steeldriver /mnt/nas-01/steeldriver -o username=steeldriver
Password:
steeldriver@faye:~$ ls /mnt/nas-01/steeldriver
Application Data  Family  Gear   Household  IT    Music      My Pictures
steeldriver@faye:~$

```I guess it's possible that it's not able to resolve the hostname - although in that case I think the error message would indicate that, e.g.

```
$ sudo umount /mnt/nas-01/steeldriver
$ sudo mount -t cifs \\\\nas-01\\steeldriver /mnt/nas-01/steeldriver -o username=steeldriver
mount error: could not resolve address for nas-01: Unknown error
```Sorry I can't be more help here

---

