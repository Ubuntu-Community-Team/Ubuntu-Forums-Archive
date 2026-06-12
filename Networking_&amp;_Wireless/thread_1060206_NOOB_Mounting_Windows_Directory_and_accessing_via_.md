---
title: "NOOB: Mounting Windows Directory and accessing via Terminal"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by JetJock_fl on 2009-02-04
I have Ubuntu 8.10 installed on my PS3 and I can see my Windows Network and I can mount a folder I am sharing by right clicking on the windows folder in Ubuntu and selecting Mount. It then appears on my desktop. This is great...however, I can't seem to find it's directory location. I get something like this when I select properties:

smb://cudaencoder/sharedfolder

when I use that structure in say:

dd if=/dev/cdrom of=smb://cudaencoder/sharedfolder/journey.iso.

it says no such directory or something like that.

I would like to have dd dump the ISO to my windows folder. Am I missing a step, or have I munged the syntax? Any help would be great.

---

### Post by pnutzh4x0r on 2009-02-04
If you mount a network resource (smb, ssh, ftp, etc.) using nautilus (gnome-volume-manager) it will use fuse to create a mount point under $HOME/.gvfs ($HOME is your home directory).

So you can hopefully do:

dd if=/dev/cdrom of=$HOME/.gvfs/cudaencoder/sharedfolder/journey.iso 

or something to that nature.

---

### Post by JetJock_fl on 2009-02-04
I will try that right now. I'm not sure what my home directory is but I will find out, easy enough. Thanks a bunch...BRB.

---

### Post by JetJock_fl on 2009-02-04
Well that didn't work for me. I don't know if it's a PS3 thing or I'm not using GNOME or what but I can not navigate my way in terminal to the mounted folder.

I can creat files in it, I can read files, I can see pictures. But when I leave the GUI and go into terminal, I can't seem to find that folder. It's weird too because the icon is placed on the desktop but when I cd desktop, I don't see any link there either. This must me some weird VOODOO mounting that the GUI that comes with Ubuntu is doing. 

Maybe if I mount it myself from terminal and install samba I might be able to mount it to a place I can navigate to.

Anyone else got any ideas? Thanks for all your help

BTW, I tried:

dd if=/dev/cdrom of=/root/.gvfs/cudaencoder/bluray/journey.iso.
dd if=/dev/cdrom of=/.gvfs/cudaencoder/bluray/journey.iso.
dd if=/dev/cdrom of=//.gvfs/cudaencoder/bluray/journey.iso.
dd if=/dev/cdrom of=/root@ubuntu@PS3/.gvfs/cudaencoder/bluray/journey.iso.

nothing seems to work

---

### Post by pnutzh4x0r on 2009-02-04
Your $HOME directory is usually /home/<username> with username being what you logged in with.  If you happen to be using root (which you should NOT be btw), then $HOME is /root.  To find out what it is, just open a terminal and do 

```
echo $HOME
```

As a note, $HOME is the same as ~/.

After you mount the network resource using the GUI, open up your terminal do:

```
ls ~/.gvfs
```

Your smb resource should be mounted there and show up.  If not, then something may be wrong.  Also this also would probably only work if you are using GNOME.

---

### Post by JetJock_fl on 2009-02-04
Thanks For stickin with this problem so much. I will now try what you posted above. I didn't want to use root, as a matter of fact, I had to jump thru hoops to get root to be login-able at the login screen. Unfortunately, I think it might be a PS3 thing, the CDROM dev won't let dd do it's work under anything other than root.

I budgeted a week to get this to work. I'm halfway down!

---

### Post by JetJock_fl on 2009-02-04
I typed ls ~/.gvfs
and it returned in a pale blue color
bluray on cudaencoder

so then I typed:
dd if=/dev/cdrom of=/root/cudaencoder/bluray/journey.iso.  (didn't work)
dd if=/dev/cdrom of=/root/.gvfs/cudaencoder/bluray/journey.iso.  (also didn't work said same thing "no such directory or file)

could I do this:

dd if=/dev/cdrom of=/root/bluray%20on%20cudaencoder/journey.iso.   (???)

---

### Post by pnutzh4x0r on 2009-02-04
You can enclose paths with spaces with quotes:

```
dd if=/dev/cdrom of="/root/.gvfs/bluray on cudaencoder/journey.iso"
```

---

### Post by JetJock_fl on 2009-02-04
Oh GREAT! Now what am I supposed to do with the other half of this week I budgeted to get this done? You got it workin half a week early!!!

Thanks a ton! The quotes did it. I still wonder if %20's would have worked too. Oh well, its a 25gig disc and I see I'm getting 4Mbps on the network connection (100Mbps) Not sure why that is but I'm not complaining! I will let it go all night. It's directly connected thru a switch and a router, should be much faster.

---

