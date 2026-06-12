---
title: "Keep losing wireless"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by lelizondob on 2009-01-28
I have 2 months since I finally made Ubuntu my primary OS, everything
works perfect. I'm using ndiswrapper to make wireless work and
everything works. But somehow, everyday, I lose my wireless internet
connection after some hours (sometimes minutes) of working, it looks
like I'm connected but I'm not, I kill X but it just won't restart, the
only choice is to restart the os.

This is not the only problem, after I lose wireless, I can't open any program at all, if I kill X, I can login but can't run any command, the only choice is to restart. Because of this, I can't tell you if I can ping to the router.

When it's restarting, Ubuntu just can't stop avahi-daemon, so I thought
that was causing the problem so I just stop loading it at boot, but the
problem remains.

Sometimes after I kill X, I get the following error:

[2815.287188] CIFS vfs: error 0xffffff90 on cifs_get_inode_info in lookup of /www

[B]The problem is that I have no idea on how to identify the source and
because of that, I don't know where or what to look for, so Google won't
be of any help.[/B]

I could really use some help here because this is annoying.

Thanks in advance

---

### Post by Sam Lars on 2009-01-29
If you try running a program in the terminal after the wireless goes, does it give any errors?

---

### Post by lelizondob on 2009-01-29
Thanks for the reply..

I can't run any program in terminal after I lose wireless, can't even open terminal, but when it's open and I loose wireless I get no errors at all, just can't run any command, if I type:

ifconfig or ping something, it just waits forever to execute and it does nothing

---

### Post by Sam Lars on 2009-01-29
Are you doing anything like mounting network shares?

---

### Post by lelizondob on 2009-01-29
Yes I do mount a directory automatically at boot, could that be the problem?

---

### Post by lelizondob on 2009-01-30
This is the network share that I mount, I do it with this line in /etc/fstab:


```
//server/public /media/public cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by Sam Lars on 2009-01-30
I have noticed before that my NFS shares can cause problems.  Sometimes if something happens to the network, Nautilus will stop responding, and I guess the system could, too.
I think it's worth a try to comment that out and see if the problem still occurs.

---

### Post by lelizondob on 2009-01-30
Unfortunately, that's something I can't do because I work a lot in that network share.

Is there any other way I could mount that share?

Thanks

---

### Post by Sam Lars on 2009-01-30
You wouldn't have to do it permanently, just to see if that's the problem.
I guess you could mount it through the Connect to Server on the menu, but I'd like to see if that's really what's causing the problems first.

---

### Post by lelizondob on 2009-01-30
I'll do it and let you know, since the error just happens and it's not like "if I do this I get the error", I guess I'll just have to wait..

---

### Post by sedawk on 2009-01-30
Run this in a terminal and check the output when wireless fails:
```

while sleep 10;do iwconfig wlan0;done

```
Check the "link quality".

You can think about making your mount user-mountable (user) but
not to automatically mount it when booting.
But that doesn't solve your problem. The symptom you get is
typical when an active network drive dies, e.g. when you
have a NFS network drive in your PATH so that every command
started will be searched for in the NFS drive which is not answering.
What helps is killing all processes that try to access the non-responsive
network drive, so killing only the desktop might not really help.

---

### Post by lelizondob on 2009-02-01
I tried to run

```
while sleep 10;do iwconfig wlan0;done
```

after I lose wireless a few minutes ago, but I just didn't get anything, this is a normal behavior when I lose wireless as I said in the original post, I can't run any command at all.

The interesting thing about it, is that when I tried to unmount the network share, nautilus just crashed. Intermediately, (ouch!), and I couldn't unmount the network share after all. I tried to do this to see if I could get the system back to work.

Unfortunately, I do a lot of work on the network share, and I need to mount it (some programs can't open or save on smb:///something)..

I've been mounting my network shares following [http://ubuntuforums.org/showthread.php?t=1053705](http://ubuntuforums.org/showthread.php?t=1053705).. do you guys have any other suggestion to mount a network share? this is how I do it:

```

//server/public /media/public cifs credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

Thanks

---

### Post by lelizondob on 2009-03-06
I'm really tired of this. I have an ubuntu server and it works great. I love Ubuntu, but I can't interrupt what I'm doing just to restart, I even restart more with Ubuntu that I do with Vista, Vista just could stay on for days.

When I looose wireless, if I try to run any command it just crashes, only 'ls' works. This is not something about a network share, yesterday I lost wireless and my server was turned off so no mount was available.

This is really annoying. Should I just dump Ubuntu and go back to Vista? Can anyone help me please, I have no idea where to start. Mounting shares with nautilus it's not a solution, since hundreds of programs can't open/save files on something like smb://someserver/somefolder, I have to mount every share to be able to open/save files on /media/someserver/somefolder

Thanks in advance

---

