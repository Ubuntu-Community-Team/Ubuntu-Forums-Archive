---
title: "Identical network shares.  AFS??"
date: 2009-11-29
forum: Networking &amp; Wireless
---

### Post by drysdan on 2009-11-29
Hi,

I'm just about to do a clean dual-boot install on a computer, and there's one thing I need it to do.  I need it to be able to share my big external drive, and have the drive to appear to other devices on the network as if it was the same network share, from both OSes.  Was that clear??  

Basically, I need my Macbook and my XBMC box to be able to access the external drive, but I want them to basically not know or care which OS is booted.

Is there a way to share the drive, and make it appear the same from both OSes?  

I was thinking of using an AFS share, because then the Macbook could use it for Time Machine backups as well, but this isn't totally essential...  I can currently do this in XP with a program called ExtremeZ IP, but I don't know if I can do it from Ubuntu, or if I can make both shares appear identical.

Any ideas?

Thanks!

---

### Post by Lars Noodén on 2009-11-29
AFS is good, but enterprise level.  It may not be worth the overhead for one or two users.  It is more useful with lots of users which are in multiple locations, like separate buildings or cities.

You probably want to try Samba here.

---

### Post by drysdan on 2009-11-29
Ok, now I feel dumb.  I meant AFP, not AFS.  Whoops.

So with Samba, how do I make the other devices see the shared drive as the same, regardless of which OS is currently sharing it? 
Also, is AFP a viable option here, or no?

---

### Post by Lars Noodén on 2009-11-30
[netatalk](http://packages.ubuntu.com/karmic/netatalk) will let you serve files via AFP.  

[http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05](http://maketecheasier.com/ubuntu-intrepid-how-to-share-file-with-mac-os-x-via-netatalk/2008/11/05)

[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

[http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/](http://blog.damontimm.com/how-to-install-netatalk-afp-on-ubuntu-with-encrypted-authentication/)

As will Samba, but over SMB/CIFS instead, which is a teeny bit easier for Linux clients.  

With either one, put the data on a separate partition, one that is available to both systems.  If you are dual booting between OS X and Ubuntu, then HFS is one option.  I think that it may be possible to force OS X to read EXT2, but it may be easier to stick with HFS+.  For that you need the packages [hfsplus](http://packages.ubuntu.com/karmic/hfsplus), [hfsutils](http://packages.ubuntu.com/karmic/hfsutils) and maybe also hfsprogs.

When you go national or international, it will be time to remember AFS.  ;)

---

### Post by drysdan on 2009-12-02
Ok, so here's the update:

I managed to get the drive shared via SAMBA properly, so that other devices can use it regardless of whether I'm booted into Ubuntu or XP.  As far as I can tell, my Macbook doesn't know the difference.  I got my Xbox running XBMC to use it as well.  For the record, I had to upgrade XMBC to the latest build to get it to store the user/pwd information for the share.  I never could get it to work on a guest account in Ubuntu.  Oh well.

Also, I configured netatalk to share a specific subfolder of the external drive via AFP, so that the Macbook can use it for Time Machine Backups.  That took a little work, and I got conflicting advice.  I think because netatalk recently updated?  Not sure.  Anyway, the key was adding 'uams_dhx2.so' to  /etc/netatalk/afpd.conf as per the instructions at 

[http://geekfun.com/2009/10/18/fixing-upgrade-problems-with-netatalk-on-ubuntu-9-04-jaunty-jackelope/]("http://geekfun.com/2009/10/18/fixing-upgrade-problems-with-netatalk-on-ubuntu-9-04-jaunty-jackelope/")

As of now, I can access the drive, and the Macbook can use it as a Time Machine backup, and it's all good.

Thanks!

---

