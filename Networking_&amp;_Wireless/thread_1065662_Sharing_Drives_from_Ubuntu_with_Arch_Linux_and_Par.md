---
title: "Sharing Drives from Ubuntu with Arch Linux and Pardus"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by EmyrB on 2009-02-10
Hi All,

I have 3 Linux boxes in my house, 1 Ubuntu 8.10, 1 Arch Linux running KDE 4.2 and 1 Pardus 2008.1.

I have a 1TB drive in my Ubuntu box which I have got my music collection on. This drive is mounted permanently in /media/sda2 and has an icon on my Ubuntu desktop.

Now my daughter's PC is the Pardus box and my son's is the Arch Linux box and they want to be able to play the music on sda2 through the network.

I have tried setting up the share through NFS, but alas I cannot install nfs-common on the Arch or Pardus box as that file doesn't exist (I think arch has something like nfs-utils) and both boxes refuse to connect to the share.

So I thought I'd try the Samba route. I right-clicked on the sda2 folder in /media and select the "share" option, but it refuses to share anything, which I assume is to with permissions.

I don't want anything fancy, just read permissions. I have posted this in the Arch and Pardus forums to see if they can shed some light as well.

Cheers in advance

EmyrB

---

### Post by DiGiTGOD on 2009-02-10
If you've got Samba installed on the Ubuntu box, I find it better doing the sharing via the config file directly.  Never really been a fan of GUI's...

To create a readonly share in samba with Guest access (i.e. no password required), try adding this to /etc/samba/smb.conf

```
[TV]
        comment = TV
        path = /var/videos/TV
        force user = martin
        force group = martin
        writeable = no
        guest ok = yes

```

(I trust I don't need to say to change the tags?)

Then restart samba 

I would say that NFS is definitely a better option if you can get that to work... I only do it because I'm yet to convince the Girlfriend that Ubuntu is the light in the darkness! 

Hopefully, it's only a matter of time...

Hope this helps...
Martin

---

### Post by EmyrB on 2009-02-10
Hi Martin,

Cheers for that, I'll give it a go. I think NFS would be better, but as I'm stuck on what to install for Arch and Pardus with regard to NFS, I'll give this a shot :)

---

