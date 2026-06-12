---
title: "how to force nfs protocol version on client ?"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by Carrot Cruncher on 2011-01-09
hi. does anyone know how to force an nfs client to use a specific protocol version ? on fedora this can be done by setting the "Defaultvers" parameter in the /etc/nfsmount.conf file. cheers.

---

### Post by movieman on 2011-01-09
Isn't there a mount option to specify the protocol version to use?

'man nfs' implies that nfs mounts can be told to use V3 or V2, and nfs4 mounts will use V4.

---

### Post by Carrot Cruncher on 2011-01-10
hi. yeah, you can manually set the version for each mount, but i want to set all mounts to default to nfsv3. oh, this is on maverick (10.10) by the way. cheers.

---

### Post by PatchesTheCaveman on 2011-01-10
Add the mount option to the options area of your /etc/fstab file.

---

### Post by Carrot Cruncher on 2011-01-10
sorry, should have made myself more clear. i'm not using fstab entries which is why i'm after a general setting. i'm actually using autofs, but i'd like a generic setting if there is one.

---

### Post by PatchesTheCaveman on 2011-01-10
You should just add the mount option after the dash in your *auto.master* file.  e.g.
```
movies    -auto,nfsvers=v3    hal:/data/movies
```
For more information, see the autofs man page:  [http://www.autofs.org/autofs-autofs5.html](http://www.autofs.org/autofs-autofs5.html)

You can try creating your own /etc/nfsmount.conf file, but it looks like the NFS packages included with Ubuntu are configured to ignore that file.  You'd have to compile and install NFS from source to be able to use that configuration file.

---

### Post by Carrot Cruncher on 2011-02-06
hi. i couldn't manage to override the nfs protocol either with a default setting or within autofs however, the reason i was trying to do this was to get around a problem with uid/gid mapping on nfs4. i have now resolved the underlying problem which turned out to be a problem with idmapd.

i had set :
NEED_IDMAPD=yes
in /etc/default/nfs-common and :
Domain = {my domain}
in /etc/idmapd.conf but this didn't appear to be working and the idmapd service didn't appear to be running.

running idmapd manually using :
rpc.idmapd -f -vv
threw this error :
rpc.idmapd: main: open(/var/lib/nfs/rpc_pipefs/nfs): No such file or directory
i couldn't work out what is supposed to create this directory so i created it manually as follows :
drwxr-xr-x 2 statd root 4096 2011-02-06 17:14 /var/lib/nfs/rpc_pipefs/nfs/
i then tried to start the idmapd service which started successfully and mounted the following :
rpc_pipefs on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)

all my uid/gid mapping is now working as it used to under nfs3.

question are :
what is supposed to create /var/lib/nfs/rpc_pipefs/nfs/ ?
or
why does idmapd error when /var/lib/nfs/rpc_pipefs/nfs/ doesn't exist if it then mounts rpc_pipefs on /var/lib/nfs/rpc_pipefs anyway ?

---

### Post by Peter Bell on 2011-02-17
I know that you have found another solution, but I think that [this]("http://ubuntuforums.org/showthread.php?p=10467361#post10467361") might be what you were looking for!

---

