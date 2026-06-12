---
title: "program to watch iso dvds?"
date: 2010-01-21
forum: Multimedia Software
---

### Post by axima on 2010-01-21
in windows i use daemon tools and media player home cinema to watch dvds i have ripped from the disc, how would i do the same in linux? thanks!

---

### Post by nmaster on 2010-01-21
To mount the image:

cd /path/to/the/iso
mkdir mnt
sudo mount -o loop NameOfDVDFile.iso mnt



To unmount the image

cd /path/to/the/iso
sudo umount mnt





you should get an icon on your desktop for the disc.  you can right click and choose an app to play it with.  i like vlc.

sudo apt-get install vlc

---

### Post by Darce on 2010-01-21
Right click on the iso and select 'open with archive mounter'
Browse to your newly mounted dvd image and play with your favourite media player

---

### Post by axima on 2010-01-21
> **Darce said:**
> Right click on the iso and select 'open with archive mounter'
Browse to your newly mounted dvd image and play with your favourite media player

part1: done
i can't get it to work with movie player, there are two options, open and open location. the first one just go straight into the dvd so i get the audiots and videots files, not sure what to make of those. the second option pops up a window with a blank box, not sure what to type in. 

isn't there any option to play the disc that is mounted, like in MS windows?

---

### Post by zami on 2010-01-21
Are you saying you just have a .iso file on your computer somewhere, or on a disk?

I just play them straight off my computer with VLC - works great!  Just right click on the file, and select "Open with VLC", or "Open with Other" and manually select VLC (or type in, vlc).

If you don't have VLC, you can get it through
System > Administration > Synaptic Package Manager, and search for VLC

I'm sure other players work as well, but VLC never fails me or asks for more dependencies or codecs.

And I apologise in advance if I'm misunderstanding your question.

-zami

---

### Post by axima on 2010-01-21
they are an iso file on disk. i prefer not to have two media players, but i will give vlc a try later, is there anyway to get things going with movie player?

---

### Post by LuridCinema on 2010-01-21
Once you see the power of VLC .. it will become your primary video player.. promise

---

### Post by zami on 2010-01-21
> **LuridCinema said:**
> Once you see the power of VLC .. it will become your primary video player.. promise
Very true!!  My first thoughts about VLC were of how... well ugly, the player is.  But it just never fails me, and once my movie is playing, I quit caring what the movie looks like. 

Anyhow, to the OP, your preferred player might work the same way.  Just try right-clicking on the file, and see if the option comes up to play it with your preferred media player.  

I just checked, and my .isos also open with Totem Movie Player (gstreamer - xine variants probably work just fine too).  

If you open it with Movie Player and get errors, or it just "does nothing", you might want to go through this guide
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
to be sure you have the correct codecs installed.

Good luck!

-zami

---

### Post by nmaster on 2010-01-23
if you have problems with the gui archive mounter, just mount the image from the command line.  

and definitely use vlc.  its very good.

---

### Post by axima on 2010-01-23
switched over to vlc, everything plays fine. i really liked movieplayer, reminds me of mpc-hc on windows. vlc is great too, i hope it will become the default media player in 10.04

---

