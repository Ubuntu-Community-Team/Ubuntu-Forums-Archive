---
title: "Cannot connect to xp share"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by l07 on 2011-08-03
I created a root drive share and set it so only my user can access it (in xp). But ubuntu says "Failed to mount Windows share."

---

### Post by galtech on 2011-08-03
Hi l07, 

Would it be possible for you to please provide some more information with regard to the steps you are taking to access your XP share?

Thanks,
galtech

---

### Post by l07 on 2011-08-03
I go to network, click workgroup, my pc name, share name.
There aren't particularly any steps to take. I can describe my config: on xp I have comodo firewall, and it's set to enable lan traffic as far as I can tell. I tried sharing ubuntu's folder, installed service as prompted, and windows sees it but says "untupc not accessible. You mightn't have perms to use this net resource. The net path wasn't found." I used network magic before, but it wouldn't let me set access permissions, so I'm trying to do this manually.

After I restarted session as prompted after share service installation, I now get the msg "failed to retrieve share list from server." after clicking on win net.

---

### Post by l07 on 2011-08-03
Still need help.

---

### Post by galtech on 2011-08-07
Hi, sorry for the delay. I was just checking how my own Ubuntu / Windows machines were configured. 

From your Ubuntu PC have you tried going to Network > Windows Network and selecting the name of the workgroup?

---

### Post by l07 on 2011-08-07
Of course. That's how I access it.

---

### Post by Morbius1 on 2011-08-07
A lot of what I'm asking for is probably overkill but rather that ask you in steps it's best to ask this all at once. Please post the output of each of the following commands from your Ubuntu machine:
```
testparm -s
hostname
smbtree
```In the meantime instead of browsing to WinXP try accessing it directly by ip address:
```
nautilus smb://192.168.0.100
```[COLOR=Blue]*Changing 192.168.0.100 to the ip address of the WinXP machine.*[/COLOR]

Try it once as is and then try it after temporarily disabling the firewall on both WinXP and Ubuntu. If you haven't done anything to the Ubuntu firewall you don't have to do anything on Ubuntu but you will on WinXP.

---

### Post by galtech on 2011-08-07
Can you ping the Windows PC from the Ubuntu PC and vice versa?

---

### Post by JRV on 2011-08-07
Try this:

Open a terminal and enter:
```
nautilus smb://WINDOWS_HOSTNAME/SHARENAME
```

In linux you can do almost everything from the command line.
Most Graphic programs are just front ends to command line programs.
When you run a program from the command line you see error messages that might be surpressed by the graphic user interface.

---

### Post by Morbius1 on 2011-08-07
> I tried sharing ubuntu's folder, installed service as prompted, and windows sees it but says "untupc not accessible. Missed that from your earlier post. Sorry, but I need the output of this command as well:
```
net usershare info --long
```

---

### Post by l07 on 2011-08-10
I'm away from my setup, I will reply as soon as I'm back and able to post the output.

---

### Post by l07 on 2011-08-12
```
testparm -s
--
[global]
    server string = %h server (Samba, Ubuntu)
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

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

hostname
--
n-pc

smbtree
--
[no output]

net usershare info --long
--
[ut1]
path=/media/files/ut1
comment=
usershare_acl=Everyone:F,
guest_ok=n
```Pinging works both ways. Launching nautilus from cmd prompt yields the same result as browsing to the share.

---

### Post by Morbius1 on 2011-08-13
And what is the output of this command:
```
ls -al /media/files
```

---

### Post by l07 on 2011-08-16
I'd rather not post the output because it contains the names of sensitive files. It looks like a regular dir listing. Are there no other suggestions?

---

### Post by l07 on 2011-08-21
Still need help.

```
Enter help out mode.
```

---

