---
title: "samba mount in fstab not working automatically"
date: 2005-12-13
forum: Networking &amp; Wireless
---

### Post by aldar on 2005-12-13
I added the following to my /etc/fstab file and it isn't working, but after I'm logged in and i run "sudo mount -a" it works fine. Should I be putting the samba mount somewhere else??
On the XP computer, there is no PW. and liek I said, the mount -a works after im in ubuntu, but only when i type it manually.

//test/80gb /storage        smbfs   uid=test,gid=test,password= 0 0

---

### Post by amohanty on 2005-12-14
I think you need to add auto to mount it at boot (provided you dont use defaults):

> //test/80gb /storage smbfs auto,uid=test,gid=test,password= 0 0

HTH

---

### Post by aldar on 2005-12-14
Nope, that didn't do it. :(

---

### Post by amohanty on 2005-12-14
Ok try the following,

if that doesnt work:
add user to the list of directives:
>  //test/80gb /storage smbfs auto,user,uid=test,gid=test,password= 0 0

and again with usernam and password directives

Finally if that doesnt work either try replacing smbfs with cifs
also after you boot up take a look at the output of 
```
dmesg
```
and see if youc a spot the failure.

HTH

---

### Post by aldar on 2005-12-14
Well, searching a bit more on the web led me to try putting a username= line in the fstab file and that worked.
So I added a new user to windows just for this. Then I adjusted the line in fstab to look like this:
 //test/80gb /storage smbfs auto,uid=test,gid=test,username=share,password= 0 0

I'm still not sure why it DID work after I booted and did "mount -a" manually, but would NOT work automatically. But oh well, it's working now. :)

---

### Post by skirkpatrick on 2006-02-05
Okay, this is starting to tick me off.  I've got the same problem where Samba shares in /etc/fstab won't mount on bootup but will just fine using "sudo mount -a".  I have seen during startup a complaint about "no route to host".  This problem exists using either static IP or DHCP.  It does seem that the network isn't up yet when mountnfs.sh is run in init.d.  So I created another link in rc2.d called "S99MountNetwork" that pointed to mountnfs.sh in the hopes that by that time, the network was up and operational.  Evidently not as the Ubuntu startup music plays at the brown screen but it takes around 5 minutes before you see all the Gnome stuff loading and you get a desktop.  The shares are mounted then but it's a 5 minute boot process.

I don't remember having this problem in Hoary, has anybody come up with a solution to this (I've searched the forums already and nothing seems to work)?

---

### Post by anchor on 2006-02-10
I've been having the exact same problem as you.  I have noticed however that it only began occuring after upgrading to the 686-smp kernel, following this guide:

