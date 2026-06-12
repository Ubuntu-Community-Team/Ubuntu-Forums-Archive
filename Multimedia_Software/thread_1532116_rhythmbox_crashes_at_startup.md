---
title: "rhythmbox crashes at startup"
date: 2010-07-16
forum: Multimedia Software
---

### Post by buddiemac on 2010-07-16
I am having some trouble with RhythmBox. It runs fine until I install  the package (Synaptics) Rhythmbox plugins 0.12.8-0. 

After I install this package and then open RhythmBox, the applications  opens for a few seconds and then closes (terminates). I get a segmentation fault.

I tried reinstalling but this does not help. 

From previous posts, others were also obtaining segmentation faults,  others had success with uninstalling the rhythmbox-ubuntuone-music-store  package. I do not have this installed on my system. My problem is  related with the plugins package.

If I run rhythmbox from the command line in sudo mode it starts without crashing but with a  warning:

Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name


 But when I select one of the plugin sources it then terminates and closes down.

Configuration is Ubuntu Lucid, 64 bit OS

---

### Post by buddiemac on 2010-07-16
The problem of crashing at startup (fragmentation fault) disappeared. The only change in the system that I can recall is a HIDPOINT software update.  Do not believe there are any dependency between this two apps.

Still crashes when some of the plugins are selected - just removed these plugins from the configuration.

---

### Post by Dsafire on 2010-08-13
To confirm, I was having the exact same problem. Other threads have mentioned the U1MS plugin, but that wasnt it, since I didnt have that on my system at all. 

At startup Rhythmbox gave me a couple of seconds before it crashed, so I dove in and disabled all of the plugins. I then reinstalled the restricted extras package out of sheer paranoia. Started up like a champ and rescanned my library. 

I'll add them back one by one to see if I can figure out where the issue was, but it's veddy veddy late now. I'll try to remember to update the post when/if I find a culprit.

---

### Post by Dsafire on 2010-08-13
Update: got it, It was the Last.FM plugin.

---

### Post by Fangorn59 on 2010-09-08
Same problem - Rhythmbox window opened and immediately closed.  Used Synaptic Package Manager to remove all rhythmbox entries. Re-installed main program on its own and checked it was working, then added one at a time -plugins, -plugin-cdrecorder, -ubuntuone-music-store and radio-browser. I had the rhythmbox app open when I installed the plugins - then closed and re-started after each one to make sure it was working.  Everything going OK now.

---

### Post by StewD on 2010-11-09
I've just reinstalled Ubuntu 10.10 and had the same problem of RhythmBox closing within a second of opening.

I've resolved by running Synaptic Package Manager from the System / Administration menu.

Searching for Rhythmbox via the QuickSearch box, and then selecting the Ubuntu One Music Store Rhythmbox plugin for removal.

Applied the changes (press the big Apply button) and RhythmBox now stays open.

Hope that helps someone else!

---

### Post by sparky333 on 2011-01-23
StewD...
I did the same thing you did and it fixed my "segfault at 0" problem at first opening. I'm running Lucid.

Thanks for your info!

---

