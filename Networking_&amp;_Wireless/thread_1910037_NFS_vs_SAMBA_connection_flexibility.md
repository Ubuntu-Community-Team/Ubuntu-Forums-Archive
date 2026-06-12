---
title: "NFS vs SAMBA connection flexibility"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by MyD0j0 on 2012-01-16
Hi and thanks for the forums!

I recently replaced a FreeNAS (embedded) box with ubuntu server 11.10 because I wanted to add some additional capabilities that the embedded FreeNAS doesn't make easy to do and also so that updates are easier to manage.  I've built a raid 5 array on the server that I intend to use for storing movies, pictures and music that will be shared across the network using both ushare and forked-daapd.  I've also been reading up on some different network file systems to figure out which would be better to use in my specific network.

In my home network, I have several laptops: a MAC, 2 ubuntu 11.10 laptops and one windows Vista machine that will be getting converted to ubuntu in short order.  I recognize that with Windows in the environment, samba is preferred, but the Win Vista machine will be getting converted to Ubuntu 11.10 soon enough and doesn't really need access to the files before conversion.  After that conversion, I don't foresee any Windows machines connecting to the server.

Since these are laptops that will be coming and going from the network, I'm curious how flexible NFS is as opposed to SAMBA.  I've read that NFS can be faster in the network but is more geared toward permanent connections, does the newer NFS improve on this?

Anyway, the community's thoughts would be appreciated!

Thanks,

MyD0j0

---

### Post by SeijiSensei on 2012-01-16
I don't know if this is true of all media players, but I've found that mplayer and its derivatives like smplayer copy files shared by Samba to local storage before playing them.  Files exported by NFS play directly off the remote server.

In an environment where Windows support isn't necessary, I don't see any reason to use Samba over NFS.

---

### Post by MyD0j0 on 2012-01-17
Thanks, Sensei.

---

