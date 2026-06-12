---
title: "Mounting Remote FTP Folder as a Local Folder"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by TerranRich on 2011-12-09
Hi UbuntuForums community... How would one mount a remote FTP folder in Ubuntu 11.10? I remember it used to be so easy in previous versions. All I had to do was go to "Places", Connect to Server, enter in the details, and it would be saved as a permanent location that I could then navigate to from within Quanta. It used to be as easy as this: [http://ubuntuguide.net/an-easy-way-to-mount-remote-filesystem-on-ubuntu](http://ubuntuguide.net/an-easy-way-to-mount-remote-filesystem-on-ubuntu)

Fast forward a few years. No more Places. Connect to Server still exists, but doesn't save the FTP location as a mounted folder. And when I log off, it disappears. Quanta is gone, and I've been getting used to BlueFish instead.

Is there a simple way to mount a remote FTP location as a local folder? Something like /whatever/foldername? If not, is there an easy-to-follow tutorial? I tried this one -- [http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html](http://www.ubuntugeek.com/how-to-mount-ftp-folder-to-local-directory-in-ubuntu.html) -- but Terminal gave me an error about "line 16" in the fstab file (the one I was supposed to add in the previous step).

It just seems that things have gotten needlessly complicated since I last used Ubuntu around 2007/08. Any help would be greatly appreciated. Thanks!

**EDIT:** I know how to add Bookmarks for FTP locations... is there any way to mount one onto a local folder? ~/ftpfolder/ or something?

---

### Post by drdos2006 on 2011-12-09
Check this out 


HOWTO Ridiculously easy home file sharing with FTP and Zeroconf
[http://ubuntuforums.org/showthread.php?t=218630](http://ubuntuforums.org/showthread.php?t=218630)

This tutorial will cover setting up ridiculously easy, reliable, cross platform, standards based home networking. You will be able to share files from any Ubuntu/Debian system and connect to them from any Linux, Windows or OS X box. If you want to share your files on a firewalled home network but dont want to bother with Samba, NFS, or AFP this is for you.


regards

---

### Post by TerranRich on 2011-12-10
Thank you for replying, but that really doesn't help me at all. :( The "Places" feature is gone in Ubuntu 11.10, and I'm not sure how to use the tutorial you linked to, to use a FTP login such as [ftp://ftp.mywebsite.com](ftp://ftp.mywebsite.com).

**EDIT:**
Okay, there is **NO** documentation on this anywhere I've found, but apparently "Places" vanished and the "Connect to Server" feature is in the File menu of the file browser (the equivalent to Windows Explorer, not sure what it's called). However, whereas in previous versions of Ubuntu you could mount it to a folder (like ~/blahblah/), there is no such option. The FTP connection appears under "Network", but if I shut down the computer and boot back into Ubuntu, the FTP location is gone. I see that I can add a Bookmark, and that's fine for now I suppose, but I really just wanted to know if I could mount it to a folder, so that in BlueFish (since Quanta is apparently gone) I can just navigate to it easily. And now that I look at it again, you can't type in the location you want to go to (like you can in any Windows dialog window), and have to point and click to it instead. So I guess a Bookmark is just as easy to use as a mounted location in this case.

So I guess this is solved. But it really shouldn't be this difficult, and there should be some simple documentation on it that doesn't involve installing something like CURLFTPFS or some SSH solution. This was all using built-in functionality, but nothing I read online mentioned where "Places" had gone.

---

