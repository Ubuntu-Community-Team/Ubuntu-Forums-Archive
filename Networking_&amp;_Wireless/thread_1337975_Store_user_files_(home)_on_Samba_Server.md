---
title: "Store user files (home) on Samba Server"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by msimon1960 on 2009-11-25
Considering using Samba for home network with three desktops.

The Samba Server is a D-Link DNS-323 NAS sharing using SMB.  Can't change the configuration much there.

I'm uncomfortable with having my files and the kid's files on their desktops -- safety and they like to share stuff (music, video, etc.).

Can I configure their Jaunty desktops so that their /home directory is on the server?

The documentation I've found involves moving /home to local HD's.  I want to put it on the network server.

P.S. Samba apparently doesn't support symbolic links.

---

### Post by dmizer on 2009-11-26
Far more could go wrong under your proposed configuration than if you left all the home directories on machines with failing hard drives. Doubly so since you're restricted to samba.

I highly suggest that you consider simply making regular, automated backups of the home directory onto the NAS instead. Mount the NAS via CIFS and /etc/fstab as outlined in the 2nd link in my sig, and use something like grsync to configure the backup with a nice easy to use GUI interface.

---

### Post by msimon1960 on 2009-11-26
Dmizer,

As always, I'm indebted to your advice...

I'm using Conduit at the moment-- seems to work but glacially slow -- I'll take a look at grsync per your suggestion.

Pardon the Newbie question but what would you suggest as an alternative to SAMBA for home and small office users who want to keep most of their user stuff on a central server.  I had thought that SAMBA was the answer...now I'm not so sure.

Matthew.

---

### Post by memilanuk on 2009-11-26
There is nothing wrong with storing files from Windows on a Samba server... I think the reservations voiced above have more to do with trying to have your *entire* home directory/folder stored remotely.  Besides network speed, any hiccup in the network and/or the server can cause problems with the client.

Depending on what you want to accomplish, a few more workable solutions may include:

1) Create one big common 'share' or folder that you can put a folder for each computer or each person and store whatever files you want there.  It would be simple, but nothing to keep kid 'A' out of kid 'B's files - or yours.

2) Create individual user shares for each person, so that only they can log on and access their files.  This give each person a place to rat-hole whatever they want - and nobody else can get in and mess with their files (except you, being the system administrator, of course).

3) Combine 1 & 2 - have individual user shares, but also have a common share to use as a drop-box for file-sharing between computers and/or users.

4) If you want to do backups of the Users home directories on Windows, you can use various back up software on the clients to back up to the user's share on the NAS... some of the software might back up *all* users shares to the NAS, depending on how things are configured.

Just a few possibilities... but I'd second the notion that you probably don't want the hassles involved with directly mounting the users home directories over the network.

---

### Post by dmizer on 2009-11-26
Most people who have remotely mounted home directories are using the Linux native file system called [NFS](http://en.wikipedia.org/wiki/Network_File_System_(protocol)), but your NAS device can't handle NFS, so Samba is your only option. Because of that, it's probably best to run regular backups instead of trying to mount everything remotely over Samba.

That doesn't mean you can't still have a central file system, that just means that you shouldn't waste your network bandwidth on Samba mounted home directories. You can still have a central music and movies library for example.

---

### Post by msimon1960 on 2009-12-14
So far I've tried Conduit, LazyBackup, a bunch of GUI frontends for rsync and haven't found an acceptable backup solution.

I love Conduit (beautiful intuitive interface) but it doesn't work most of the time and is painfully slow.

I ended up creating 'Launchers' on the desktop for each of the shared folders.  A really clumsy solution but it's workable.

I'd still like to mount the /home folders on my NAS (Samba 3).  Any insight into why you think this is unworkable?

In my case security is of zero concern.

---

### Post by dmizer on 2009-12-15
Mounting the /home directories on the NAS causes so many concerns. First of all, if you have more than one computer active at the same time you will run in to bandwidth concerns unless you have a gigabit LAN and gigabit capable NAS (yours isn't). Your NAS hard drive read write counts will be at least double of a normal hard drive.

You're spending a whole lot of time trying to figure out how to do something that is extremely inadvisable. I suggest you spend that time and effort learning how to configure automated backups correctly. If the GUI frontends don't work well for you, just learn to do it from the CLI via cron.

Here's a good explanation of cron: [http://www.debianhelp.co.uk/schedulejobs.htm](http://www.debianhelp.co.uk/schedulejobs.htm)
You can use tar to perform a compressed/incremental backup to the NAS: [http://www.gnu.org/software/tar/manual/html_section/Incremental-Dumps.html](http://www.gnu.org/software/tar/manual/html_section/Incremental-Dumps.html)
More information on backups with tar: [http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

---

### Post by paxmark1 on 2009-12-27
in re ssh on DNS-323

ffp.log   snippet

* /ffp/start/sshd.sh ...
Starting /ffp/sbin/sshd
* /ffp/start/rsyncd.sh ...


see (google) DNS-323 wiki

sshfs
Ubuntu Hacks Jonathan Oxer 2006 pg. 326
Ubuntu Linux Toolbox 2008 pg. 248

the fun plug script is not to hideously difficult and  overlays many cli unix commands onto the DNS-323   

Just grsync over daily if need be to back up.

---

### Post by msw on 2009-12-28
I don't see much of a problem having 3-4 pc's on a network with /home folders stored on a remote server. With Samba in the role as a PDC, it supports roaming profiles for Windows and there are 1000's of network configurations like this and of which I have supported as a consultant to. The profile is stored on the Samba server and unless you store 100's of MB's of data in your profile, the speed concerns are negligible. Setting up user quotas will further reduce this potential issue. 

These same principles applies to Linx machines where a /home folder is stored on a remote server. As for concerns of bandwith, a 100 MB connection (which is now the most common for home and businesses) you will never, ever saturate this with 3-4 pc's on a home network.

---

