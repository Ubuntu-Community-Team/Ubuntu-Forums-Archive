---
title: "Weird Creative Zen Problems"
date: 2011-02-22
forum: Multimedia Software
---

### Post by ckwhiz on 2011-02-22
OK, I found this odd.  Many of the answers I looked at on the forums here do not pertain to my particular problem, or they don't work thus far.  If I missed it, please direct me in that direction. :)

First of all, my Creative Zen is at the very least about four to five years old.  It's the basic old one.  It's a trooper; it's been through extreme heat, extreme cold, and soaked once and it's still kicking.  I've never upgraded the firmware before.  I am running Ubuntu Lucid 10.04, kernel 2.6.32-38-generic, and Gnome 2.30.2.  If it has anything to do with it, I am running this off of an ECS Motherboard, an AMD Phenom II x4 925, four gigs of DDR3 RAM, with integrated video and sound with a nVIDIA GeForce 9500 GT.

Whenever I plug it in, Ubuntu recognizes it seemingly perfectly.  Little box pops up and asks what program I would like to open with it. I can access it as a mass storage device.  I can add and delete music, but this messes with the playlists on the device (when deleting).  These playlists were created using the proprietary software in Windows.  My ultimate goal is to be able to create and delete playlists.  I haven't changed a playlist in over a year and it's starting to get redundant, to say the least.

I have installed both KZenExplorer and Gnomad2.  Sometimes, about 1 out of 5 times, it is recognized in Rhythmbox as My Zen.  Usually it's Unknown Device and I cannot see any music.  It is recognized in Amarok, but I am unable to create a new playlist - I can only play the music from the device.  I have tried to run both as root, and am getting many error messages.  Here is what happens:

This happens when the Creative Zen is mounted in nautilus:
> caitlin@caitlin-desktop:~$ sudo gnomad2 
Device 0 (VID=041e and PID=4157) is a Creative ZEN.
Queried Creative ZEN
Segmentation fault
This is what happens when it is not mounted:
> caitlin@caitlin-desktop:~$ sudo gnomad2 
Device 0 (VID=041e and PID=4157) is a Creative ZEN.
Queried Creative ZEN
Bus error
Gnomad2 pops up for a second, saying it is searching for devices, and then shuts down.

This happens whether or not Creative Zen is mounted:
> caitlin@caitlin-desktop:~$ sudo kzenexplorer 
Error: "/tmp/kde-caitlinY7sRol" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-caitlinOKc9YK" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-caitlinOKc9YK" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-caitlinY7sRol" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-caitlin" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/tmp/kde-caitlinY7sRol" is owned by uid 1000 instead of uid 0.
DCOP Cleaning up dead connections.
Error: "/var/tmp/kdecache-caitlin" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-caitlin" is owned by uid 1000 instead of uid 0.
caitlin@caitlin-desktop:~$ kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
Error: "/tmp/kde-caitlinY7sRol" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/lib/libkdeinit4_kconf_update.so
KZenExplorer's splash screen then pops up for a second and it says "Could not find any jukeboxes!"

I find this increasingly odd, because all of this is happening although Amarok and Rhythmbox can sometimes 'see' it, and Nautilus has no problems with it.

I would just edit the playlist (.zpl) files in gEdit, but I do not want to mess up the path of the files and have the playlist not work.  Am I missing something here?  

Thanks in advance!!

---

### Post by TVTrukChik on 2011-02-22
I have noticed some odd behavior with my Creative Zen also.  It seems like it is mounting and then unmounting itself 5 or 6 times in a row when I first plug it in.  Then it settles down and stays mounted.  

I have found that if I let it settle down before starting Banshee, I can then get it to sync up just fine.  If Banshee is already running when I plug in the Zen, or if I start it right away, I get all sorts of weird things happening... Banshee will see 4 or 5 different Zens, or want to delete and re-sync half my library, or just not talk to it at all sometimes.  

What happens if you wait a minute or so before starting any of the programs?

---

### Post by ckwhiz on 2011-02-22
I did try that.  I usually just hit cancel and try the others.  I tried rebooting in between as well, and after that waited a few minutes.  I let Rhythmbox run for ten minutes to see if it would search and find the Zen (whenever it comes up as "Unknown Device" instead of "My Zen").  I was playing with it for about an hour or so.

Does Banshee allow you to create playlists that can be played on the Zen?

I haven't run into problems with Ubuntu mounting and unmounting the Zen.  The only problem is once it randomly shut off while I was trying things, but my Zen has been doing that randomly, about once a month or so, since it got soaked.  Using the reset button fixes that.


PS I am the queen of run-on sentences.

---

### Post by TVTrukChik on 2011-02-24
I've never tried copying a playlist from Banshee to the Zen.  Usually when I use the Zen, I just put on random and let it go.

---

### Post by jaaacob on 2011-03-21
I have tried Qlix, Rhythmbox, Mediamonkey (via wine) and even installing old libmtp8 files to install Gnomad2 on my meerkat. Nothing is working! I've tried everything you guys have said and it's an absolute pain. 
And ckwhiz I know what you mean about this original Zen being a trouper, looks like it's finally met it's match...

---

### Post by eddier on 2011-04-05
Having just installed PCLinuxOS Xfce on my spare PC imagine my surprise when Gnomad2 and libmtp8 both worked!

My creative Zen was seen and synced,no problem. Furthermore the fonts in Gnomad2 were fixed.

Gnomad was version 2.9.4 and libmtp8 was version 1.0.3-2pclinux.

eddie

---

