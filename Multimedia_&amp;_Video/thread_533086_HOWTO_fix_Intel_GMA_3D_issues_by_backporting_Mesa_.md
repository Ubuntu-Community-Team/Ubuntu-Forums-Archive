---
title: "HOWTO fix Intel GMA 3D issues by backporting Mesa 7.01"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by zyth on 2007-08-23
In some games and 3D applications (notably for me, Neverwinter Nights), the Intel GMA 950 has graphical errors that are caused by a bug in the version of Mesa that ships with Feisty.  This bug is resolved in version 7.01 of Mesa, but unfortunately that version is only available in 7.10 Gutsy Gibbon.  Therefore, the solution is to backport it.  This would normally be a complicated process, however it is greatly simplified by the use of a program called **prevu**

First, add the Gutsy source repos to your sources.list (replacing ca.archive.ubuntu.com with your appropriate local repo):
> 
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse


Then update apt and install prevu from the repositories
> 
sudo apt-get update && sudo apt-get install prevu


Then initialize prevu's build environment:
> 
sudo prevu-init

You will see many things scroll by for a while.  Prevu will ask you if you want to have your directory that will contain the newly built debs added to your sources.list.  I recommend selecting 'Yes' to this so that you can just do an apt-get upgrade later to update Mesa to the new version.

Now, you need to build the Mesa packages
> 
prevu libgl1-mesa-dri

This will tell prevu to build the libgl1-mesa-dri package and its dependancies.  You will see many packages being downloaded and installed, followed by a whole lot of compiling.  Sit back and grab a coffee, because this will take a while.  

After this finishes, you will have a bunch of shiny new debs in /var/cache/prevu/feisty-debs.  If you selected 'Yes' to having prevu add a line to your sources.list earlier, all you need to do now is:
> 
sudo apt-get update && sudo apt-get upgrade
 
And voila!  You now have Mesa 7.01 built and installed!  If you didn't choose to have a line put in your sources.list, you will need to manually upgrade to the new versions of your appropriate Mesa packages (Just check in synaptic to see which are already installed by searching for Mesa and upgrade the appropriate ones).

Restart X, and away you go.

---

### Post by pike2k on 2007-08-26
Thanks for this excellent guide!

But I still have graphics issues with my GM945/GMA950 with 3d overlays. Which intel driver do you recommend ?

Regards

---

### Post by zyth on 2007-08-26
Make sure you're using the xorg-server-intel driver, and not the old i810 driver.  It is far better, and you won't need any kludgy hacks like 915resolution either.

---

### Post by pike2k on 2007-08-27
the last post in this bugreport describes it pretty well: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/73698]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/73698")

> This only appears to affect GL applications, such as Blender.
Dragging windows containing GL output also produces artifacts.



I was using the i810 driver so I'll see if changing to the intel driver has any positive effects

edit: no difference with newer intel driver

---

### Post by zyth on 2007-08-29
I've noticed some of the GL window issues as well, I use x11 for mplayer's video out, because XV doesn't work properly, nor does GL, and for 3D games, I use fusion-icon to turn off compiz-fusion.  I don' t know any way around that, unfortunately.

---

