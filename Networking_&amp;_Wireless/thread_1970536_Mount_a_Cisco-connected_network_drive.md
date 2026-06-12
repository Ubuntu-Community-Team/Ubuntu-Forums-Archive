---
title: "Mount a Cisco-connected network drive"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by ricomoss on 2012-05-01
I have a very specific problem to solve.  I've read a few how-tos explaining how to mount a network drive and I can't seem to get it working.

I have a network drive connected directly into a Cisco router.  I need to mount this drive permanently.  That is, I need it to be available after each restart.

I started by creating a directory to mount the drive at.
```
mkdir /media/Yssecure
```

I then installed smbfs.
```
sudo apt-get install smbfs
```

Then I entered the following line into /etc/fstab.
```
//Yssecure /media/Yssecure smbfs username 0 0
```
Where "Yssecure" is the share name in the router admin settings.

Then tried to mount it.
```
sudo mount -a
```

I get the following error.
```
mount error: could not resolve address for Yssecure: Unknown error
```

I tried to change it to the IP address of the drive.  This is where I have run into some trouble - I can't seem to figure out what the IP address is.  This might be a Cisco specific problem.  I essentially just pointed it to the IP address of the router but it didn't work.

First I changed the fstab entry.
```
//192.168.1.254 /media/Yssecure smbfs username 0 0
```

Then I tried to mount again and it's asking for a password.  I believe it's asking me for the admin password to the router - but I can't be sure about that.

Has anyone had this problem before?  Any suggestions to fix the problem?

---

### Post by bab1 on 2012-05-01
> I have a network drive connected directly into a Cisco router.
What model is this *network drive *?

If it is a network drive (NAS) it should have an IP address of its own and servers running (NFS and SNB/CIFS).   You as a client can use these servers to mount the remote share on you local file system (/media/Yssecure)

You need to set up the share.  It can be the entire disk if you like.  But you need to configure the share it before you can mount it.

---

### Post by ricomoss on 2012-05-01
> **bab1 said:**
> What model is this *network drive *?

If it is a network drive (NAS) it should have an IP address of its own and servers running (NFS and SNB/CIFS).   You as a client can use these servers to mount the remote share on you local file system (/media/Yssecure)

You need to set up the share.  It can be the entire disk if you like.  But you need to configure the share it before you can mount it.

The model is SAMSUNG HD204UI.

There is already a share setup through the router and we can easily see it available on the Windows boxes throughout the office.

I cannot find any information about it's IP address through the router or properties info on the Windows boxes.

Where do I go from here?

---

### Post by bab1 on 2012-05-01
> **ricomoss said:**
> The model is SAMSUNG HD204UI.
This appears to be a bare hard drive (no network intelligence at all).> 

There is already a share setup through the router and we can easily see it available on the Windows boxes throughout the office.

I cannot find any information about it's IP address through the router or properties info on the Windows boxes.

