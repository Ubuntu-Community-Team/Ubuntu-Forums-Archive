---
title: "Windows samba shares"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Hackit on 2009-12-02
HI everyone,

I know this is a windows issue, but maybe someone here has had this issue before.

I have changed my shares in ubuntu and windows 7 still shows the old shares, how do I make windows not display a share if it is no longer there?

I have already cleaned out /var/lib/samba/usershares.

Hope someone has an idea.

---

### Post by Hackit on 2009-12-02
Ok I know the info is stored in windows on what smb servers it has joined, and I know this is not the right place top ask for help.

Can someone recommend a good forum to fiond the answer, I find it to be hard to find a windows forum where they also have linux experience.

---

### Post by Hackit on 2009-12-04
I'm still looking, has no one had this issue with old samba shares show in windows?

---

### Post by doas777 on 2009-12-04
let me confirm, you remove a share from samba, but it still shows up on the windows client?

windows caches netbios names for ease of access, so once it's there, it's there, but you can clear it out, either by rebooting, or running 'nbtstat -R' 
```

PS C:\Windows\system32> nbtstat -R
    Successful purge and preload of the NBT Remote Cache Name Table.
PS C:\Windows\system32>

```

that should do ya.

---

### Post by Hackit on 2009-12-04
Thanks so much for the steps, bad part is This did not work.

I have restarted both computers and ran the command a couple times.

And yes you are right I created a share on my Linux box and now I can not remove this obsolete share from windows.

Thanks for the reply.

I'm now reading and trying to figure out windows smb client side caching, still feeling lost though. Might just leave it be as this has been an issue for about 6 months already.

---

### Post by capscrew on 2009-12-04
> **Hackit said:**
> Thanks so much for the steps, bad part is This did not work.

I have restarted both computers and ran the command a couple times.

NETBIOS has nothing to do with creating shares.  It is a mapping service between IP addresses and COMPUTER NAMES.  It is the MS nameserver convention.
> 
And yes you are right I created a share on my Linux box and now I can not remove this obsolete share from windows.

Thanks for the reply.

I'm now reading and trying to figure out windows smb client side caching, still feeling lost though. Might just leave it be as this has been an issue for about 6 months already.

The shares are cataloged by the *browse master* and this is by election of the running Samba servers (yes your Windows hosts are servers as well as clients).  The strange part is that this is updated every 15 minutes or so.  it is a dynamimc process.

Check to see if you have these *phantom * shares listed in the /etc/samba/smb.conf file.

---

### Post by Hackit on 2009-12-04
> **capscrew said:**
> 

Check to see if you have these *phantom * shares listed in the /etc/samba/smb.conf file.

Thanks, No the smb.conf is clean only showing my 3 shares.

Just thought of something else, about 4 months ago I reinstalled windows 7 and the phantom shares still showed up. So They must be in some config file on my Linux box.

Ok Maybe this will help, I first added my shares in terminal and have also used the properties page on the folders. The last share that is showing that no longer exists was added and removed from the properties of the folder and not sudo gedit /etc/samba/smb.conf.

But i have gone into the config and made sure to add all my shares.

This is more of a why than it is an issue, i hate when things are not the way they should be.

---

### Post by capscrew on 2009-12-05
> **Hackit said:**
> Thanks, No the smb.conf is clean only showing my 3 shares.

Just thought of something else, about 4 months ago I reinstalled windows 7 and the phantom shares still showed up. So They must be in some config file on my Linux box.

Ok Maybe this will help, I first added my shares in terminal and have also used the properties page on the folders. The last share that is showing that no longer exists was added and removed from the properties of the folder and not sudo gedit /etc/samba/smb.conf.

But i have gone into the config and made sure to add all my shares.

This is more of a why than it is an issue, i hate when things are not the way they should be.

Sometimes we are our own worst enemy.  Configuring shares sometimes using Nautilus (Gnome GIO) and/or manually at other times confuses the issue.  I do not have access to my Linux network (vacation) for the next 30 days,so all of this is by memory.  I do not remember any shares in my system at /var/lib/samba.  I'm not sure (by my memory) whether there is bookmarks of share locations there either.  You might see if you have any *"places"* marked for shares.  You can move (mv) all the files (or rename the root directory to see what happens.

My best guess is that this is a Nautilus issues not a direct Samba issue. 

