---
title: "Shotwell - updated 12 to 14 but can't now launch it"
date: 2013-05-09
forum: Multimedia Software
---

### Post by Ace..... on 2013-05-09
Shotwell was failing to display videos, so I checked their site and discovered, my version was out of date (I always thought it auto updated like most packages on ubuntu).

I entered the following 3 commands:

$ sudo add-apt-repository ppa:yorba/ppa
$ sudo apt-get update
$ sudo apt-get install shotwell

Note I didn't remove the earlier version, cos the Yorba site did not instruct me to do do so.

Clicking the shotwell icon does not launch the app.
Typing shotwell, or./shotwell in terminal doesn't work.

The former producing this: shotwell: error while loading shared libraries: libgexiv2.so.2: cannot open shared object file: No such file or directory

I ran $ sudo apt-get install shotwell again..... terminal reported:
shotwell is already the newest version

Tried launching from dash, but this doesn't work.
Loaded software centre, and this informs me shotwell is installed, offering the option to remove it.

What is my best course of action?

Edit: tried inserting an SD card with pics, to get the 'load shotwell' command.
Clicked the command but only got a lot of hard disk activity for a period.

Edit: I since decided to remove shotwell thru software center.
I then re-installed, but no joy.
Typing shotwell in terminal still produces this:  shotwell: error while loading shared libraries: libgexiv2.so.2: cannot open shared object file: No such file or directory


:confused:

---

### Post by eric-yorba on 2013-05-09
> **Ace..... said:**
> (I always thought it auto updated like most packages on ubuntu).

For the most part, Canonical only provides bug fixes, not entirely new versions of software.  For that you either have to update the package from a PPA, build it from source, or update to the next Ubuntu release.


>  Typing shotwell in terminal still produces this:  shotwell: error while loading shared libraries: libgexiv2.so.2: cannot open shared object file: No such file or directory

Try reinstalling Gexiv2, I bet that will fix it.

---

### Post by Ace..... on 2013-05-09
> **eric-yorba said:**
> 
Try reinstalling Gexiv2, I bet that will fix it.

Thanks Eric.

I searched software centre for Gevix2.
It indicates that I have : libgexiv2-1 0.4.1-1build1  installed.

I'll remove it, and then re-install it.

Here goes.

interesting that it stated that 'shotwell must first be removed'.

I wonder if shotwell auto loads this library,
or which I load first, shotwell or the library.

---

### Post by Ace..... on 2013-05-09
I installed the library first, and then shotwell.

Shotwell from software centre was a two stage install.
1st stage downloaded, and then configured.
This was taking some time so I left it.

When I returned, the software center was showing the shotwell namer and another install button, which I clicked.
This finished the installation, and I could load Shotwell.

So thanks for your advice eric :P

I do now have a strangish situation..... perhaps due to my own fault...... perhaps it's normal.

I had simply copied .shotwell dir to a temp dir, as a bakup before removing shotwell..... I don't know if this has caused a problem.

Upon opening shotwell 14, I noted that the vids were still not displaying in their appropriate dated 'event' folders, even though the files are actually stored in the date named folders.
I also noted a folder dated 1947, displaying some of the missing vids.

However, I noticed on the dir tree a folder called 'folders'.
Within this is nested 'again' my date named folders, but without 1947.

In this set of folders, all the recently taken videos are presented correctly according to their date.
However, there is a 1970 01/01 folder containing a whole load of vids taken a few years ago.
Each of their actual file dates reflect correctly when the vids were taken.
Perhaps the camera used did not store the file data other than as a normal file.
It would seem that Shotwell has not fallen back to use the file date, and has simply lumped them all in 1970 01/01.

It's not the end of the world..... 59 files that I guess I can manually move into appropriate dated folders.

[B]Question:
Would manually moving these files be the appropriate fix, or must I create new date information for each file?[/B]

**Dir tree by 'events' - is it normal it doesn't display vids (in which case I guess we'll simply use dir tree by dated folders to view our photos and vids)?**

---

