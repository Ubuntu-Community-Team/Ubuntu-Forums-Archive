---
title: "Mythvideo Setup (shares) HELP Please"
date: 2009-04-05
forum: Mythbuntu
---

### Post by rodercot on 2009-04-05
Hey Guys,

 I have been reading all day, to find a simple solution to this issue. 

 here is my setup.

 Unraid Server (Media) SMB shares as

 //TOWER/disk1, disk2, disk3, disk4 etc..
 
 Then in eash disk I have this folder structure

 disk1/Movies1, disk1/TV1, disk1/HDMovies1
 disk2/Movies2, disk2/TV2 etc 

 The files are 

 /disk1/Movies1/movie_name/Video_TS
 /disk1/TV1/show_name/season1/showname s01e01 - ep1.avi
 /disk1/HDMovies1/moviename/moviename.ts

 My mythsetup is 
 
 1 - mstr b/e
 2 - frontends only

 I am trying to configure mythvideo to see the shares on my unraid server. I have read and read as to how to do this properly. 

 What would the proper solution be for this, how could I mount all the drives on the mstr b/e and then have them show up on each of the frontends.

 I can only find tidbits of different setups via google or the wiki and not really a definitive process to getting all this to work. 
 
 Any help or guide info for this would be Awesome.

 Another issue is I have all of my movies setup with NFO's for movies and tvshows as well as hdmoves and each file or episode contains either a coverart .tbn or .jpg file and or an episode thumbnail and all the nfo's have an imdb or tvdb ID #, will mythvideo use these nfo's or do I have to scan it all manually again. 

 This should not be this difficult I hope it get's easier in 9.04, with xbmc I can setup my sources and scan my library in under 15 minutes, I am hoping it can be that simple in myth.

 I would be happy to write a Good tutorial on this once I have it working, because I started working on this at 5am this morning and I am right now still no further ahead.

 Thanks,

 Dave

---

### Post by rodercot on 2009-04-08
Still having issues with mounting shares. I have since I think properly created my mounts on the master backend. The confusing part to me now is how do I setup and share the proper folders to the frontends with symlinks and exports as you can see I am using cifs as my server does not support nfs shares. I still have to mount my TvShow folders as well but once I figure this part out it may get easier.

 
 rgds,

 Dave

---

### Post by rodercot on 2009-04-13
Anyone have any ideas here. Even an alternative method at this point I am ready to try anything.

 Thanks,

 Dave

---

### Post by nickrout on 2009-04-14
The shares need to appear at exactly the same point in the filesystem n each backend and frontend.

So set up the mounts identically in /etc/fstab on each machine.

If you mount them on your backend and then mount your backend on your frontends then the file is going to go through the network twice - once from tower to BE and once from BE to FE.

---

### Post by rodercot on 2009-04-14
> **nickrout said:**
> The shares need to appear at exactly the same point in the filesystem n each backend and frontend.

So set up the mounts identically in /etc/fstab on each machine.

If you mount them on your backend and then mount your backend on your frontends then the file is going to go through the network twice - once from tower to BE and once from BE to FE.

 If that is the case, and my backend is headless, and I do not use a frontend on that machine at all, do I even need to mount them there at all and just mount them on the front ends only.
 
 The other issue is the symlinks, can I in Some way mount all the shared folders as one symlink or do I have to list them ALL in Mythvideo as separate mounts.

 Thanks,

 Dave

---

### Post by rodercot on 2009-04-14
I think I will just stick with xbmc as a link of the mainmenu, setting up mythvideo is just way to much work in comparsion to xbmc's video libraries.

 I think that mythvideo needs a lot of work to make it way more user friendly than it is. Even LMCE makes this less work. I have a ton of movies in those folders and to have to reset them all is way to much work to do again, I have NFO's in every directory for every movie with the imdb numbers in each nfo, this should be automatic and it seems to be almost ancient with mythvideo.

 I did get it working with a couple of mounts and after seeing the amount of work needed made up my mind.

 Thanks for the help.

 Dave

---

### Post by newlinux on 2009-04-14
It was nothing more than mounting each network share on each *frontend* machine and then listing : separated list of directories in mythvideo and that was that. There are bulk scanners that will read nfo files and look up tv show information, etc.  (there are a number of them- they run commandline, but you only have to run them once, and then maintain with new videos), but your are right, none are as easily integrated as XBMCs. But having the videos available on each frontend and running one of the bulk scanners for me was just as easy as setting them up in XBMC, once the directories are properly mounted.

You can use symlinks if you want, they have to be setup the same way on all the frontends machines. But if what you want to do is just have a number of directories available in myth you are probably better off just listing all the directories (separated by a colon).

A couple of options for bulk metadata import:
[http://code.google.com/p/mythvideo-scanner/](http://code.google.com/p/mythvideo-scanner/) (this is the one I primarily use now, but I've used quite a few others).

[http://ubuntuforums.org/showthread.php?t=1061733](http://ubuntuforums.org/showthread.php?t=1061733)
It can use .nfo files...

XBMC overall to me is better for video libraries, but mythvideo does have some features XBMC doesn't have (or I haven't found them in XBMC) like direct seeking, and shared bookmarks across multiple frontends.

---

### Post by joshoekstra on 2009-04-14
I use NFS-mounts and under ubuntu they're pretty much easy to set-up:

in /etc/exports you define your exported shares:
```
/share/movies   192.168.1.1/255.255.255.0(rw,async) 
```
On the frontend you can use automount:
/etc/auto.master:
```
/share /etc/auto.share ## the file which holds info about your shares
```
then /etc/auto.share:
```
movies 192.168.1.1:/share/movies ##192.168.1.1 is the MBE
```

The package automount then mounts the directory on the local filesystem of your fontend on /share/movies.
You could also use fstab, but I found that automount behaves in a nicer way than with fixed mounts when the connection gets lost(switch reboot, MBE reboot).

Hope it helps :)

---

