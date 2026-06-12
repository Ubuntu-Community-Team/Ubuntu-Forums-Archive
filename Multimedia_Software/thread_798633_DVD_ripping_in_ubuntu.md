---
title: "DVD ripping in ubuntu ?"
date: 2008-05-18
forum: Multimedia Software
---

### Post by MrGando on 2008-05-18
Hi , I use MacOSX as my primary System. However I do have a file server hosted in my ubuntu 7.04 Box. ( Haven't updated to 7.10 because of fear of screwing my netatalk setup or something ). 

Well, the point is that on Mac I use MacTheRipper to rip DVD's ( It creates a Folder of the size of the DVD that has all the Disk Content ) . Is there something like this for Ubuntu ? 

I have just found software that "Rips" ( creates a .avi ) from a DVD, and I don't really need that. :(

Could someone help me out here ? :)


Thanks a lot.

---

### Post by mc4man on 2008-05-18
you could use vobcopy, though the ver. in feisty repo is old. You can get newer versions here [http://vobcopy.org/](http://vobcopy.org/) and compile (quite simple - takes a min. or two)
typical command vobcopy -v -m -F 16 /media/cdrom0  (remove -F 16 for older feisty ver.)
Also you can use k9copy to rip to folder (set in output). Before ripping go to settings -> configure...-> dvd and adjust target size higher than dvd to avoid transcoding. With k9 you have opportunity to remove unwanted audio,sub streams, or do movie only, ect.

edit: your only issue with either app would be with structure protected titles, k9 can handle alot of them, the newer ver. 1.2.3 would be better though again not avail. in feisty. (you can compile, not that hard, if wanted i'll hook you up with a how to)
vobcopy can also deal with sp, but you need to modify the source and have external tools the repair the mis-structure.

---

### Post by papafreebird on 2008-05-18
> **MrGando said:**
> 
Well, the point is that on Mac I use MacTheRipper to rip DVD's ( It creates a Folder of the size of the DVD that has all the Disk Content ) . Is there something like this for Ubuntu ? 


The easiest way I have found to accomplish that is to use [dvdfabhddecrypter](http://www.dvdfab.com/free.htm) through wine.  Now I know some people only want to use nix software but I don't know of any nix software that does the job as easy as this does.  Just use the free version of dvdfabhddecrypter (the payware is not necessarry just to get the dvd to your hard drive).

---

