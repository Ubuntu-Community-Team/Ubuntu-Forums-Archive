---
title: "why is smbfs so slow?"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by acroporas on 2010-12-01
I have two computers, both Running Ubuntu.  10.04 on the desktop, and 10.10 on laptop. 

On the desktop is a partition that is set up as a samba share.

When mount the share as an as an smbfs via fstab, the max transfer rate is 15MB/s

When I mount the share with Places->Connect to server -> windows share the max transfer rate is 60MB/s

Why such a big difference? Is there a better way to share files between two computers running ubuntu than samba?

---

### Post by pricetech on 2010-12-01
I use SSH when I'm connecting two Linux boxen.  Places - Connect to Server and choose SSH as your connection method.

SSH Server does have to be installed and working of course.

---

### Post by Morbius1 on 2010-12-01
My very first guess would be that Places->Connect to server -> windows share isn't using smbfs - it's using cifs. 

Comment out the line in fstab and substutute cifs for smbfs and see if the speed improves.

---

### Post by Boondoklife on 2010-12-01
> **Morbius1 said:**
> My very first guess would be that  Places->Connect to server -> windows share isn't using smbfs -  it's using cifs. 

Comment out the line in fstab and substutute cifs for smbfs and see if the speed improves.

What? Here I always thought it used gvfs. Also mounting the shares in nautilus does not put it in the fstab.

---

### Post by acroporas on 2010-12-01
> **Morbius1 said:**
> My very first guess would be that Places->Connect to server -> windows share isn't using smbfs - it's using cifs. 

Comment out the line in fstab and substutute cifs for smbfs and see if the speed improves.

Replacing smbfs with cifs in fstab makes no difference in speed.  Still maxes out at 15MB/s

---

### Post by lukeiamyourfather on 2010-12-01
Check to see what speed the network adapter is using. I've had network adapters run at 100 Mbps instead of 1,000 Mbps for no apparent reason. Replace eth0 with a different adapter if necessary. Also you might have to install ethtool?

```
ethtool eth0
```

---

### Post by Morbius1 on 2010-12-01
> **Boondoklife said:**
> What? Here I always thought it used gvfs. Also mounting the shares in nautilus does not put it in the fstab.
Did you read the original post? He's comparing mounting it through Nautilus to mounting it through fstab using smbfs.

And what do you think gvfs-mount smb:// uses - magic? It has to use cifs to mount it to .gvfs

---

### Post by Morbius1 on 2010-12-01
Come to think of it if you like the speed of connecting to the share using Nautilus but you want it to automount there is little utility called Gigolo that you might find amusing:
```
sudo apt-get install gigolo 
```And just in case you already don't have it installed:
```
sudo apt-get install fuse 
```It's considered a network browser but it does have the ability to automount remote shares.

The procedure is relative simple:
When you first bring it up make a change in the preferences:
[B]Edit > Preferences > Interface>
Select "Show Side Panel"[/B]
**Select "Start minimized in the Notification Area"**
**Disable "Show auto-connect error messages"**

Then you browse to the share using the Network Tab on gigolo
Then you bookmark the share by right clicking the share icon and select **"Create Bookmark"**
When you bookmark it select the **"Auto-connect"** option

Then have gigolo start at login:
**System > Preferences > StartUp Applications > Add > Command = gigolo**

When you login it will automatically mount remote shares and you will see an icon on your desktop. 

This auto-connect function has one other feature. If the remote share  isn't available gigolo will scan the  network every 60 seconds ( user adjustable ) and mount it when it finds  it.

---

### Post by acroporas on 2010-12-01
> **lukeiamyourfather said:**
> Check to see what speed the network adapter is using. I've had network adapters run at 100 Mbps instead of 1,000 Mbps for no apparent reason. Replace eth0 with a different adapter if necessary. Also you might have to install ethtool?

```
ethtool eth0
```

Please read my original post again. It is not the connection that is the problem.  It is the same two computers talking over the same connection.

1. Mount with smbfs via fstab
2. Test speed - 15MB/s
3. unmount
4. Mount via nautilus
5. Test speed - 60MB/s
6. unmount
7. Mount with cifs via fstab
8. Test speed - 15MB/s

I never rebooted or reconnected so it can not be the connection at fault.

---

### Post by Boondoklife on 2010-12-01
or you could just use a script I wrote. [Here]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77")

---

### Post by Morbius1 on 2010-12-01
*[I][COLOR=Black]acroporas[/COLOR],*[/I]

So the question on that table in my mind is what are your objections to using some variation of Places->Connect to server ( Gigolo, your own gvfs-mount script, or whatever ) over the fstab mount method.

Is it the hidden mount point that gvfs produces by default because you can create a symlink to work around that problem. Or is there a more fundamental problem.

---

### Post by Boondoklife on 2010-12-01
Well if you have different users then you will need to do some magic with fstab or libpam-mount to do it with cifs/smbfs.

To do it with fuse (gvfs) then all you need to do is use my script or just browse to the share. The password for the share will be saved in an encrypted state in your keyring. Gvfs tends to xfer data faster than the other option in my experience.

---

