---
title: "Unable to play dvd.iso over network..."
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by trmentry on 2007-04-28
I was having all kinds of issues getting Totem-Xine to play Divx videos from a Samba share.  I uninstalled Totem-Xine and installed Totem-gtstreamer and it works now.

However, I still am unable to play a dvd.iso over the network.  vlc won't even play it.  If I move the iso to local on the computer, vlc plays it fine.  But kinda defeats the purpose of keeping things centralized.  

I'm at a loss as to why I can't stream a dvd.iso over the network.  I hate to say it but it works in windows fine with vlc, so this is a fiesty issue or I'm missing some obscure library that I can't seem to find in any of the other posts/howtos i stumble on in google.

Any pointers would be most appreciated.

Thanks

---

### Post by hardyn on 2007-04-28
from what you have described, your network does not have throughput to stream the movie.

there have been complaints about samba throughput, and i believe there have been some posts on this forum to improve that.

good luck.

---

### Post by whatever on 2007-04-28
did you mount the smb share? if not you should try it...

---

### Post by mgmiller on 2007-04-28
That's not it.  vlc will not play over a samba share.  Neither will mplayer.  Only totem can do that.  If you want to use vlc or mplayer, you will need to set up nfs shares instead of samba shares and mount the drive to the local machine.  I use this setup for 2 Ubuntu machines on my home network and it works great.  If the machine serving the videos is Windows, I don't know how to get it to play.

As long as it is Ubuntu to Ubuntu, here is how you do it as gleaned from a few other postings from this site.  (I agree, it seems a lot, but just follow it step by step.  Hopefully, this will be semi automated in gutsy gibbon):

  
Part ONE:
NFS installation on the server


Install NFS by typing the next lines on the prompt.


sudo apt-get install debconf

sudo apt-get install libc6

sudo apt-get install libwrap0
sudo apt-get install nfs-common

sudo apt-get install sysvinit

sudo apt-get install nfs-kernel-server


Make a directory that can be accessed by anyone by typing


“mkdir /nameofthedirectory”

“chmod a+rw /nameofthedirectory”
Example...
All I did was take my existing /home/marty and chmod it.
chmod a+rw /home/marty

By using "sudo gedit /etc/exports"
change /etc/exports to add the line:

/nameofthedirectory 192,168,1,0/255,255,255,0(rw,root_squash,sync)
Example...
This is what my /etc/exports looks like:
# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
/home/marty     192.168.1.0/255.255.255.0(rw,sync,no_root_squash)



type “exportfs -av” to activate

type “rpcinfo -p” to test


Part TWO:
NFS installation on the client


Make a directory to mount the server map to by typing


mkdir /mnt/nameofmountmap
Example:
sudo mkdir /mnt/server


Change the permissions, so you can read and write in it by typing


chmod a+rw /mnt/nameofmountmap
Example:
sudo chmod a+rw /mnt/server

Using "sudo gedit /etc/fstab"
change /etc/fstab to add the line:

192,168,1,NNN:/nameofdirectory /mnt/nameofmountmap nfs rw,hard,intr 0 0
(NNN is the end of the ip-adress of the server)
Example:
192.168.1.4:/home/marty	/home/marty/server nfs soft 0 0 

Or you can use the "hard" option instead.  If you use "soft" as above, if the 
server is down when you start the remote machine, you won't get an error message and 
a simple sudo mount -a after the server is booted will mount up the share.

If you use "hard" as below, you will get errors if you try to start up and the server is down
for some reason.  I use the "soft" option.

nameofserver:/nameofdirectory /mnt/nameofmountmap nfs rw,hard,intr 0 0

Finally,
Mount by typing

sudo mount -a

Finally, when it is all working, you should be able to use nautilus to browse to the folder
you have designated as the mount point on the remote machine. In this case it is /mnt/server.  Once it is open and showing all the files, in nautilus, click on Bookmarks>Add Bookmark to create a quick link to the mount point.  Now it is on your Places menu and a single click there will instantly open the share.  You can also stream over this kind of share with vlc and totem, etc.

---

### Post by trmentry on 2007-04-28
Ok I find it strange that vlc won't play from a smb share as it will when its run via windows.

The server is a gentoo box running samba that can handle multiple streams on it. :)  go go gigabit.

Anyway.. I exported to nfs a directory on the server to try out and mounted it on my ubuntu box and vlc plays the files fine now.

Any ideas why vlc won't play via a smb share?   Granted I didn't mount the share per se, just went via PLACES -> CONNECT TO SERVER to try it out.

Thanks for the pointer on nfs.

---

### Post by meltingrobot on 2007-08-16
Had the same problem with my knoppmyth setup.  Drove me insane!!!  I was thinking it was the effing region code crap.  I ended up remounting cifs and everything works FANTASTIC!!!  Just change smbfs to cifs in your fstab.  It will fix things!  ;)

---

