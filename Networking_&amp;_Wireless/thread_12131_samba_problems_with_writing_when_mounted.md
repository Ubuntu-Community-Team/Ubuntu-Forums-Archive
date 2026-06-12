---
title: "samba problems with writing when mounted"
date: 2005-01-22
forum: Networking &amp; Wireless
---

### Post by ubuntu_demon on 2005-01-22
Hi,

I want to be able to have acces to my files from another ubuntu machine.

I followed the ubuntuguide on samba. I also did some reading at [www.samba.org](www.samba.org) before posting here.

I can read from my shares. I have problem with writing to my shares. But only when they are mounted.

nautilus smb://192.168.0.1/username
writing and reading works

when mounted writing doesn't work properly

for example when I do touch test the file is instantly created but I wait for some time (20 seconds or something) and I get this :

touch: setting times of `test': Input/output error

fstab :

//192.168.0.1/opslag	/mnt/p3-opslag	smbfs	credentials=/root/.smbcredentials,dmask=777,fmask=777	0	0

---

### Post by ubuntu_demon on 2005-01-22
In windows XP everything seems to work fine. I'll check some more.

correction :
there's also some strange stuff when doing :
nautilus smb://192.168.0.1/username

I can copy and create files and folders. but when I edit a file with gedit I can't type.

when I copy a bunch of files to it soms files don't arrive

here's my testparm results :

```

# Global parameters
[global]
        server string = %h (Samba, Ubuntu)
        obey pam restrictions = Yes
        passdb backend = tdbsam, guest
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        time server = Yes
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        username = /etc/samba/smbusers
        invalid users = root, bin, daemon, adm, sync, shutdown, halt, mail, news, uucp, operator
        hosts allow = 192.168.0.216
        delete readonly = Yes
        dos filetimes = Yes
        dos filetime resolution = Yes
        fake directory create times = Yes

[homes]
        comment = Home Directories
        valid users = username
        read only = No
        create mask = 0700
        directory mask = 0700
        browseable = No

[printers]
        comment = All Printers
        path = /tmp
        create mask = 0700
        printable = Yes
        browseable = No

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[opslag]
        comment = p3 : /mnt/opslag
        path = /mnt/opslag
        valid users = username
        force user = nobody
        force group = nogroup
        read only = No
        create mask = 0700
        directory mask = 0700


```

---

### Post by ubuntu_demon on 2005-01-27
How come when in windows everything works perfectly but when I mount my samba paritions in Ubuntu it doesn't work properly ?

---

### Post by albersag on 2005-01-27
Editing documents opened by other users, nees to configure oplocks or veto files.

What's the problem exactly?. I can not understand with the previous posts whats happening

---

### Post by ubuntu_demon on 2005-01-28
[QUOTE=albersag]Editing documents opened by other users, nees to configure oplocks or veto files.

What's the problem exactly?. I can not understand with the previous posts whats happening[/QUOTE]
 I've got 2 computers. The samba server is the one running ubuntu. The other one is a dual boot machine with windows XP and ubuntu (warty).

So -> only 1 client pc with 1 user.

In Ubuntu my mounted harddisk doesn't respond to a lot of things I want. In windows the same but less often.

I'm trying to find some sort of system / logic in those time outs (when I for example want to remove something)but I can't.

So it's functioning more or less but doesn't respond very well.

I don't have a clue what's happening.

---

### Post by ubuntu_demon on 2005-01-29
[global]
oplocks=no

doesn't help

---

### Post by kdavison007 on 2005-02-06
I have the same problem you do.  I have a Fedora 3 server with samba running and an XP system and my Ubuntu laptop.  XP works great with read/write.  When I'm in Ubuntu only if I mount the share does everything get owned by root and then I can't write to it.  This happens even when I put the user switches in the mount command so it shouldn't come up as root owned.  I've also tried an smbcreditials file with a username and password in it.  No dice.  Did you ever find a fix?

---

### Post by ubuntu_demon on 2005-02-12
[QUOTE=kdavison007]I have the same problem you do.  I have a Fedora 3 server with samba running and an XP system and my Ubuntu laptop.  XP works great with read/write.  When I'm in Ubuntu only if I mount the share does everything get owned by root and then I can't write to it.  This happens even when I put the user switches in the mount command so it shouldn't come up as root owned.  I've also tried an smbcreditials file with a username and password in it.  No dice.  Did you ever find a fix?[/QUOTE]
 no I didn't :(

---

### Post by ubuntu_demon on 2005-03-09
anyone ?

---

### Post by ubuntu_demon on 2005-03-10
after I upgraded my client pc to hoary the problems seem to have dissappeared.

---

