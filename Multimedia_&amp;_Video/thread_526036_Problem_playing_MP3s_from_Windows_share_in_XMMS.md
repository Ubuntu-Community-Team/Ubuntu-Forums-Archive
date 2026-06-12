---
title: "Problem playing MP3s from Windows share in XMMS"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by wrybread on 2007-08-15
Having an odd problem with my new Ubunutu install: when I play an MP3 in XMMS or BMP from a Windows share, nothing happens, it doesn't recognize the MP3. Copy the same MP3 to my Ubuntu desktop and plays fine.

Totem plays fine both locally and over the network.

Any interesting trick to get XMMS working from a Windows share?

---

### Post by tgalati4 on 2007-08-15
I believe XMMS has problems reading network file shares in general.  From a SAMBA share, XMMS will not play an mp3 but mplayer will.  I haven't researched it so I'm not sure what the problem is.

If you go to network places in Nautilus and choose your SAMBA share and see mp3 files then right-click and "Open With" XMMS you will get the name of the file but no play.  "Open With" mplayer and it will work.  

I think it has something to do with how network shares are specified in Gnome Desktop.  mplayer can handle these server://file_directory pointers but XMMS has trouble with them.

Someone else needs to provide a more authorative answer--I only know the symptoms.

Edit:  The work-around is to locally mount the SAMBA share using either the command line or an appropriate entry in /etc/fstab.  Then you point XMMS to your local mount point and the network share shows up and plays reliably.

Here's an example of two types of SAMBA shares in an /etc/fstab entry:

/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda3       /media/ipod     hfsplus rw,force,user,noauto 0 0
//192.168.1.102/mnt/hd2/1 /mnt/dynebolic smbfs rw 0 0
sshfs#tgalati4@homeserver:/mnt/hdd5/Lsongs /home/tgalati4/Lsongs fuse rw,nosuid,
nodev,max_read=65536,user=tgalati4 0 0

---

### Post by DugieHowsa on 2007-08-16
I have found that smbfs is very buggy. You may have better luck with cifs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

