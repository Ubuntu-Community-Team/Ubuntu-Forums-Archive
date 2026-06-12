---
title: "Windows networking issue"
date: 2008-05-07
forum: Mythbuntu
---

### Post by CleverJake on 2008-05-07
I just set up mythbuntu, and im trying to set up as many of the features that I can.
My next stop is importing music files over a network, and ive hit a wall.

I already had my windows files accessible through my Ubuntu laptop

I pinged the local ip, to make sure that the windows could see mythbuntu, and vice versus. So far so good.

next, i set the mount point on myth, via sudo mkdir /mnt/audio
and the file is created

next, i try mounting the network file on the windows box
```
sudo mount -v -t smbfs -o username=*****,password=***** //Windoze/D/AA/Audio /mnt/Audio
```

and it replies as such

```
parsing options: rw, username=*****,password=******

mount.cifs kernal mount options unc=//Windoze\D,ip=192.168.1.107,ver=1,rw,username=*****,password=******,prefixpath=AA/Audio

```

so, as far as I can tell, it looks like it worked, but when i try to access the file, it says it doesn't exist, when i try to remount the file it says it DOES exist, and when i try to remove the file, it says cannot remove file is directory

any help as to what im doing wrong would be great

thanks

---

