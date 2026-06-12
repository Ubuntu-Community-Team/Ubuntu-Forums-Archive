---
title: "Help setting up NFS for media server"
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by descendent87 on 2013-03-31
I'm trying to setup NFS for my home media server (running ubuntu server 12.10) but running into a few problems.
I want to share (with read and write access for any device between 192.168.0.3 - 192.168.0.10) my home folder and the contents of two drives (/media/disk1 and /media/disk2)
disk1 contains just TV shows
disk2 has sub-folders for TV, Films and Music

I would like the NFS shares to be like this:

/srv/home - My home folder (/home/ben)
/srv/media - All my media, seperated in sub-directories like this:

/srv/media/Films - All my films (/media/disk2/Films)
/srv/media/Music - All my music (/media/disk2/Music)
/srv/media/TV - All my TV shows (/media/disk1/ and /media/disk2/TV)

At the moment the contents of /etc/fstab is:
```

/home/ben                /srv/home              none    bind    0  0
/media/disk2/Films     /srv/media/Films     none    bind    0  0
/medis/disk2/Music     /srv/media/Music    none    bind    0  0

```

and /etc/exports:
```

/srv/home     192.168.0.3/10(rw,fsid=0,insecure,no_subtree_check,async)
/srv/media    192.168.0.3/10(rw,fsid=0,insecure,no_subtree_check,async)

```

When I mount them from my desktop (mac) I have the following problems:
/srv/home - Shows the contents of /srv/media
/srv/media - Shows the correct sub-directories (Films, TV, Music) but they are all empty

If I ssh into the server I can see that the contents of both folders look correct (/srv/home contains the contents of my home directory and the sub-directories in /srv/media/ have films, music etc in them).

I would also like to create symlinks in /srv/media/TV/ to everything in /media/disk1 and /media/disk2/TV so it appears that the two directories are one.
The contents of these folders isn't likely to change often as I have finished ripping all my DVD's.

I tried doing:
```
ln -sf /media/disk1/* /srv/media/TV/
ln -sf /media/disk2/TV/* /srv/media/TV/

```

and if I 'ls /srv/media/TV/' on my server it's all there, and if I look in to one of the sub-directories (eg 'ls /srv/media/30\ Rock/') there are sub-directories for each season but on my desktop when I mount the NFS and try to view the TV folder the top-level items (eg '30 Rock') are all there but if I try and view the contents of it I get 'The operation can’t be completed because the original item for “30 Rock” can’t be found.'

---

