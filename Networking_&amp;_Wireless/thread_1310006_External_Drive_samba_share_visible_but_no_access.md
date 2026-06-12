---
title: "External Drive samba share visible but no access"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by cordage on 2009-11-01
I had, on Jaunty, my external drive shared from the root so that my home network can access all files from there. On upgrading, I have to set the share at each boot *and* though the windows machines can see that it is shared, none of them can access it. I get Y:\ not accessible, Network access denied.

I have set Guest access on the share, I even set to login with my username. The later kept asking me for my password over and over.

The drive is set with my user account as owner. All the other network shares on the internal drive work with no problems. The only issue is the external drive.

It is formated NTFS and is 320GB. Again, this worked in Jaunty and not in Karmic.

Any guidance would be appreciated.

---

### Post by blkcat1028 on 2009-11-02
I'm having the exact same problem. I thought I was the only one. Have you made any progress? I had to revert to using my Windows box as a server. I feel dirty. :shock:

---

### Post by BouncinDave on 2009-11-13
Same issue here.

I've shared local drive access, and external drive access. Other computers can access the local shares, but the ones on the external drive get access denied.


Any solutions?!

---

### Post by dmizer on 2009-11-13
This probably has something to do with how the external drive is mounted. Did you create an entry for the external drive in /etc/fstab with the necessary permissions, or did you just let nautilus auto-mount handle it?

---

### Post by BouncinDave on 2009-11-13
I've done mine using nautilus auto mount...

How would I do it with /etc/fstab?

---

### Post by dmizer on 2009-11-13
> **BouncinDave said:**
> I've done mine using nautilus auto mount...

How would I do it with /etc/fstab?

Start here: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by BouncinDave on 2009-11-13
So you would put the entry into fstab, and then share the media in the /media folder (rather than just in 'computer'?

---

### Post by dmizer on 2009-11-13
> **BouncinDave said:**
> So you would put the entry into fstab, and then share the media in the /media folder (rather than just in 'computer'?

You can mount the USB disk anywhere, so if you need it to be mounted in your home directory, feel free to do so. The important part here is the permissions rather than the mount location.

---

