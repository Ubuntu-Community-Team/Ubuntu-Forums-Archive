---
title: "File sharing between two jaunty computers"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by sprunkie on 2009-10-14
Hello, I am having a problem when trying to file share between my two computers.  Both with jaunty,  but all of my files are on my desktop with in a second drive.  I can share between my laptop and the main hard drive of my desktop but the storage drive on my desktop won't allow my to make it shareable.  I have been looking but can find anything that works.  Any ideas will help I'am pretty much a noob on jaunty.  But lov'in it so far.

Thanks for any help.

---

### Post by Iowan on 2009-10-14
Might be a permissions thing... How do you have the drive mounted (fstab-wise...)

---

### Post by sprunkie on 2009-10-14
No, I don't think I have the drive mounted. 
I mean that I have to go to places and click on the drive and then its mounted?  Right?
But if not how would one go about mounting the drive so that it always on at startup?

Sorry, like I said pretty new.

---

### Post by sprunkie on 2009-10-15
So on my desktop I go and click on places
then clink on the hard drive 
then the folder that I want to share with LAN
Right click then sharing options
Share this folder,  allow other people to write in this folder, and guest access.
 So then my Share names is highlighted and it states - 
'net usershare' return error 255: net user add:
cannot share path (media/hd/music) as we are restrcted to only sharing directories we own

Ask the administrator to add the line "usershare owner only = false"
to [global] section of smb.config to allow this

I under stand what to do but not where in the [Global] part of the smb.conf to add 
usershare owner only = false 
just anywhere in the [global] text area?

---

### Post by sirtrent on 2009-10-15
First thing I'd say is that you drive isn't being automatically mounted on startup. Personally I'd recommend you have the drive you want to share automatically mounted on each reboot. Second is to make sure the drive has the permission you want, probably something that lets lots of people do whatever they want.

The best way to do this is using fstab do something like the following:

```
sudo gedit /etc/fstab
```

and then add a line like this:

```
/dev/sdxx    /media/extradrive   ext3    defaults   0  0
```

where /dev/sdxx is your hard drive you want automatically mounted on startup /media/extradrive is a folder where you want your drive mounted (make sure it exists), ext3 is the filesystem (change to what filesystem you use), defaults is the options (Here you may be able change this to have different default permissions on the drive), and 0 0 should be left.

Once you have it automatically mounting you can either change the ownership of /yourdrive/music or you can edit smb.conf like it suggests in /etc/samba/smb.conf

EDIT: As for where to put that line in smb.conf, it doesn't matter as long it's after [global] and before the next [anything]

---

