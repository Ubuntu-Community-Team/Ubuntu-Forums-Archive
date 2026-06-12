---
title: "How to share a folder so Windows can see it ?"
date: 2009-12-25
forum: Networking &amp; Wireless
---

### Post by Mongao on 2009-12-25
Hi all,

Please, my Ubuntu "sees" shared folders on other computers running Windows, but how can I implement the vice-versa ?

I mean, how can I share folders in my Ubuntu PC so others Windows computers can access it ?

Of course I`ve gone through all the way, but I stopped in the point where Ubuntu asked me to edit a TXT file I believe, I am afraid of damaging my installation.

Thanks,
Mongao

---

### Post by Iowan on 2009-12-26
You will need to install the server component of Samba. I have a few good How-To's bookmarked at home, but I'm not there...

---

### Post by ELGL on 2009-12-26
Just copy the smb.conf to smb.conf.backup and then edit it. That way you can safely experiment. When samba doesn't start anymore you can simply copy smb.conf.backup to smb.conf and start over.

Just some quick tips to get you started,

Fist make sure that samba is installed, open a terminal and type this,

```

user@euser-desktop:~$ smbd -h

Invalid option -h: unknown option

Usage: smbd [-?DiFSbV] [-?|--help] [--usage] [-D|--daemon] [-i|--interactive] [-F|--foreground]
        [--no-process-group] [-S|--log-stdout] [-b|--build-options] [-p|--port=STRING]
        [-P|--profiling-level=PROFILE_LEVEL] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE] [-V|--version]
        [--sbindir=SBINDIR] [--bindir=BINDIR] [--swatdir=SWATDIR] [--lmhostsfile=LMHOSTSFILE]
        [--libdir=LIBDIR] [--modulesdir=MODULESDIR] [--shlibext=SHLIBEXT] [--lockdir=LOCKDIR]
        [--statedir=STATEDIR] [--cachedir=CACHEDIR] [--piddir=PIDDIR]
        [--smb-passwd-file=SMB_PASSWD_FILE] [--private-dir=PRIVATE_DIR]

```

When you see that invalid option and a lot of other text returned you're fine and samba is installed.

Otherwise, install samba first

```

sudo apt-get update
sudo apt-get install samba

```



Add this to the bottom your smb.conf to share a folder. Do mind to change the path to the path you want to share
```

[share]
path = /home/user/Public  # the full path to the folder you want to share
writeable = yes   # basic access control allowing everyone that authenticates to write
browsable = yes   # let's it show up when you browse the network in windows, making it a NOT hidden share
comment = Writeable share on desktop # just a comment 
```

Then in a terminal restart samba so it reloads it's configuration and activates the share.

```

sudo service samba restart

```

almost there.. now create a user in samba with smbpasswd
```

sudo smbpasswd -a user

```

replace user with your username and enter a password twice.

aaaand... you're done.

---

### Post by Morbius1 on 2009-12-26
**Open Nautilus > Right click a file you own ( like in your /home directory ) > Select "Sharing Options" > check all three boxes > Select "Create Share" **

It will then ask you if you want to modify the permissions - you do. 

It will create a share that allows guest access with Read / Write permissions. You can also set it to require authentication if that's what you want to do.

If you've done all that and Windows can't see it, that's another matter. If this is the problem you need to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type** testparm -s**

---

### Post by Mongao on 2009-12-28
> **Morbius1 said:**
> **Open Nautilus > Right click a file you own ( like in your /home directory ) > Select "Sharing Options" > check all three boxes > Select "Create Share" **

It will then ask you if you want to modify the permissions - you do. 

It will create a share that allows guest access with Read / Write permissions. You can also set it to require authentication if that's what you want to do.

If you've done all that and Windows can't see it, that's another matter. If this is the problem you need to post the output of the following commands:

Open **Terminal**
Type **net usershare info**
Type** testparm -s**

Thanks to everybody that replied, really appreciated.

I have tried this method and Ubuntu gave me this message back:

Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

Please, any tips ?

THANKS A LOT,

Mongao

---

### Post by dmizer on 2009-12-28
> **Mongao said:**
> Ask the administrator to add the line "usershare owner only = false" 
	to the [global] section of the smb.conf to allow this.

Since you are your administrator, do just what it says:
```
gksudo gedit /etc/samba/smb.conf
```
Look for the "[global]" line, and add
```
usershare owner only = false
```
directly below it.

Save the file, and reboot.

---

### Post by Mongao on 2009-12-28
THANK YOU ! Worked like a charm !

Mongao

---

### Post by escaleraroyal on 2009-12-29
> **ELGL said:**
> Just copy the smb.conf to smb.conf.backup and then edit it. That way you can safely experiment. When samba doesn't start anymore you can simply copy smb.conf.backup to smb.conf and start over.

Just some quick tips to get you started,

Fist make sure that samba is installed, open a terminal and type this,

```

user@euser-desktop:~$ smbd -h

Invalid option -h: unknown option

Usage: smbd [-?DiFSbV] [-?|--help] [--usage] [-D|--daemon] [-i|--interactive] [-F|--foreground]
        [--no-process-group] [-S|--log-stdout] [-b|--build-options] [-p|--port=STRING]
        [-P|--profiling-level=PROFILE_LEVEL] [-d|--debuglevel=DEBUGLEVEL]
        [-s|--configfile=CONFIGFILE] [-l|--log-basename=LOGFILEBASE] [-V|--version]
        [--sbindir=SBINDIR] [--bindir=BINDIR] [--swatdir=SWATDIR] [--lmhostsfile=LMHOSTSFILE]
        [--libdir=LIBDIR] [--modulesdir=MODULESDIR] [--shlibext=SHLIBEXT] [--lockdir=LOCKDIR]
        [--statedir=STATEDIR] [--cachedir=CACHEDIR] [--piddir=PIDDIR]
        [--smb-passwd-file=SMB_PASSWD_FILE] [--private-dir=PRIVATE_DIR]

```When you see that invalid option and a lot of other text returned you're fine and samba is installed.

Otherwise, install samba first

```

sudo apt-get update
sudo apt-get install samba

```

Add this to the bottom your smb.conf to share a folder. Do mind to change the path to the path you want to share
```

[share]
path = /home/user/Public  # the full path to the folder you want to share
writeable = yes   # basic access control allowing everyone that authenticates to write
browsable = yes   # let's it show up when you browse the network in windows, making it a NOT hidden share
comment = Writeable share on desktop # just a comment 
```Then in a terminal restart samba so it reloads it's configuration and activates the share.

```

sudo service samba restart

```almost there.. now create a user in samba with smbpasswd
```

sudo smbpasswd -a user

```replace user with your username and enter a password twice.

aaaand... you're done.

My guest is ubuntu and my host is win7. I did all this but I can't see my Ubuntu shared folder in windows.

---

### Post by dmizer on 2009-12-29
> **escaleraroyal said:**
> My guest is ubuntu and my host is win7. I did all this but I can't see my Ubuntu shared folder in windows.

Instead, use Morbius1's directions in post 4 here: [http://ubuntuforums.org/showpost.php?p=8561462&postcount=4](http://ubuntuforums.org/showpost.php?p=8561462&postcount=4)

---

### Post by Morbius1 on 2009-12-29
> **escaleraroyal said:**
> My guest is ubuntu and my host is win7. I did all this but I can't see my Ubuntu shared folder in windows.

I've been having a couple of bad days here recently so maybe this is the start of another one but I have to ask this question:

Do you mean guest as in client and host as in server? Or are you running Ubuntu as a guest in VirtaulBox or VMWare on top of Win7?

---

