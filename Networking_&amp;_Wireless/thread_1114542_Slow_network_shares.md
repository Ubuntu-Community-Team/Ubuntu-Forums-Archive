---
title: "Slow network shares?"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by jh0n on 2009-04-02
I've got a small home network.  Two desktop PC's and a NAS device wired into a wireless router with a laptop connected wirelessly.  Basic  connectivity, etc. is fine whether wired or wireless.  All PC's can browse each other's shares.  Things are good.

Except for the PC-to-PC shares.  They're SLOW.  I have two primary shares.  One is a Synology DiskStation sharing up a 1tb NFS RAID 1.  The maximum throughput on the device is about 3mb/s, which I see when transferring files to/from.  The other share is a 1tb USB drive (formatted NTFS) on one of the wired PC's.  It's a mirror of the DiskStation NAS.  

The problem I have is that when changing directories, I experience REALLY substantially slow times.  Changing to a directory that contains ~500 items within it can take a minute or more.  It doesn't matter which PC I do this from, or which share I do this to.  

If I didn't know better, I'd grin and bear it.  But on my work network (2k3 domain), I regularly work within directories with over 2k subdirectories/files, and the time it takes to browse those shares is almost negligible.  Two seconds, max.  And my servers there are loaded down with MANY more clients accessing them.

Any thoughts?  It has to be network related, because browsing the USB drive from the PC it's attached to is relatively quick.  A bit slower than I'm used to, but not substantial.

Thanks in advance.
-j.

---

### Post by freonchill on 2009-04-02
assuming 54mbps wireless (54mbps theoretical max)
54 / 2 / 8 = 3.375mbps

so over wireless you arent going to get more than 3.3megabytes per second

now, for your slow browsing, i dont know about that
over wireless (54mbps) i have similar setup, though using directories, (not with icons / thumbnails) i can access most < 200 file directories in next to no delay.

---

### Post by jh0n on 2009-04-02
Yeah, I'm not looking for more speed.  Because I do a lot of work between directories, I need to drastically reduce the latency.  Going from directory to directory in cases where they're both <25 items can take 10s or so...

---

### Post by dmizer on 2009-04-02
What kind of data is in the directories? Try disabling thumbnails.

For the network drives, how are you connecting to them?

---

### Post by jh0n on 2009-04-03
it's all music.  previewing is off.

the nas device is nfs.  connecting via:

192.168.0.110:/volume1/Storage /media/TeraStation nfs rw,rsize=8192,wsize=8192 0 0

in fstab.  from other pc's sometimes i just connect to smb share from "connect to server" dialog as needed.

the ntfs usb disk is just shared thru nautilus right click menu.  connect via smb.

any other thoughts?

---

### Post by dmizer on 2009-04-05
Anything connected via "places > connect to server" is very likely to be slow both in read/write as well as displaying content. Also, my experience with IDE drives connected via USB has been the same as yours and to make matters worse, your USB drive is NTFS which will slow things down even further.

The thing that's puzzling me is your NFS mounted via /etc/fstab which should be quite speedy even with gobs of data in the share.

Someone else with a similar problem was able to solve it by using Thunar instead of Nautilus for their file manager: [http://ubuntuforums.org/showthread.php?p=6509369#post6509369](http://ubuntuforums.org/showthread.php?p=6509369#post6509369)

---

