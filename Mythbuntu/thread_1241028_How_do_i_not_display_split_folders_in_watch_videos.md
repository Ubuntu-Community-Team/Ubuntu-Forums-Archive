---
title: "How do i not display split folders in watch videos?"
date: 2009-08-15
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-15
Hi;

I have all of my ripped dvd .iso files on my second harddrive within my myth box mounted at /media/media/videos.

I have a load of .mp4 / divx / mpeg / vob etc files on my nas that i want to view in myth.  I have added both locations under the general media libary settings and have access to both folders.  (Mounted under /media/nas/videos)

The part i would like to change is the folder icons displayed under media libary-watch videos.  

I would like to have all of my collection displayed in one screen without having to navigate between the nas folder and the local media folder.  

Is there an easy way i can achieve this in myth?  (Is a symblink enough?).

Thanks.

---

### Post by geekyhawkes on 2009-08-17
Is this possible?  I am also going to have to install another internal HDD as my media drive is full and it would spoil the Myth interface if i have to pick which hdd to view from via these folders rather than browse all my videos / ripped dvds.

---

### Post by newlinux on 2009-08-17
at worst you could probably symlink each indivual file under your main media directory and scan that one only.

---

### Post by geekyhawkes on 2009-08-17
Wow thats no small job!  Im just about to add a 1TB drive having already filled my 500gb drive with about half my dvds!!  

Can i not just use a symlink directory 2 directory?  

Or is there some kind of batch command from bash i could use to create a bunch of symlinks?

---

### Post by newlinux on 2009-08-17
> **geekyhawkes said:**
> Wow thats no small job!  Im just about to add a 1TB drive having already filled my 500gb drive with about half my dvds!!  

Can i not just use a symlink directory 2 directory?  

Or is there some kind of batch command from bash i could use to create a bunch of symlinks?
 If you symlink directory to directory, I think you'd end up with the same problem (because you'd have a subdirectory in your mythvideo directory). Don't know of any existing scripts, but someone with real shell scripting skills (unfortunately that's not me) could probably do it pretty quick. I could probably do something, but it would take me a while to write it up.

---

### Post by geekyhawkes on 2009-08-18
I guess i will have to have to symlink all of my files and see if that works.  Im guessing i could select all the files and choose create link from the gui?  See how it works!

---

### Post by SiHa on 2009-08-18
It's surprisingly easy to script this.

I've been fiddling around for a while and came up with this one-liner:

```
ls /media/*.mpg /media/*.avi | while read i ; do ln -s "$i" /var/lib/mythtv/videos; done
```

This will list all .mpg and .avi files in /media, and create symlinks with the same name in /var/lib/mythtv/videos.

If you wanted to save this as a script:
```
#!/bin/bash
ls /media/*.mpg /media/*.avi | while read i
do
   ln -s "$i" /var/lib/mythtv/videos
done

```

The quotes in the ln command are so that it will work with long filenames containing spaces. If you regularly add videos, you could run this as a cron job. Each time it runs, if the symlink already exists, it will just be skipped.

**Edit:** I've been thinking, and this could probably be simplified by turning it on it's head:
```
ln -s "`ls /media/*.mpg /media/*.avi`" /var/lib/mythtv/videos
```

Really it would be neater if each time the script ran it removed all symlinks and re-created them all, so it would update if you removed videos.

> rm "`ls -F /var/lib/mythtv/videos/|grep @|cut -f 1 -d \@`"

Will (I think) remove all symlinks from the /var/lib/mythtv/videos directory. ls -F categorises all entries, and symlinks are marked with an @ grep only returns those lines with the '@', and the cut command removes this from the grep results so that 'rm' can remove the file. Note the " ` " is not a " ' ".

**Edit:** The double quotes should allow for spaces in the filenames - not tested.

**[COLOR="Red"]Warning[/COLOR]** This last bit works after minimal testing on my system, but your are strongly advised to test this some more if you intend to use in anger. I don't want to be responsible for you losing all your videos!

Hope this is of some help.

Simon

---

### Post by geekyhawkes on 2009-08-18
Perfect cheers simon!  This seems to be just what i am after, i will give it a whirl this weekend! 

Great work thanks!

---

### Post by tgm4883 on 2009-08-19
> **geekyhawkes said:**
> Perfect cheers simon!  This seems to be just what i am after, i will give it a whirl this weekend! 

Great work thanks!

I think you have your video directories set up incorrectly. It sounds like you have /media/nas/videos set up and two directories in that?  What do you have your media directory set up as in MythTV? For multiple directories, you should set it up as

```
/path/to/dir/1;/path/to/dir/2
```

---

### Post by geekyhawkes on 2009-08-19
I had setup multiple directories in myth but i didnt want to navigate around to view everything i have saved around my various folders etc. 

Creating symblinks has solved the problem for me as i just drop symlinks into the myth video directory and then it doesnt matter where the file "really" lives.

---

### Post by tgm4883 on 2009-08-19
IIRC, If you setup multiple folders in Myth (not multiple folders under the directory you told Myth), then you don't even need to symlink them. It just shows up in your library

---

### Post by geekyhawkes on 2009-08-19
Ok Thanks.

---

