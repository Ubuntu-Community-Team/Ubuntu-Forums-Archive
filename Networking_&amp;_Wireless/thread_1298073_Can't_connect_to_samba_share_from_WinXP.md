---
title: "Can't connect to samba share from WinXP"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by bivab on 2009-10-22
I recently set up a samba server on my ubuntu machine for my local home network. I put in the default "homes" share. I can connect to it just fine from my mother's laptop, which is running Vista, by typing "\\192.168.1.103\homes" into the address bar of windows explorer. When I do the same thing on my WinXP laptop, however, it tells me that "Windows cannot find \\192.168.1.103\homes."

I'm pretty sure this is a problem with my WinXP box since it works fine on my mom's computer, but I have no idea what to do to solve it...any clues?

EDIT: I should mention that I've already tried disabling all firewalls on my Windows machine, and changing it to be part of the same workgroup as the samba server.

---

### Post by SteveDee on 2009-10-22
> **bivab said:**
> ....I'm pretty sure this is a problem with my WinXP box since it works fine on my mom's computer, but I have no idea what to do to solve it...any clues?

EDIT: I should mention that I've already tried disabling all firewalls on my Windows machine, and changing it to be part of the same workgroup as the samba server.

You don't say whether your XP/Vista machines communicate.

Have you tried to ping between machines?

One thing I found on XP was that using Simple File Sharing is the best approach (from Windows Explorer > Tools > Folder Options > View > "Use Simple File Sharing")

---

### Post by bivab on 2009-10-22
Thanks for the help. I've already enabled simple file sharing but I haven't tried to communicate between the XP and Vista machines. Pinging works fine, however, so at least I know my computer can sort of "see" the other machines. I'm also able to use cygwin to ssh into the other machine, and I can use ftp to access its ftp server as well. It seems the only problem is accessing the samba shares via windows explorer...

---

### Post by dmizer on 2009-10-23
Please post your current /etc/samba/smb.conf file.

---

### Post by bivab on 2009-10-23
Certainly, though as I mentioned I doubt it's a problem with samba since my mom's vista computer can see the shares just fine.

```

[global]
    workgroup = LITINTERP
    netbios name = "bivab-server"
    interfaces = 127.0.0.1, 192.168.1.103
    bind interfaces only = yes
    username map = /etc/samba/smbusers

[homes]
    comment = Home Directories
    guest ok = no
    read only = no

[d]
    comment = d
    path = /home/bivab/d
    writeable = yes
    browseable = yes
    valid users = bivab

```

And here's my smbusers file:
```

bivab@bivab-server:~$ cat /etc/samba/smbusers
# Unix_name = SMB_name1 SMB_name2 ...
root = administrator admin
nobody = guest pcguest smbguest
lily = lily
bivab = david alistair

```

---

### Post by dmizer on 2009-10-23
Does the username on your Windows machine have a space in it ... like "david alistair", or do you have two Windows users "david" and "alistair"?

---

### Post by bivab on 2009-10-23
The latter. I don't put space in my usernames, makes things too complicated. :)

---

### Post by dmizer on 2009-10-23
Is your XP box connected wirelessly, and if so are absolutely postitive that you're connected to your own wireless network?

---

### Post by bivab on 2009-10-23
Yes, and yes--I know this because I can access the wireless router, and I can ping the other two machines. (On windows command line typing "ping 192.168.1.103", where that's the local IP of the linux box for example, works just fine.)

(By the way, thanks for your help, and sorry for all the trouble)

---

### Post by dmizer on 2009-10-23
No problem. I just noticed something though. Your bind only interfaces line has only one IP address listed. Try adding your laptop's IP address, or your laptop's hostname to the bind only interfaces line. In this case, I'm not really sure why your mom's machine can even access the share.

---

### Post by musicmanmg on 2009-10-23
I've found this to be a common Windows/Linux config change that needs to be amended to allow SMB to talk.
 
On the XP machine:
 
Control Panel > Administrative Tools > Local Security Policy > Local Policies > Security Options:
 
Change the following 4 entries from "Not Defined" to "Disabled"
 
Microsoft network client: Digitally sign communications (always) - Disabled
Microsoft network client: Digitally sign communications (if client agrees) - Disabled
Microsoft network Server: Digitally sign communications (always) - Disabled
Microsoft network Server: Digitally sign communications (if client agrees) - Disabled
 
Then either restart the PC or run start > run > cmd > and type ```
gpupdate /force 
```
 
I had a similar issue getting a Mac Server to share to Windows and this did the trick. That was using SMB. I hope it works for you.

---

### Post by bivab on 2009-10-23
Thanks to both of you, I'll be sure to try those tips and let you know what happens next time I have the chance (currently no longer at home)

---

### Post by bivab on 2009-10-25
Alas, still no luck...Windows still tells me, "Windows cannot find '\\192.168.1.103\'. Check the spelling and try again, or try searching for the item by clicking the Start button and then clicking Search." Nothing shows up in "My Network Places."

I have the feeling that this isn't anything to do with Samba, but a problem with my WinXP install...:/

---

### Post by musicmanmg on 2009-10-26
Just further to my previous post, can you try the following:
Make sure you do this on the Microsoft Network Client section.
 
Microsoft network client: Digitally sign communications (always) - Disabled
Microsoft network client: Digitally sign communications (if server agrees) - Enabled
 
Reboot your XP and machine and try again. This may be required if you are using XP Home edition. Please see [http://support.microsoft.com/kb/887429](http://support.microsoft.com/kb/887429)
 
Cheers,
 
Martin.

---

