---
title: "How to ensure file system and permissions correct on USB stick? / using repository?"
date: 2009-01-01
forum: Multimedia Software
---

### Post by xarte on 2009-01-01
I'd saved some packages on a USB stick in Ubuntu, and just now tried to open them in Mint. I couldn't open them and couldn't change permissions, and the instructions I didn't make much sense to me. So I dragged the files onto the desktop, and was able to change the permissions. I opened one of them but the package manager said I should use the repository.

So two questions.

1) When using USB sticks (and I suppose SD cards too?) how do I make sure that I've got the correct file system for data storage, and that permissions are enabled so that I can use it for a different distro?

2) I'm guessing that it wants me to use the built-in software repository because it checks for dependencies?  Is there another reason that I should use this rather than saving packages to disk?

(Basically I'm trying to save download and time when playing with different distros, and since Mint is ubuntu-based I figured the debs would work. Later I'll want to import files etc from my Mac and back.)

---

### Post by mc4man on 2009-01-01
The message about repo's is fairly standard, if you know what your doing then there is no problem directly installing packages.
Properly created packages will install any added deps. as long as they're available from your enabled sources.

If your not sure about what your doing then just use the repo's.

Fat32 or NTFS is better for external drives, Ext2/3 only allow write for the owner which obviously may be different on other installs.

For example
If I have a flash drive in Ext2 which I've chowned to me (doug) the only other installs of linux that will have write permissions on it would have to have a user name of doug .
( or you'd have to kept chowning it per use to the username

---

### Post by xarte on 2009-01-01
ah, ok. Well I don't know what I'm doing.. but hey, gotta learn somehow.

I did have the same username, always do... so not sure what gives there.  In the first properties tab it says msdos filesystem, then in volume it says vfat (fat16), and permissions could not be determined.

why fat16 and not fat32? Should I reformat it?

---

### Post by mc4man on 2009-01-01
The username thing only applies to Ext2/3 
You shouldn't have any trouble with vfat flash drives as far as read, write on linux, mac ect. unless you don't 'safely remove' in windows. (it's good practice in linux and mac to unmount before pulling the drive out.

The permissions tab doesn't matter, the mount options do. I'm not sure what mint does so don't know..

> couldn't open them and couldn't change permissions, and the instructions I didn't make much sense to me

here's a screen of the mount option ubuntu uses on a vfat flash drive

---

### Post by xarte on 2009-01-02
that looks pretty much the same as the information on mine. 

Well I'm mystified. Maybe it was just the fact that it was the package manager trying to access it? I'll experiment with other file types and see if I have any further problems. 

Thanks for that.

---

### Post by Geweten on 2010-01-02
Hi guys I'm already in there since Ubuntu 5 and found my way through the woods...
I preferred not to start a new thread since my questions are about "permissions" too...

But this permission-thing drives me nuts...

Could it be that since I use Karmic 9.10, the usb stick's permissions get changed, each time you copy large (e.g. 1gig) blocks of files to it ? (also f.e. songs get mixed up: getting a songtitle with incorrect performer... But this may be another thread...)

I surfed around and found no accurate solution, I tried editing /etc/fstab as suggested in older threads...
Tried chmod...
Tried gksu nautilus...
I checked my "users and groups" permissions and they are as they should...

Nothing works.

The file system is fat and became read only...
I cannot delete/ anything...

What am I missing ?
Do I really have to format and lose all files ?
Should one format a stick each time you want to put other stuff on there ?
I sometimes wonder weather "sticky bits" (and pieces) might hang in there to ruin newly added files ?! (since Ubuntu automatically seems to add a .trash file...)


Thanks in advance !

---

