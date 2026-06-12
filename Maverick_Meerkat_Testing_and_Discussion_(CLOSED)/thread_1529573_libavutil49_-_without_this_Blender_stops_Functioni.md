---
title: "libavutil49 - without this Blender stops Functioning"
date: 2010-07-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-07-12
Blender does not work without libavutil49 ..... 

Each time I do an upgrade Blender stops functioning ......

The solution that I use is below .... the question is how will other people know to do this

**aptitude install libavutil49**

```


root@keith-laptop:/home/keith# aptitude install libavutil49 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libavutil-extra-49 
The following NEW packages will be installed:
  libavutil49 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 93.3kB of archives. After unpacking 229kB will be used.
The following packages have unmet dependencies:
  libavutil-extra-49: Conflicts: libavutil49 but 4:0.5.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

Remove the following packages:
libavutil-extra-49

Leave the following dependencies unresolved:
imagination recommends libavutil-extra-49
Score is -441

Accept this solution? [Y/n/q/?] y
The following NEW packages will be installed:
  libavutil49 
The following packages will be REMOVED:
  libavutil-extra-49{a} 
0 packages upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 93.3kB of archives. After unpacking 143kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) lucid/main libavutil49 4:0.5.1-1ubuntu1 [93.3kB]
Fetched 93.3kB in 0s (140kB/s)
dpkg: libavutil-extra-49: dependency problems, but removing anyway as you requested:
 libmoon depends on libavutil49 (>= 4:0.5.1-1) | libavutil-extra-49 (>= 4:0.5.1-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
 xvidcap depends on libavutil49 (>= 4:0.5+svn20090706-3) | libavutil-extra-49 (>= 4:0.5+svn20090706-3); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
 blender depends on libavutil49 (>= 4:0.5.1-1) | libavutil-extra-49 (>= 4:0.5.1-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
 audacious-plugins depends on libavutil49 (>= 4:0.5.1-1) | libavutil-extra-49 (>= 4:0.5.1-1); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
 xjadeo depends on libavutil49 (>= 4:0.5+svn20090706-3) | libavutil-extra-49 (>= 4:0.5+svn20090706-3); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
 kino depends on libavutil49 (>= 4:0.5+svn20090706-3) | libavutil-extra-49 (>= 4:0.5+svn20090706-3); however:
  Package libavutil49 is not installed.
  Package libavutil-extra-49 is to be removed.
(Reading database ... 412863 files and directories currently installed.)
Removing libavutil-extra-49 ...
Selecting previously deselected package libavutil49.
(Reading database ... 412855 files and directories currently installed.)
Unpacking libavutil49 (from .../libavutil49_4%3a0.5.1-1ubuntu1_i386.deb) ...
Setting up libavutil49 (4:0.5.1-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

root@keith-laptop:/home/keith#


```Once its fixed properly we can all run Blender without the need for the above.

[B]What is the proper fix - is a fix in progress ? or does a Bug Report need to
be put in for it ?[/B]  
I have highlighted it once before [Blender Devede ]("http://ubuntuforums.org/showthread.php?t=1518275&highlight=blender+devede")

But I am worried now that it will **not be fixed properly** unless some other action is taken.

I agreed with the solution that was given there - but it was only a temporary fix.

It was only affecting **Devede** before - but now it is also affecting 

***[ imagination]("http://gtk-apps.org/content/show.php/Imagination?content=100045") ...... **(it recommends it ?)

---

### Post by 23dornot23d on 2010-08-02
Its interesting where this is now heading ...... To get Blender working I need to install libavutil49

Even more packages need to be removed to get Blender to work


```


root@keith-laptop:/home/keith# aptitude install libavutil49
The following NEW packages will be installed:
  libavutil49 
0 packages upgraded, 1 newly installed, 0 to remove and 240 not upgraded.
Need to get 93.3kB of archives. After unpacking 229kB will be used.
The following packages have unmet dependencies:
  libavutil-extra-49: Conflicts: libavutil49 but 4:0.5.1-1ubuntu1 is to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     devede                      
2)     libavutil-extra-49          



Accept this solution? [Y/n/q/?] Y
The following NEW packages will be installed:
  libavutil49 
The following packages will be REMOVED:
  devede{a} dvdauthor{u} libaudio2{u} libavutil-extra-49{a} 
  libdirectfb-1.2-9{u} libdvdnav4{u} libdvdread4{u} libenca0{u} 
  libiso9660-7{u} liblzo2-2{u} libmpcdec3{u} libpostproc-extra-51{u} 
  libsvga1{u} libts-0.0-0{u} libvcdinfo0{u} mencoder{u} mplayer{u} 
  tsconf{u} vcdimager{u} 
0 packages upgraded, 1 newly installed, 19 to remove and 237 not upgraded.
Need to get 93.3kB of archives. After unpacking 29.5MB will be freed.
Do you want to continue? [Y/n/?] Y



```