You can also try the CLI for information.  Try this```
smbclient -L -u <yourLogin>
``` Or some such.  This is the CLI client and it works along the lines of raw FTP.

---

### Post by Hackit on 2009-12-06
> **capscrew said:**
> Sometimes we are our own worst enemy.  Configuring shares sometimes using Nautilus (Gnome GIO) and/or manually at other times confuses the issue.  I do not have access to my Linux network (vacation) for the next 30 days,so all of this is by memory.  I do not remember any shares in my system at /var/lib/samba.  I'm not sure (by my memory) whether there is bookmarks of share locations there either.  You might see if you have any *"places"* marked for shares.  You can move (mv) all the files (or rename the root directory to see what happens.

My best guess is that this is a Nautilus issues not a direct Samba issue. 

You can also try the CLI for information.  Try this```
smbclient -L -u <yourLogin>
``` Or some such.  This is the CLI client and it works along the lines of raw FTP.

Thanks so much Capscrew,

This is what I entered
smbclient -N -L server

output;
server@linux-server:~$ smbclient -N -L server
Anonymous login successful
Domain=[MINE] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (linux-server server (Samba, Ubuntu))
	[COLOR="Red"]Torrent Links   Disk      
	Torrent Downloads Disk      
	Kevs Folder     Disk[/COLOR]      
	torrent-links   Disk      
	torrent-downloads Disk      
	kevs-folder     Disk      
Anonymous login successful
Domain=[MINE] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	SERVER               linux-server server (Samba, Ubuntu)
	SIMPLE-NAS           Simple-Nas

	Workgroup            Master
	---------            -------
	MINE              SIMPLE-NAS

Now how do i make the first three (red) entries disappear?

---

### Post by capscrew on 2009-12-06
> **Hackit said:**
> Thanks so much Capscrew,

This is what I entered
smbclient -N -L server

output;
server@linux-server:~$ smbclient -N -L server
Anonymous login successful
Domain=[MINE] OS=[Unix] Server=[Samba 3.4.0]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (linux-server server (Samba, Ubuntu))
	[COLOR="Red"]Torrent Links   Disk      
	Torrent Downloads Disk      
	Kevs Folder     Disk[/COLOR]      
	torrent-links   Disk      
	torrent-downloads Disk      
	kevs-folder     Disk      
Anonymous login successful
Domain=[MINE] OS=[Unix] Server=[Samba 3.4.0]

	Server               Comment
	---------            -------
	SERVER               linux-server server (Samba, Ubuntu)
	SIMPLE-NAS           Simple-Nas

	Workgroup            Master
	---------            -------
	MINE              SIMPLE-NAS

Now how do i make the first three (red) entries disappear?

Interesting.  It persists when talking directly to the Samba daemon *(smbd)*.  Did you try the renaming of the /var/lib/samba directory?

Somewhere you still have data that the smbd parses upon start up.

---

### Post by Hackit on 2009-12-06
> **capscrew said:**
> Interesting.  It persists when talking directly to the Samba daemon *(smbd)*.  Did you try the renaming of the /var/lib/samba directory?

Somewhere you still have data that the smbd parses upon start up.

I have not, should I try renaming my samba directory?

---

### Post by bab1 on 2009-12-06
> **Hackit said:**
> I have not, should I try renaming my samba directory?

I think what capscrew is saying is to move the files temporarily. 

The idea is to to move the /var/lib/samba directory to something like /var/lib/samba.original.  This should stop the Samba daemon from using any data from there.

You can always revert back once this is done.

---

### Post by Hackit on 2009-12-06
> **Hackit said:**
> I have not, should I try renaming my samba directory?

Ok I moved samba to the desktop and all that happened was samba no longer worked.

I moved it back and restarted all services and it was the same.

The good news is the issue is gone.

I changed the name in smbconfig, I had no idea the name of the share, and the title had to be the same.

See below.

EX
[COLOR="Red"][Torrent Downloads][/COLOR]
    path = /media/disk/[COLOR="Red"]Torrent-Downloads[/COLOR]
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = kevin
    force group = kevin

so I changed to this

EX
[Torrent-Downloads]
    path = /media/disk/Torrent-Downloads
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = kevin
    force group = kevin

Issue is resolved, thanks to all who helped, best forum ever, everyone is so helpful.

---