Where do I go from here?
The drive itself has no IP address.  it is probably mounted to the cisco Router and shared via that device.  What name (//SERVER/share) appears (is available) on the Windows hosts?

Have you tried mounting the share as //SERVER/share. Have you tried using Nautilus to mount the shares (ALT-l smb://Server.  The IP address should be the LAN side IP address of the cisco host.

From the Ubuntu host what do you get with this```
smbtree -d3
```

[COLOR="Blue"]**Edit: **[/COLOR]Just realized you are using [COLOR="RoyalBlue"]kubuntu[/COLOR].  Do you have Gigilo and gvfs-backends installed?

---

### Post by ricomoss on 2012-05-01
> **bab1 said:**
> This appears to be a bare hard drive (no network intelligence at all).
The drive itself has no IP address.  it is probably mounted to the cisco Router and shared via that device.  What name (//SERVER/share) appears (is available) on the Windows hosts?

Have you tried mounting the share as //SERVER/share. Have you tried using Nautilus to mount the shares (ALT-l smb://Server.  The IP address should be the LAN side IP address of the cisco host.

From the Ubuntu host what do you get with this```
smbtree -d3
```

Ok, I went into the Dolphin folder browsing interface (I assume that's what Nautilus is?).  I dug around on the Network icons and finally found it!

Clearly the computer can see the drive but now I need to mount it.  Is there information available here that I can use to mount the drive?

I can't see any obvious paths or anything.  Under properties it just shows the location as... ```
/(smb)
```

Thank you so much for the help, bab1!

---

### Post by bab1 on 2012-05-01
> **ricomoss said:**
> Ok, I went into the Dolphin folder browsing interface (I assume that's what Nautilus is?).  I dug around on the Network icons and finally found it!

Clearly the computer can see the drive but now I need to mount it.  Is there information available here that I can use to mount the drive?

I can't see any obvious paths or anything.  Under properties it just shows the location as... ```
/(smb)
```

Thank you so much for the help, bab1!

The SMB/CIFS resource is //SERVER/SHARE. Not a path.  In Dolphin, smb:// is the protocol; then add the //SERVER/SHARE (as smb://server/share or smb://IP_Address/share)

This WILL MOUNT the share at /home/your_login/.gvfs (or the Dolphin equivalent).  You can control where it mounts from the command line with ```
sudo mount -t cifs //SERVER/SHARE /your/mount
```  This will mount the share as owned by root.  If this works I can dig up the rest of the options so that it will mount with you as the owner.

---

### Post by ricomoss on 2012-05-01
> **bab1 said:**
> The SMB/CIFS resource is //SERVER/SHARE. Not a path.  In Dolphin smb:// is the protocol; then add the //SERVER/SHARE (as smb://server/share or smb://IP_Address/share)

This WILL MOUNT the share at /home/your_login/.gvfs (or the Dolphin equivalent).  You can control where it mounts from the command line with ```
sudo mount -t cifs //SERVER/SHARE /your/mount
```  This will mount the share as owned by root.  If this works I can dig up the rest of the options so that it will mount with you as the owner.

I apologize but you are going to have to be a little more verbose with me.  I'm not sure what you are talking about.

Are you saying that I need to literally have smb://server/share or that I need to find out what "//server/share" needs to be?

I hate to sound dumb but I actually have no idea what is going on right now.

---

### Post by ricomoss on 2012-05-01
OMGOMGOMG...I just got it to work!  Thank you so much!

So for posterity I'll put my exact steps so this might be useful for others.

Start by creating a directory where you want to mount the drive:
```
mkdir /path_to_where/you_want_to_mount/your_drive
```

Then install smbfs:
```
sudo apt-get install smbfs
```

Now determine "where" this network is located.  This was the difficult part (for me).  I was trying to find a hard drive connected directly to a Cisco router.  I was able to go into the admin panel of the router and find the disk information under the "Storage" tab.  Look for the "Display Name" for the "Shared Folder" of the device you are wanting to mount.  You should also notice an IP associated with the drive (this is what I was missing).

Now connect that information to create an entry for your fstab file.  Enter the following into the fstab with sudo permissions.
```
//ip_associated_with_the_drive/display_name_found_in_router_admin_panel /path_to_where/you_want_to_mount/your_drive smbfs your_username 0 0
```

Now mount it.
```
sudo mount -a
```

I was able to do a simple ls command to see everything I wanted.  :)
```
ls -l /path_to_where/you_want_to_mount/your_drive
```

Glorious day!

---

### Post by bab1 on 2012-05-01
> **ricomoss said:**
> OMGOMGOMG...I just got it to work!  Thank you so much!

So for posterity I'll put my exact steps so this might be useful for others.

I guess you found that //server/share is based on whatever you named the host and the share. :-) 

 For example I have a host (the server) named *rincon* and a share I named *public* so they would be located by smb://rincon/public.

[COLOR="Blue"]**Edit:**[/COLOR] I believe that you should be able to browse the shares available using Dolphin, just like in Windows.  Look for something like Places>>Network

---

