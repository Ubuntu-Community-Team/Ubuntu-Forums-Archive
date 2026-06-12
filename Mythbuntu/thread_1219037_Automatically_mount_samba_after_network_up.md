---
title: "Automatically mount samba after network up"
date: 2009-07-21
forum: Mythbuntu
---

### Post by Caysho on 2009-07-21
How can samba servers be automatically mounted after the network is up ?

---

### Post by nasha on 2009-07-21
[HTML]http://wiki.geteasypeasy.com/How_to:_deal_with_samba_shares[/HTML]
Might provide some help. I know ubuntu scans fstab after network up for NFS shares and then mounts them automatically. I cant speak for samba shares though as i dont use them

---

### Post by Caysho on 2009-07-23
Looks like that is the case for cifs entries.
I had a broken entry (noauto and a typo).
It does work, but it is quite slow to do it - it takes at least one minute to do the mount.

Does it try to check with a WINS first ?  I do not have one set up that I know of.  My smb.conf says not to use WINS.

Found a thread on the [name resolving in samba]("http://ubuntuforums.org/archive/index.php/t-826938.html"), wins means different things in nsswitch.conf vs smb.conf

---

### Post by Caysho on 2009-07-28
> **Caysho said:**
> 
It does work, but it is quite slow to do it - it takes at least one minute to do the mount.

Looks like the mount is waiting for the network to come up - Network Manager is just slow.

---

### Post by Tteddo on 2009-07-29
I do this by adding 4 lines to /etc/rc.d (one for each mount) so that everything is up and running before it tries to mount. This avoids putting it in my fstab.
My rc.d looks like this:

> mount -t smbfs //Warpdrive/Backup /var/Backup -o rw,uid=tteddo,username=tteddo,password=password &&
mount -t smbfs //Warpdrive/wwwroot /var/wwwroot -o rw,uid=tteddo,username=tteddo,password=password &&
mount -t smbfs //Warpdrive/Triton /var/Triton -o rw,uid=tteddo,username=tteddo,password=password &&
mount -t smbfs //Phaedrus/www /var/www -o rw,uid=tteddo,username=tteddo,password=password &&

exit 0

Warpdrive is a Win2000 box and Phaedrus is an Intrepid machine. This also avoids hangs if one of the remote machines is off or something.

---