[http://ubuntuforums.org/showthread.php?t=85917&highlight=upgrade+kernel](http://ubuntuforums.org/showthread.php?t=85917&highlight=upgrade+kernel)

It does not occur with the stock kernel that ships with the install disc.  Doing "sudo mount -a" work just fine, but it refuses to mount automatically at startup.  I'm currently looking for a fix, but i've yet to run into a solution.

---

### Post by skirkpatrick on 2006-02-10
I'm running the K7 kernel.

---

### Post by can2002 on 2007-04-17
I came across this thread after encountering the same problem.  In my case I was connected to an authenticated share, but it didn't seem to matter what combination of options (e.g. user, auto, uid, etc.) I placed in fstab, the share refused to mount at boot.

In case it's of use to anyone else, I tried placing the following in my /etc/rc.local file before the last line:

sleep 30
/bin/mount -a -t smbfs

I originally tried it just to see if it might be something to do with boot order; however as it works I'll leave it in place for now!

Cheers,
Chris

---

### Post by mountainman101 on 2007-04-22
I  had smbfs working under edgy,  when I upgraded to fiesty, it stopped working.  Dont know what happened to it, but it wont mount.  I tried apt-get install smbfs and it says its installed, but man smbfs doesnt come back with anything.  Anyone else have this problem after the upgrade?

---

### Post by varangian on 2007-04-22
I hit some problems on Feisty as well. I decided to do a clean install so I set everything up from scratch. A simple smbfs link to a shared folder on an XP box that worked fine in Edgy.

The manual mount worked ok but on reboot I got whinges from Gnome about a defunct panel - presumably a reference to the icon that appeared on the desktop even though the share hadn't been mounted. Worse it appeared to be slugging the system as folder browsing ground to halt from time to time. The intended mount point was busy so manual mounting/unmounting would fail and the quickest way to recover was to comment out the line in fstab and reboot.

The fix I made was that in the new setup I had decided to make the mountpoint as /mydir. When I changed this to /media/mydir some of the problems disappeared. It still won't reliably automount but it just silently fails without apparently having any knock effects.

---

### Post by GnuSense on 2007-05-05
I've had this problem on a couple of Kubuntu systems, one an upgrade (from Hoary Hedgehog originally) and another a fresh install.  So I don't think it is peculiar just to upgrades.   Curiously, a third fresh install worked fine mounting FSTAB shares, even though the user had to enable his WPA wireless internet connection by activating his password wallet after he was booted in to Gnome.  The first two systems are Athlons, the third is an Intel Core Duo, if that makes any difference (maybe to the installed kernel?)

I also tried inserting links to a script mounting the samba shares in various /etc/rc#.d directories, that didn't work.  For one system that a newbie will be using I had to make a script for him using visudo that was automatically run by Gnome & KDE when they start. Lots of screwing around with SUID, etc., I forget exactly what I did, but it seems to work.   I see logs from his machine on my server's /var/log/samba, so I guess its working for him.

I'll give can2002/Chris' solution a spin.  It doesn't seem ideal since it will slow down the boot process.  I hope I come across a better alternative or some update cures this weirdness.

EDIT: Chris' solution worked well and it didn't even take notably longer to boot up.  Thanks.

---

### Post by tom-ubuntu on 2007-05-09
Having now exactly the same problem as you guys. Chris' solution unfortunately did not work for me; after the reboot, mounting does not work :(

Here is my fstab entry:

//192.168.x.x/video    /video   smbfs auto,user,uid=tom,gid=tom,password= 0 0

I like to connect to a Buffalo Linkstation.

Any help appreciated.

Regards,
Tom

---

### Post by taj on 2007-09-12
try cifs instead of smbfs

See if that works

---

### Post by Helmi on 2007-09-13
cifs does not change anything to the automount behaviour - should it?

Same problem here and still the same with gutsy now.

Trying the solution from page 1 and let's see....

---

### Post by GnuSense on 2007-09-30
I haven't tried cifs yet on Feisty to see if it works to automatically mount shares, but after some upgrades  I noticed that my old smbfs FSTAB language no longer properly mounted my Debian SAMBA shares on my Edgy Xubuntu install, they would be listed in my MTAB, but I couldn't access them.  So I changed to CIFS and it seems to work flawlessly.  The verbiage of mounting a CIFS share is a little different than SMBFS.  See [here]("http://joey.ubuntu-rocks.org/blog/2007/04/25/resolution-to-mounting-samba-shares-dont-use-smbfs/"). 

Anywho, here is how my CIFS FSTAB stanza looks now:
>  //server/share      /mnt/share  cifs   credentials=/root/.smbcredentials,user,uid=*myserver_username*   0    0

---

### Post by awan on 2007-12-27
(Ubuntu Dapper 6.06 Server; Novice)

I started having  this same issue as well just out of the blue.  I could not automatically mount samba shares by placing entries in the /etc/fstab file; I would get an I/O error when trying to access the share.  Oddly enough, I also found that samba SERVER would run very sluggish or stop working all together as well.

I COULD, however, manually mount the shares either using "mount -a" or using the "mount" command for each individual share.  Here's my old /etc/fstab entry:

```
//server/share /media/my-share smbfs username=user,password=password 0 0
```

I was able to remedy the situation by swapping out "smbsf" with "cifs" in the /etc/fstab file.  My Win2k servers seem to be handing the alternate protocol just fine.  I also added the "auto" and "user" options but that appears to not have been the ultimate solution:

```
//server/share /media/my-share cifs auto,user,username=user,password=password 0 0
```

Early on I was very confused why my second server (supposed to be identical) was NOT having this issue.  I later discovered that they indeed has different kernel versions (2.6.15-26-server & 2.6.20-15-server) ; there's  a very good chance that they were running different versions of samba as well. Both are now have samba at 3.0.22-1ubuntu3.6.

Anyway...it's working great now.  Thanks for the assistance.

---

### Post by skarphace on 2008-05-20
In case anyone runs into this thread searching for a solution, I'll post what I just found out.

smbfs has been depreciated and replaced with cifs.  During an upgrade to one of my workstations, the system's rc scripts were updated to reflect this change.  fstab was not updated to reflect this change as I wasn't even aware of it.

After some hours of digging, I found that 'smbfs' was not listed on line 30 of /etc/rcS.d/S35mountall.sh, only cifs was.

```
                mount -a -t noproc,nfs,nfs4,smbfs,cifs,ncp,ncpfs,coda,ocfs2,gfs
```

So, moving fstab over to use cifs instead, did the job.  Potentially, you may also be able to add 'smbfs' to that line and have your old setup continue to work.

---

