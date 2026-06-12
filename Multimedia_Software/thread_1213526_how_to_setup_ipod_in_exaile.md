---
title: "how to setup ipod in exaile"
date: 2009-07-14
forum: Multimedia Software
---

### Post by sandman92 on 2009-07-14
can some one guide me through the steps for setting up my ipod in exaile in ubuntu 9.04

---

### Post by addiebk on 2009-07-28
Step One: Find a good friend who has Windows and iTunes, plug your iPod into their computer, open iTunes, and name the iPod, etc.  The first time the iPod is plugged into a computer, it will be formatted to either FAT32 (Windows) or something much less useful (Mac).  You want it in FAT32, because Linux can't read that weird Mac voodoo formatting stuff.

Step Two: Edit --> Plugins
Find the iPod Device Driver plugin and install it.  With your iPod connected to your computer, in the "installed plugins" tab, click "Configure." In the "Mount Point" drop down box, select your iPod.  It should be right there in the menu, but if it's not, you can find it in /media.

Step Three:  You should have a new tab in Exaile, right below "Radio".  It should be called "Devices".  Click on that tab.  From the drop-down menu, select iPod Device Driver, and click on the plug icon, so that it "plugs in".  You should see your iPod available.

Step Four:  Click and drag songs that you want onto your iPod's name.  You'll see a dialogue "Transfer Que".  Once you have all of the songs that you want on your iPod in the Transfer Que, click on the "Transfer" button, and it will all get copied over.

In theory, this should work.  It doesn't always, though.
If you have trouble with the Transfer step (Exaile says that it successfully transfers, though you have no new music on your iPod), you are not alone.  Some people just haven't gotten this to work yet.  Try a different media player until the Exaile team gets it fixed.  In the meantime, you can help by adding your experience to the bug report: [https://bugs.launchpad.net/exaile/+bug/179410](https://bugs.launchpad.net/exaile/+bug/179410)

---

