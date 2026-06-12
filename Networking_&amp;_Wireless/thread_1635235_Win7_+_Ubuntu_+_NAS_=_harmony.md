---
title: "Win7 + Ubuntu + NAS = harmony?"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by Jago-X on 2010-12-01
So I have been searching for info on this topic for a while now and have never really found "the" definitive answer on how to do it easily.

My hardware setup is as follows:

- Desktop: dual boot Win7(x64) & Ubuntu v10.10 (x64)
- Laptop: Windows XP (x32)
- NAS: Dlink DNS-321 - 1.5TB drive (ISOs) & 750GB drive (docs, pics, etc.)

Within Windows I have it setup so that the the My Documents, My Pictures, My Music & My Pictures all point to the NAS which is was very easy to do...in Ubuntu, not so much :(

I've managed to get Ubuntu to be able to let me *see* the network drives and I can read/write to them. The one thing I can't seem to figure out how to setup is how to have Ubuntu set the Videos, Pictures, Music, Documents, etc. folders on the NAS.

Is this even possible? or is there something I am missing somewhere?

---

### Post by Boondoklife on 2010-12-01
You could use [this]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77") script to mount the folders on login and then create links pointing to the mounted shares.

Note: look in ~/.gvfs for the shares

---

### Post by Jago-X on 2010-12-01
Oh nice...I'll give that a test right now :) I'll let you know if it works...

---

### Post by Jago-X on 2010-12-01
Oops...just realized I forgot to mention that the NAS is password protected. Will this make a difference at all with your script?

I've done some other tinkering & since Ubuntu is just my "play thing" I may just wipe and reinstall...probably do that tomorrow when the wife isn't home ;)

---

### Post by Boondoklife on 2010-12-01
You have to map them one time using nautilus, when you do this it will prompt you for your password. If you tell it to remember it, you will not be prompted again. This script assumes you are using your login as that username.

---

### Post by r.peel on 2010-12-03
I have a similar question.

Instead of moving my Documents etc. folders to the NAS id link to sync some of them to the machines hard drive (specifically thinking about my laptop and netbook).

In windows I can use SyncToy and mapped drives to do this, how can it be achieved in linux, preferably without having to touch the cmd line?

--
I don't have a NAS box yet but don't want to invest in one if this isn't possible.

---

### Post by Boondoklife on 2010-12-03
> **r.peel said:**
> I have a similar question.

Instead of moving my Documents etc. folders to the NAS id link to sync some of them to the machines hard drive (specifically thinking about my laptop and netbook).

In windows I can use SyncToy and mapped drives to do this, how can it be achieved in linux, preferably without having to touch the cmd line?

--
I don't have a NAS box yet but don't want to invest in one if this isn't possible.

Dropbox

---

### Post by r.peel on 2010-12-03
> **Boondoklife said:**
> Dropbox

Will DropBox allow me to sync just between two locations on my network? 

I have little / no desire to use the "cloud"

---

### Post by Boondoklife on 2010-12-03
It does lan sync as well as cloud. You could try rsync but doing that over samba can be a pain, if you even get it to play nicely it is a miracle IMHO.

---

### Post by Jago-X on 2010-12-21
> **Boondoklife said:**
> You could use [this]("http://ubuntuforums.org/showpost.php?p=9322776&postcount=77") script to mount the folders on login and then create links pointing to the mounted shares.

Note: look in ~/.gvfs for the shares

Sort of late in following back up in this thread but your script worked great & I got the 2 drives to mount on startup...but I can't get Ubuntu to redirect the locations of Documents, Pictures, etc. :(

I tried using Ubuntu Tweak to change the location & after sharing the 2 mounts in ~/.gvfs, I got the UT to let me chose the folders on my NAS however when I rebooted it didn't seem to save. Is there a manual way to change this that I may not be aware of?

---

### Post by Boondoklife on 2010-12-23
try dropping to terminal and rm moving the folders you want to link.

First remove the folders, make sure you have everything out of them that you want to keep.
```
cd /home/USERNAME
rm -fR Documents Music ETC...
```then create links to the shared folders
```
ln -s '/home/USERNAME/.gvfs/Documents on SERVER' '/home/USERNAME/Documents'
```Note the ('), this will make sure any spaces are correctly interpreted.

Just remember this will only work when you are connected to the network, if you are not then you will not have access to your files and the links will not be valid.

---

