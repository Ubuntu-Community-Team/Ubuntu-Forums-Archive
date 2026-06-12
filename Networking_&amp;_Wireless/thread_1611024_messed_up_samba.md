---
title: "messed up samba"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by ubunterooster on 2010-11-01
Trying to get a share going with Vista and 7, I messed something up and decided that I would delete the samba.config file and once I started samba again the file would be remade. This did not work and after trying to pruge and reinstall samba which did not work, I deleted the etc/samba folder. This still did not work.


So.... how do I recover from this?

Samba's testparm returned error 1: Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
params.c:OpenConfFile() -[COLOR=Red] Unable to open configuration file "/etc/samba/smb.conf":
    No such file or directory[/COLOR]
Error loading services.

---

### Post by luvshines on 2010-11-01
See if you have a default copy(comes with samba-common) of smb.conf at this location```

/usr/share/samba/smb.conf

```

---

### Post by ubunterooster on 2010-11-01
Okay, I took that and copied it to the place where it should be.

---

### Post by ubunterooster on 2010-11-01
Okay, I can now tell Samba to share a folder but when I do it flickers, and when it comes back, the "share" option is deselected

---

### Post by Morbius1 on 2010-11-01
I hope you don't mind the interruption but what are you using to share - Nautilus or some specific samba GUI app?

---

### Post by ubunterooster on 2010-11-01
I am using nautilus-share

---

### Post by Morbius1 on 2010-11-01
Why not post the output of the following commands so folks on this thread can see how things are configured:
```
net usershare info --long
```
```
testparm -s
```

Also run the following command and see if you are a member of the **[COLOR=Blue]sambashare[/COLOR]** group:
```
id
```

---

### Post by ubunterooster on 2010-11-01
```
ubunterooster@mountaindew:~$ net usershare info --long
ubunterooster@mountaindew:~$ 
```Okay; nothing there```
ubunterooster@mountaindew:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[Backup]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    encrypt passwords = No
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[Backup]
    comment = Shares
    path = /media/Backup
    read only = No
    guest ok = Yes
ubunterooster@mountaindew:~$ 
``````

ubunterooster@mountaindew:~$ id
uid=1000(ubunterooster) gid=1000(ubunterooster) groups=1000(ubunterooster),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),[COLOR=Blue]122(sambashare)[/COLOR],126(libvirtd),1004(smbshare)
ubunterooster@mountaindew:~$ 

```

---

### Post by Morbius1 on 2010-11-01
Aside from one mistake in your copy of smb.conf:
>      encrypt passwords = No[COLOR=Blue]That should be changed to Yes[/COLOR]

It's not apparent that anything is wrong with that.

After you copied the smb.conf file did you restart samba:
```
sudo service smbd restart
```

---

### Post by ubunterooster on 2010-11-01
After changing that to yes, I restarted smbd and then the computer. 
 
I can see the shared folders but am unable to connect: 
"Unable to mount location
Failed to mount Windows share"

---

### Post by luvshines on 2010-11-01
Also check if you can access them by terminal:
```

## Access the shares. Use -U% for Guest login
smbclient //<server-ip>/<share-name> -U<user>%<passwd>

```

---

### Post by ubunterooster on 2010-11-01
```
ubunterooster@mountaindew:~$ ## Access the shares. Use -U% for Guest login
ubunterooster@mountaindew:~$ smbclient //<server-ip>/<share-name> -U<user>%<passwd>
bash: syntax error near unexpected token `newline'
ubunterooster@mountaindew:~$
```

---

### Post by luvshines on 2010-11-01
Oh ok, did you replace <...> with actual values(ip, share-name, username and password) ?

---

### Post by ubunterooster on 2010-11-01
Oops!

---

### Post by ubunterooster on 2010-11-01
I forget how to check the IP

---

### Post by luvshines on 2010-11-01
> **ubunterooster said:**
> After changing that to yes, I restarted smbd and then the computer. 
 
I can see the shared folders but am unable to connect: 
"Unable to mount location
Failed to mount Windows share"

IP can be determined by ifconfig command on Linux and ipconfig on Windows

Just a question, you are trying to share Ubuntu directories and trying to access from Vista, right ?

Or is it the other way round ?

---

### Post by Morbius1 on 2010-11-01
```
ifconfig
```
Your ip address in after "inet addr:"

Also a "failed to mount" sometimes relates to a Linux permissions problem.

What's the permissions on /media/Backup:
```
ls -dl /media/Backup
```
And is it an NTFS or FAT32 partition by any chance?

---

### Post by Morbius1 on 2010-11-01
OOPS, Sorry for butting in luvshines :oops:

---

### Post by ubunterooster on 2010-11-01
```
ubunterooster@mountaindew:~$ smbclient //192.168.122.1/Backup -Uubunterooster%**********
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]
smb: \> 
smb: \> 
```Good or not? Sorry but I had less than 4hr sleep last night and dealt with two security breakins and am fried

---

### Post by ubunterooster on 2010-11-01
> **Morbius1 said:**
> OOPS, Sorry for butting in luvshines :oops:
No problem

---

### Post by luvshines on 2010-11-01
> **ubunterooster said:**
> ```
ubunterooster@mountaindew:~$ smbclient //192.168.122.1/Backup -Uubunterooster%**********
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.5.4]
smb: \> 
smb: \> 
```Good or not? Sorry but I had less than 4hr sleep last night and dealt with two security breakins and am fried

So the terminal is working fine, only nautilus is giving trouble :mad:
In nautilus, are you trying to use ip or name ?

---

### Post by ubunterooster on 2010-11-01
If I go to the vista PC and go to network>Mountaindew (my Ubuntu PC) and click on the share shown, it says it is a misspelled name. Funny thing was all I used was the mouse.

---

### Post by luvshines on 2010-11-01
> **Morbius1 said:**
> OOPS, Sorry for butting in luvshines :oops:

Absolutely no issues :D
I admire the way you handle/solve queries. You pop in and it is marked SOLVED in no time :)

---

### Post by Morbius1 on 2010-11-01
I never thought about using Nautilus to try to access a share on the same machine as a diagnostic technique before but I have been able to reproduce the following error message:
> "Unable to mount location
Failed to mount Windows share"     I did that when trying to access a guest share where I purposely set permissions to 0700.  Set it back to 777 and problem solved.

So please post the output of the following command:
```
ls -dl /media/Backup
```And tell us if Backup is by any chance a fat32 or ntfs partition.

---

### Post by ubunterooster on 2010-11-01
It's Fat32 :barfs:

```
ubunterooster@mountaindew:~$ ls -dl /media/Backup
drwx------ 11 ubunterooster ubunterooster 16384 1969-12-31 19:00 /media/Backup
ubunterooster@mountaindew:~$ 
```

---

### Post by ubunterooster on 2010-11-01
Got to go mow grass. Be back later

---

### Post by Morbius1 on 2010-11-01
2 ways to fix this:

The hard way - go into fstab and modify or maybe create a line to mount this partition with the correct permissions

The easy way:
Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to your share definition so that it looks like this:
> [Backup]
    comment = Shares
    path = /media/Backup
    read only = No
    guest ok = Yes
**[COLOR=Blue] force user = ubunterooster[/COLOR]**Save the smb.conf file and restart samba:
```
sudo service smbd restart
```

Anyway, that's what I would do.

---

### Post by ubunterooster on 2010-11-01
[B]That worked!

 **Morbius1 gained 2**70 Geek exp.
**Morbius1 ****leveled up**! 

 **luvshines**** gained 2**70 Geek exp.[/B][B]
 **luvshines****leveled up**! 
[/B]

---

