---
title: "Network drive connection"
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by dougalkerr on 2009-07-23
How do I keep my Network drives once making connection. That is when Ubuntu starts next time I want to see my Network drives icons ready to go... Vista reconnects automatically when the option is slected. I have seen the option to Bookmark the drive but, I don't know what this does, it certainly makes no difference to seeing the icons next start-up.
Cheers.

---

### Post by brallan on 2009-07-23
there is a file called 

/etc/fstab

which determines which drives are automounted on setup. you may be able to edit this file and get it to do what you need. what command/steps are you using to mount the remote drives?

---

### Post by Grenage on 2009-07-23
He's already got the remote drives mounted, he just wants them to automatically mount when he reboots.  I'd do it using fstab:

[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by dougalkerr on 2009-07-23
As Grenage says: I have the drives connected but, they don't appear again when I start-up next time.

---

### Post by dougalkerr on 2009-07-23
Grenage: I looked at the link you left but, it is overly complicated and not instructive enough, ie; when I connect Network drives manually on a Windows Terminal I would simply type something like;

net use g: \\fs1\sharename

and save it as a batch file to load with Windows.

The commands and adding of the text lines to /etc/fstab seem very complicated compared with this. Besides Ubuntu now has a simple GUI to enter the details. I just need to know how to make the drives persist as you quite rightly obsevred.

Thanks for your input though...

---

### Post by Grenage on 2009-07-23
Ok, then let's take the GUI route.  Why does it not work for you when you add a bookmark?  For example, I have a bookmark for smb://fileserver/documents/

When I click on it after a reboot, it mounts the share and opens it.  What happens for you?

[ATTACH]122136[/ATTACH]

---

### Post by Sweaty Elvis on 2009-07-24
Hi, hope nobody minds too much if a noob butts in with a similar question,

I have a secondary internal drive that I would like to mount automatically on startup...*without* having to click on it.  (my screensaver pictures are on it.)

Can editing fstab help me?  What exactly is the right code to add to fstab?  Following is the contents of my fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=132981b1-0117-4ddd-9e14-f6284bc899f2 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d53f68aa-d603-496a-aad0-33f45b726d65 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```Thanks for any help and sorry for the (partial) hijack.

---

### Post by Swammy on 2009-07-24
I had a problem when trying to mount network shares, but I ended up coming to an easy solution by doing the exact same thing that Grenage is suggesting. Here's the step by step:

1. Hit Alt+F2, this brings up the Run window
2. Type in your shared folder as follows: > smb://192.168.0.11/TV Shows
(The ip and folder name are there for reference...ensure you change to apply to your own network share)
3. If you typed it right, your network share pops up...Hit Ctrl+D to add this as a bookmark
4. From now on, that network share shows up in your "places > Bookmarks" menu, even after rebooting your computer.

Editing the fstab was complicated for me, and it ended up causing an error with my wireless card hanging upon reboot. Granted, I'm not the smartest person when it comes to Linux...but hopefully my problem has helped lead to your solution :)

Good luck to you.

---

### Post by brallan on 2009-07-26
> **Sweaty Elvis said:**
> Hi, hope nobody minds too much if a noob butts in with a similar question,

I have a secondary internal drive that I would like to mount automatically on startup...*without* having to click on it.  (my screensaver pictures are on it.)

Can editing fstab help me?  What exactly is the right code to add to fstab?.... Thanks for any help and sorry for the (partial) hijack.

if you ask your question in a new thread. other users will have the same question and can find the answer easier. and then if it gets solved, you can mark it solved so folks know that too.

first make a mount point:

```
sudo mkdir /mnt/seconddrive
``` or
```
sudo mkdir /media/seconddrive 
``` in /media it will create and icon on the desktop


go ahead and back up your fstab file:
```
sudo cp /etc/fstab /etc/fstab.bak
```

then look at:
```
mount
```
to see what you have mounted now.
```

sudo fdisk -l
``` to find out the dev/ address of the partition you want to automount. if you want, you can also figure out it's UUID using
```
sudo blkid
``` 

whats UUID? old fstab files used syntax like /dev/hda1 or sda1. Now, using UUID permits drives to be moved around or even USB drives & pendrives to autmount!

now you have the info to edit (add a few lines to) your fstab:
```
sudo gedit /etc/fstab 
```
if the partition you wanna add is /dev/sdb1, and the partition is fomratted ext3:

add:
```
# Comment: Manually added second hardrive which was at /dev/sdb1
UUID=long-string-of-blkid-chars-with-the-quotes-removed /media/seconddrive               ext3    rw,user,exec		0	0

```

if its ntfs just put ntfs where it says ext3.

and if its mounted, unmount it using 

```
sudo umount /dev/sdb1
```

then to remount it on the new mountpoint, just do:

```
mount -a
```

hope that helps

---

### Post by Sweaty Elvis on 2009-07-27
> **brallan said:**
> hope that helps

It sure did!  Thank you for the detailed instructions.

Let me summarize what I have learned here, for people doing a search:

The different between /mnt and /media is that a volume in /media will show up in the desktop.

I can edit configuration files owned by root by launching gedit from the command line with ```
 sudo gedit /path/filename 
```Internal and external local drives can be automatically mounted by following the steps you described above.

> **brallan said:**
> if you ask your question in a new thread. other users will have the same question and can find the answer easier. and then if it gets solved, you can mark it solved so folks know that too.

That's a good idea.  Maybe some helpful moderator will move this into a new thread :-).

---

### Post by dougalkerr on 2009-07-30
Hi Guys

I have the Network drive listed under the 'Places' menu after ensuring I had it bookmarked. Not sure why I hadn't noticed it there before. Probably coz my brain was lazy in thinking I would see the drive icon on the Desktop or my Web browser for some reason (Bookmarks and so on...).
So now that I have the drive available every start-up how can I make it available without having to enter my password every time. I had noticed somewhere the option to remember the password forever but, it is not on the GUI interface available under 'Connect to Server'.

Thanks for all the suggestions guys - tremendous help...

---

