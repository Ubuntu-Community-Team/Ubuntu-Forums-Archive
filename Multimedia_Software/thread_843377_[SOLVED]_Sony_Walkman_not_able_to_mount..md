---
title: "[SOLVED] Sony Walkman not able to mount."
date: 2008-06-28
forum: Multimedia Software
---

### Post by WorldPax on 2008-06-28
I found a fix in this thread but it's not working for me. The thread is marked solved and I don't think anyone is looking at it. I have not had a reply in almost a week.

[http://ubuntuforums.org/showthread.php?p=5240760#post5240760](http://ubuntuforums.org/showthread.php?p=5240760#post5240760)

I attempt this:

> **cozmicharlie said:**
> Is it a Walkman?

This might work for you:

Install pmount: 
```
sudo apt-get install pmount 
```

and then: 
```
pmount /dev/sdxx WALKMAN
```

For sdxx use whatever the device is showing up as in your system.  To find out type or cut and paste:
```
ls /dev/disk/by-label -lah
```

but I get the following when trying the second part of the fix.

pax@pax-laptop:~$ ls /dev/disk/by-label -lah
total 0
drwxr-xr-x 2 root root 60 2008-06-22 17:14 .
drwxr-xr-x 6 root root 120 2008-06-22 17:14 ..
lrwxrwxrwx 1 root root 10 2008-06-22 17:14 WALKMAN -> ../../sdb1
pax@pax-laptop:~$ pmount /dev/WALKMAN
Error: device /dev/WALKMAN does not exist

Please help, I am unable to rock :guitar:

---

### Post by cozmicharlie on 2008-06-28
The other thread was marked solved so I was not tracking - sorry for not responding to your other post.  

In step 2 did you use sdb1 as your device?
pmount /dev/sdb1

---

### Post by WorldPax on 2008-06-28
Thank you, that did it. So do I have to manually mount the mp3 player everytime now, or will it automount it from now on? Oh and feel free to merge this thread with the other, if you think it's necessary.

---

### Post by cozmicharlie on 2008-06-28
I believe you should only have to do this one time.  It should recognize it when you plug it in.  If not post back - there may be a script or something we can write that will do it for you.  You don't have to merge the posts - just mark it solved and others doing a search should find both.

Glad it worked for you

---

### Post by cloggie on 2008-11-18
cozmicharlie Thank you very much.
Just yesterday my wife gave me a Sony nwz-s736f walkman and now i am able to see it in Ubuntu Hardy through your advice.
My only problem is that I rebooted the laptop, just to see if it returned but i didn't. So should I write it into my fstab or not? And if so, what type should I use for this thing?
At the moment I just did "pmount" again and that mounts it, but i don't want to have to do this al the time if you catch my drift.

---

### Post by cloggie on 2008-11-18
cozmicharlie Thank you very much.
Just yesterday my wife gave me a Sony nwz-s736f walkman and now i am able to see it in Ubuntu Hardy through your advice.
My only problem is that I rebooted the laptop, just to see if it returned but i didn't. So should I write it into my fstab or not? And if so, what type should I use for this thing?
At the moment I just did "pmount" again and that mounts it, but i don't want to have to do this al the time if you catch my drift.

---

### Post by cozmicharlie on 2008-11-19
You could try writing it fstab (make sure to back up the current fstab though).  If that does not work you could write a small script and have it set to work when you start the computer.  Try the fstab first and if that does not work I can take a shot at a script.  Also, maybe someone else will come along that knows more than I do and have an answer.

Glad it helped.

How do you like your Walkman?  My Ipod died so I am looking for a replacement.  How much storage do you have on the Walkman?

---

### Post by cloggie on 2008-11-19
Hi,

Thanks for the reply. 
First the connection problem. I fixed it in a whole other way. After some more searching I found a site ([http://kubuntuforums.net/forums/index.php?topic=3096598](http://kubuntuforums.net/forums/index.php?topic=3096598)) where someone had the same problem. There I saw an answer to rebuild hal.
I did and you know what, it worked like a charm. I only rebuild hal and not mtp, maybe I'm gonna do that this weekend, see if it makes a difference. But everytime now when I connect the walkman to the USB port, Nautilus opens up with "Walkman" dir and I can just move files in and out of the player. Even Amarok sees it now without any hassle.

So that problem seems to be solved for me.

As far as the player goes, it has a 4 Gig memory and after using it for two days, it seems like a nice player. It hold mp3's, but can also do video's, photo's, podcasts, and it has a build-in FM radio too. 
The earplugs are a bit of a hassle, the ones that come with it, but they do work as they should too.
Anyway, so far, so good.

(btw, how do I remove the second entry of mine, because it looks so stupid, two entrys with the same answer)

---

### Post by cozmicharlie on 2008-11-20
Te beauty of Linux - their is always more than one way to do things.  Glad it worked.  

Thanks for the info.

Not sure how you remove it- I would not worry about it.

---

### Post by DLF44 on 2008-12-06
i tried entering the code above but it doesnt work for mine. any other ideas?

---

### Post by cozmicharlie on 2008-12-06
> **DLF44 said:**
> i tried entering the code above but it doesnt work for mine. any other ideas?

Are you positive you got the correct drive name here?
pmount /dev/sdxx WALKMAN

Does your walkman show up (is it mounted) when you plug it in to the computer?

---

### Post by DLF44 on 2008-12-07
i entered what i thought it was. how can i find out for sure the correct one?

when i plug it in, it shows up as a usb drive in places. but icant access it or do any thing with it.

---

### Post by helterskelter on 2008-12-07
If you want to use a walkman with Linux try 'Jsymphonic'.

You will need the Sun Java JRE installed to use it.

[http://backports.ubuntuforums.com/showthread.php?t=716477&page=2](http://backports.ubuntuforums.com/showthread.php?t=716477&page=2)



eddie

---

### Post by DLF44 on 2008-12-07
alrighty,so i got jsymphonic and it seems to be working,. i just cant find the device path for the mp3 player. is there a way to do that?

i entered "df -h"
and got:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G   97G   41G  71% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  216K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.8M  494M   1% /dev
tmpfs                 496M  224K  496M   1% /dev/shm
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.27-9-generic/volatile

```

i thought that would list my player but i dont see it there.

---

### Post by cozmicharlie on 2008-12-08
The easiest way is to install gparted (in Synaptic).  It shows all your attached drives and where they are located.  You can also open a terminal and type the code below (dmesg).  It gives a long list but the usb devices are usually towards the end.  You should see your device listed.  Gparted has a nice gui so whatever you are comfortable with. 
```
dmesg
```

or 

```
lusb
```

---

### Post by helterskelter on 2008-12-08
Unzip Jsymphonic..

Select the unzipped .jar executable and open with Sun Java Runtime..

When it opens up use the file browser to got  /media/disk..thats your walkman.

Similar with music files,except point it your music folder.

You have to create a blank folder,name it OMGAUDIO and copy it to your walkman.(do this from the desktop).

There are extensive instructions within the zipfile.

eddie

---

### Post by DLF44 on 2008-12-11
When i type in /media/disk it says:

"the device path you entered is not valid. No folder OMGAUDIO found"

Also when i try to copy the OMGAUDIO folder to the mp3 player. it says operation not supported by backend.

---

### Post by Skiro'n on 2009-02-24
JSymphonic searches in the path you gave a "OMGAUDIO" folder. If your player is empty, as said before, just create an empty OMGAUDIO folder.

Of course, you need to have sufficient rights to create a folder in your player (check that it is mounted with read/write rights for your user).

---

