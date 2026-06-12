---
title: "What are the benefits to NFS over CIFS?"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by Roasted on 2011-05-14
I was asking around in some IRC channels earlier trying to develop some thoughts on how NFS is better than CIFS.

I set up a FreeNAS file server, and that's where all of my data now resides on a pair of raided drives. That way my main desktop, which is kind of a power hog gaming rig, can be powered off since I pretty much live on my laptop now. Hey, going green - right?

Anyway, I began to tinker with CIFS and NFS. Since some family members in the household use Windows, I definitely need CIFS. But I wanted to bounce back to NFS too and check it out. 

While I do think it's nice I don't have to worry about authentication to the NAS box when using NFS, it's still a little scary. Being that it's more of a trust method instead of actual authentication, truthfully all a user needs to get into your data is the path to your NFS share and a matching UID. I mean, am I wrong by saying this? Sure, it may seem like NFS is convenient, but this angle of it is a little scary. I just don't feel like that screams "secure."

On the flip side, you have CIFS, which uses a user authentication level. So I hit my little shortcut to my NAS and it asks me who I am. I log in and bam, I have connection. I can browse other folders on the share, etc. This is convenient because I do have a "public" share on here with a generic user. That way if friends come over and want to transfer something to me, I have them drop it in the public share and I later transfer it accordingly. Since there is a user level authentication, this to me seems a little more secure.

Speed wise I was a little concerned, as some users have said NFS is faster than CIFS. Well, they might be right. But I did a few bench tests here on my laptop, using the same exact share except one with CIFS one with NFS. I stayed in the exact same location and transferred the same 300mb file in each instance. 

NFS - 1.7mb/s
CIFS - 1.5/mb/s

Not exactly enough to warrant a huge argument over, so I leave that argument along the road to be forgotten about since it doesn't really have any bearing on this situation.

So, tell me. I like things about both NFS and CIFS. I just want to know why is it "not optimal" to use a full blown CIFS setup even if you're using 100% Linux systems.

---

### Post by Roasted on 2011-05-15
So I'm doing a little reading here and a little experimenting on my own. I set up an NFS and CIFS share. It's the same share on the NAS server, and on my desktop I had two windows connected to it. One through NFS, one through CIFS. I pushed a 700mb file over my 100mb network connection and timed the results.

CIFS - 1:13:67
NFS - 1:15:72

I can see NFS being handy because it mounts the share as a local folder, which is super nice to do some basic rsyncing since the destination is just a folder. That's something I'm fighting with now, is figuring out how I can rsync over CIFS. But I really don't see any bearing on this speed comparison. I've had NFS run faster, CIFS run faster, and both run identically in many of my trial runs. 

That said, for a secured file sharing environment, I'm trying to understand how NFS would fit the bill. Without any hardcore introduction of Kerberos, there seems to be nothing, really, with a basic NFS setup. Just the UID matching which isn't really a layer of authentication, it's just a layer of meshing things up to work.

Am I missing something, being naive, or just beginning to understand the pros/cons of both NFS and CIFS?

---

### Post by Morbius1 on 2011-05-15
I have little experience with NFS but one line in your post confuses me:
> I can see NFS being handy because it mounts the share as a local folder,  which is super nice to do some basic rsyncing since the destination is  just a folder. That's something I'm fighting with now, is figuring out  how I can rsync over CIFSRegardless of how the samba client accesses the remote samba share it mounts the share to a local directory. You just may not be aware of where it is.

If you go to Nautilus > Network ..... and access the remote share it will automatically mount to a directory in your home folder at:
> /home/your-user-name/.gvfs/share-name on server-nameBecause the Nautilus developers are a cruel and heartless lot they put the mount point in a hidden directory ( .gvfs ) and with spaces in the name :shock:

---

### Post by Roasted on 2011-05-15
If that's the case, then I should be able to rsync easily if the share is already mounted.

That said, let's pretend the CIFS share is mounted. How do I rsync to it? 

/home/jason/.gvfs/ then what? Just the name of the mounted share?

Also - what do I miss out on, attributes wise, by syncing over CIFS? My objective is just to have a backup on the NAS, as well as being able to access this backup in real time from my laptop with a very small hard drive. Is there any disadvantage here?

---

### Post by abadr on 2011-05-18
I have a similar setup at home. I have a backup server running ubuntu server and samba and I control it using webmin. I have a share called "backup" and on the client computers I mounted it from fstab as "/mnt/backup". Everybocy on the client computers can see and access the share.

I use rsync to bakcup one huge photos directory to the backup server. The exact command escapes me at the moment but I do remember that the command treated all the source and destination pathes as local path.

---

