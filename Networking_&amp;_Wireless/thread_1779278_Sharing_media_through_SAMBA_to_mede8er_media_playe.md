---
title: "Sharing media through SAMBA to mede8er media player"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by Slav3 on 2011-06-10
Hi all

First off let me say that I am far from proficient in UNIX/LINUX/Ubuntu  having last used anything similar 10 years ago.  Why I say this is that  if I could get this working then pretty much anyone else could.  Also, a  large number of mede8er users appear to be less proficient in Ubuntu  and I hope that I can save them some of the frustrations I had to go  through.  First off I'd like to thank dmizer for his [SAMBA tutorial ]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")and Stormbringer for his [SAMBA tutorial]("http://ubuntuforums.org/showthread.php?t=202605&highlight=HOWTO%3A+Setup+Samba+peer-to-peer+Windows"). Finally I'd like to thank Wormzy for his [how to mount NTFS partitions tutorial]("http://ubuntuforums.org/showthread.php?t=1604251").

_**Background**_

I recently purchased, at a steal, an HP ProLiant ML110 G6 server which I  decided to configure as a NAS for my media.  I thought it would be an  ideal time to foray into the Ubuntu environment.  I purchased 2 x 2TB  seagate drives as additional storage for my setup. I formatted these in  Windows 7 as NTFS drives and selected MBR.  I then installed the two  drives to my server.  I installed Ubuntu Desktop 10.10 (?), mounted the  drives via disk management and followed the instructions in dmizer's  tutorial which is simple and to the point.  Note that my mede8er and the  Ubuntu desktop are wired to a Linksys WAG200G ADSL router.  Windows PCs  are connected via wireless on the same router.

[U][B]The Problem
    
  [/B][/U]I was able to browse the workgroup on my mede8er (wired to  network) and see my shares on the Ubuntu server (wired to network) but  every time I selected a share it would prompt me for a login.  No matter  what I tried (guest, Ubuntu username etc. etc.) I constantly received a  login failed on the mede8er.  I spent the next couple of days trying to  figure out if I'd done anything wrong in terms of configuring SAMBA and  came across Stormbringer's tutorial.  After trying everything possible  regarding SAMBA setup I began to despair.  The really strange thing for  me was that the CDROM that I shared via SAMBA was easily accessible  (without a login prompt) from the mede8er and windows PCs (Windows 7 and  XP).  Trying to access my data shares from windows threw up a  permissions error.  I tried CHMOD (changing security permissions) on the  folder to which the drives were mounted (/media/data1 and /media/data2)  and although the command didn't throw up any error no changes to  permissions were effected.  The media folder is owned by root so I tried  CHOWN (changing ownership) of the media folder to my username and  although this worked I still could not change permissions on the data  folders.

[U][B]The Solution
    
  [/B][/U]Many hours of searching later I came across Wormzy's tutorial,  which to be honest was my last hope.  Guess what - it solved my  permissions error and I can now browse all my SAMBA shares from the  mede8er without having to enter a username or password.  It works  wonderfully and streaming, even of my HD home video (MTS files) goes off  without a hitch.  Having read through numerous forum posts there are a  number of issues that one can experience when trying to share via  SAMBA.  if however, you have NTFS formatted drives in your Ubuntu  machine I would recommend:

1) Mount them with sufficient permissions using Wormzy's turorial as a guide.
2) Use either of the SAMBA tutorials highlighted above.  I am sure that  they would have both worked if I had the right permissions set up in the  first place.  I did also note that the second SAMBA tutorial was  archived as being outdated.

_**Next steps**_

Now that the shares are working my next steps are:

1) Configure permissions appropriately as the shares are now open with  full control to everybody on my WEP encrypted network (apparently not  the most secure).
2) Configure RAID 1 to mirror the 2 drives.
3) Configure remote access through remote desktop or VNC so that I can  stash my server out of the way and still access it with ease.

If I run into problems with 1-3 I will be sure to post how I resolved  them in this thread.  For those of you who experienced the same issues  as I did, this forum was an excellent source of information for a total  Ubuntu N00b.

---

### Post by Alasjo on 2011-06-10
Thanks for sharing! My own experience from setting up Samba tells that even though Samba (smbd) gives permission to read/write, the shared folders also need that permission from root. So sudo chmod 0777 is the way to go.

---