---

### Post by dino99 on 2010-08-02
might need to report

---

### Post by mc4man on 2010-08-02
> might need to report

It's a well known thing. 
What you are doing with the extra version of libavutil49 I'm not sure, the point of the temp workaround for devede was not to use it. (libavutil49-extra

libavutil49-extra is basically an empty package, no .so's are included, in other words -  worthless - other than satisfing the repo devede deps.

You shouldn't have to remove anything but devede to change to libavutil49, if you had modified devede as discussed then not even that.
(or if you did, you let it get updated back to repo version and libavutil49 was updated back to the extra version.

Aptitude is the wrong method here, use synaptic instead.
(though any package removed can be re-installed.

Or wait for these packages to get rebuilt (devede and blender

---

### Post by 23dornot23d on 2010-08-02
Ok cheers have now reported it as a [BUG]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/612643") 612643

Blender will not open without libavutil49 ...... and each time I do a fresh install of the system
I go through the same procedures each time ...... I am not sure if things should change
as we report things or not as this is my first time doing the testing.

Maybe patience is what I need - but its hard without some sort of feedback as to what is 
actually happening .......

out of 6 things that I have highlighted ........

6 things still need re-doing every time I try to do the testing ...... 

1
I never have sound working - so I do this ......
**gksudo gedit /etc/modprobe.****d/alsa-****base.conf**
 options snd-hda-intel model=auto

2
I still have to reset the volume levels - so I do this

gksudo gedit  /etc/pulse/default.pa . (do this) **# load-module module-device-restore** 


3
I still need to add libavutil49 to get Blender to fire up ..... so I do this

[B]aptitude install libavutil49

4
GRUB2 still does not work properly ...... so I use a Custom Menu

If I dont stop these two loading up ......  grub-common grub-pc
( * aptitude hold grub-common grub-pc ) or
I loose my MAIN GRUB2 menu and have to rebuild that too .....

[/B]5
Nautilus runs slowly unless I remove UbuntuOne ......
My workaround is to install thunar

6
Wizardpen does not work anymore ......
No solution yet - working on it .



And do not get me wrong I understand to suit every different setup - it must take some real
sorting out ..... I have thought about what works for me may stop someone else's working

So keep up the great work ..... the system rocks ..... I just want to help make it even better.

---

### Post by mc4man on 2010-08-02
> Maybe patience is what I need
Certainly, at some point devede and blender will be rebuilt to use the current ffmpeg (0.6

Your current issue is exactly the same as it was before and it's devede, not blender. Devede is making you install a non functional libavutil-extra-49, blender can use either but it needs libavutil to be functional to run.

If you had previously modified devede, than if re-installing maverick save the .deb and reuse.
(you could bump the version to devede_3.16.8-0ubuntu[COLOR="Blue"]2[/COLOR]_all.deb when modifing to prevent an update but allow the new version to be seen whenever it arrives.

---

### Post by 23dornot23d on 2010-08-02
> **mc4man said:**
> Certainly, at some point devede and blender will be rebuilt to use the current ffmpeg (0.6)


Cheers .... 
I will be more patient and the work around's do not bother me too much as long as I know that what I am reporting actually helps UBUNTU to do something positive down the road. 

Will keep my posts to a minimum now on subjects that re-occur.
Thanks again.

________________________________________________________________________________

keith@ubuntu:~$ uname -a
Linux ubuntu 2.6.35-14-generic #19-Ubuntu SMP Mon Aug 2 01:43:35 UTC 2010 i686 GNU/Linux
keith@ubuntu:~$ 


This has been sorted properly now with .... libavutil50 .........

---

