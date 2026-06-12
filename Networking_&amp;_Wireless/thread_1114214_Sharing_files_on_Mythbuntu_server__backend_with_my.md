---
title: "Sharing files on Mythbuntu server / backend with my Ubuntu client / MythTV frontend"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by sjd1980uk on 2009-04-02
Hi,

This is my first post, although I've used these forums loads for some great advice.

I am trying to mount (using fstab) the video and music folders from a USB WD 'My Book' HD connected to an old desktop pc I am using as a Mythbuntu backend / server onto my laptop which I would like to use as a client and occasional MythTV frontend. 

I have a my desktop connected via ethernet to an Orange livebox wireless router (which has caused problems in the past.) which I then connect to with my laptop via a wireless link.

None of the advice for setting up samba shares (cifs,smbfs) seems to work. I am struggling to figure out where my set-up has gone wrong or whether it is not possible to mount via cifs the external hard drive which is already mounted on my desktop - if you follow me.

Before I installed MythBuntu and was running an ubuntu server / ubuntu client configuration this set-up worked well.

I am also struggling to mount external hard drive on my laptop via the desktop e.g. the following does _not_ work:

```
sudo mount -t cifs //stuart-desktop/videos /mnt/samba -o username=*******,password=*******,iocharset=utf8,file_mode=0777,dir_mode
```

Thanks

S

---

### Post by marlin9800 on 2009-04-02
Not sure how much help I can be but I recently went threw a similar setup and FINALLY got it working. I am using an old desktop with a 500Gb USB drive as a NAS and samba as the share. I couldn't properly mount the share on my Ubuntu box, but it mounted no problem on wife's MAC, Vista box, a LiveCD session of another distro running on the Ubuntu box, and a VM image of another distro on the same Ubuntu box! (I know right!?)

There were a lot of angles I came at this with so I can't give you a step by step, but I can start with something simple, doing a samba mount. I tried 5 different commands until I was able to use something that worked.
```
sudo smbmount //192.168.1.99/media /mnt/nas -o username=%username%
```

That is of course assuming the mount is working correctly on the server. *edit, the only reason I run that command when I startup is because I have my conky set to show space status and I needed a local mount point instead of a smb://media/%whatever%/

---

### Post by sjd1980uk on 2009-04-02
Thanks Marlin, guess you went through my frustration!

this just returns:
```

Password: 
retrying with upper case share name
mount error 6 = No such device or address
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

---

### Post by marlin9800 on 2009-04-02
ok... so I assume the share isn't "sharing" properly (that part was my last step after I got everything else working). Can you browse to the share; Click Places; Network; (wait a min and see if it comes up there, if not click Windows Network [that is how it sees Samba shares]).

---

### Post by sjd1980uk on 2009-04-02
Yes, found it under Windows shares, can browse all of the sub folders I need and play videos etc...

---

### Post by sjd1980uk on 2009-04-02
Finally sorted it, needed to add the command ,nounix after the mount command as explained on this link. <http://public.ok2life.com/welcome/index/75> .

This fix also works with mounts in fstab.

Thanks

---

