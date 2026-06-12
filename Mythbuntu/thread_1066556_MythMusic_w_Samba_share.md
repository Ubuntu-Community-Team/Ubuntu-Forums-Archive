---
title: "MythMusic w/ Samba share"
date: 2009-02-11
forum: Mythbuntu
---

### Post by lofttroy on 2009-02-11
So I've been attacking this for a couple of days and can't seem to find the right solution.  I've googled until my eyes bleed.

I've got a Samba share on the Myth BackEnd.  //192.168.33.73/mythmusic

I can see this will my FrontEnd in dolphin exactly where it should be.  I can see this on my Windows machines as well.

On the front end I've included the Samba share in the fstab
/192.168.33.73/mythmusic /var/lib/mythtv/music 	cifs rw,user=xxx,password=xxx 0 0

When I attempt to rip a CD into the directory it only creates the Artist directory with file permissions 755 even though I've got a directory mode =0777 in the smb.conf.  This prevents creating the album directory and stops MythMusic in it's tracks.

The directory is created in the correct location (on the back end).

How do I make it create a directory with the correct permissions.

Please reply using small words and ideas I'm pretty new to this, but becoming better through frustrations.

Thanks for your help,

Troy

---

### Post by jayman8547 on 2009-02-11
don't know if this will help you or not but you can try:

chmod 2775 -R /folder

I don't quite understand the 2 in 2775 but it works and the -R means recursive (gives all files under the top folder the same permissions)

---

### Post by lofttroy on 2009-02-11
I don't want to change the existing files.  It's when Mythmusic is creating the files that the problem occurs.

---

### Post by nickrout on 2009-02-11
> **lofttroy said:**
> So I've been attacking this for a couple of days and can't seem to find the right solution.  I've googled until my eyes bleed.

I've got a Samba share on the Myth BackEnd.  //192.168.33.73/mythmusic

I can see this will my FrontEnd in dolphin exactly where it should be.  I can see this on my Windows machines as well.

On the front end I've included the Samba share in the fstab
/192.168.33.73/mythmusic /var/lib/mythtv/music 	cifs rw,user=xxx,password=xxx 0 0 

for a start don't do this, /etc/fstab is world readable so your password is revealed. use credentials=/root/cifscredentials and make /root/cifscredentials readable by root only.

>  

When I attempt to rip a CD into the directory it only creates the Artist directory with file permissions 755 even though I've got a directory mode =0777 in the smb.conf.  This prevents creating the album directory and stops MythMusic in it's tracks.


try also in smb.conf

force directory mode = 0777

> 
The directory is created in the correct location (on the back end).

How do I make it create a directory with the correct permissions.

Please reply using small words and ideas I'm pretty new to this, but becoming better through frustrations.

Thanks for your help,

Troy

---

### Post by bau on 2009-03-25
I did the same on my master-backend (MBE). But I solved it in a different way: I read that the directory for all mythtv machines must be the same, preferrably /var/lib/mythtv/music. In order to follow this, I made a symlink on the MBE from my music-directory (also sambashare) to /var/lib/mythtv/music. On the frontend I use the autofs package to automount the sambashare from the MBE to excatly the same /var/lib/mythtv/music (this time on the frontend).
You will circumwent all problems later with mythweb as well.

---

