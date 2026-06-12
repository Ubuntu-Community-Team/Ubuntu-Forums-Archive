---
title: "Can't share media over network"
date: 2008-03-25
forum: Mythbuntu
---

### Post by jbrown96 on 2008-03-25
I just installed Mythbuntu 7.10 on an old Dell and am having a lot of trouble. I don't have my tuner card yet, so I'm just trying to be able to share music/movies from my laptop to the Mythbuntu box. I can't seem to figure out how to share them. I have enabled sharing on the laptop (Ubuntu 7.10) by right-clicking and choosing to share in Nautilus. I can even find the different computers on the network in Nautilus, but the shared folders aren't there. The same thing happens with the default shared folders with Mythbuntu. 

I could really use some help getting Mythbuntu to automatically (if possible) mount my movies/music from my laptop when it is connected to the network and having all my recordings available from Mythbuntu, too. 

Thanks for any help.

---

### Post by nasha on 2008-03-25
```
#  Make a directory for the mountpoint: mkdir /mnt/<name-of-mount-point>
# Mount the share: mount -t smbfs -o username=<username>,password=<password> //<win-box>/<share> /mnt/<name-of-mountpoint> Note: The syntax -username=<username>,password=<password> saves the password. 
```

This should be all thats needed to mount a windows share. Fill in the <...> with your details. If you would like it to automatically mount when you turn it on each time, you will need to edit /etc/fstab

---

### Post by johnnybirdman on 2008-03-26
Since you are sharing between two Ubuntu boxes you will use NFS shares.
I've used his thread [[COLOR="DarkOrange"]_**here **_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+share+network+fstab") to set up music and media shares between my 7.10 box and my 7.10 server. (currently I'm thinking about going with a FreeNAS server, but the share concept is the same)  I haven't set up my mythbuntu box yet, but when I do I'm going to have the same issues since all my media will be in another location.
The only other thing I'm seeing with a myth setup is that you can create the shares on/to the mythbox, but then I think you will have to symlink those shares to the place myth looks for the files.  I'm not sure you would directly want to link the share into the myth storage directory.  However, someone with a current setup might shed some light on that.
Hope that helps.
J.

---

