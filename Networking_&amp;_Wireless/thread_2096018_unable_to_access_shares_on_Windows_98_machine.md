---
title: "unable to access shares on Windows 98 machine"
date: 2012-12-18
forum: Networking &amp; Wireless
---

### Post by abcd123xyz on 2012-12-18
I have installed Ubuntu 12.04.1 LTS on a new laptop.  Everything seems great, except...

I have this old Windows 98 machine that I treat as a server (no remarks, please).  I've had it for a long time.  When I access the shares from the Ubuntu 12.0.4 machine, a lot of files and directories that I know are there do not show up.  

I've tried just browsing to the shares in nautilus, places -> networks -> Windows Network, pick the machine, pick the share.

I've also used the following command line to mount the share:
```

sudo mount -t cifs //192.168.0.14/D /mnt/server_d -o user=john,servern=SERVER,sec=lanman

```Same results either way.

After six months of searching for answers on the internet, I found two clues.  If I connect to the share using "smbclient \\server\d", then type "dir", some of the files listed are missing the first letter of the name.  Also, I found a bug listed on launchpad: "2.6.31 - Can't see files in CIFS-mounted directories", which describes a similar problem.  From that I learned that if I use the "noserverino" option to mount, I can see all the files.  I also have to use dir_mode and file_mode to get the modes right, though.

Finally, I dragged out an older laptop that has Ubuntu 10.04.4 LTS on it.  It works just fine.  Nautilus finds the share, allows me to edit files, everything.

Also, I fired up my old Windows XP machine.  I don't see any problems with accessing a share on that, so it seems like the problem is between Ubuntu 12.04.1 and Windows 98.

Samba on the 12.04 machine is version 3.6.3.  Samba on the 10.04 machine is version 3.4.7.

Any ideas?  Is this the right place to seek help, or is this a samba problem and I need to go over there?  Is there some way to tell samba "when you talk to the windows 98 machine, he's old and cranky, so you have to talk like this for him to understand"?

thanks in advance,
John

---

