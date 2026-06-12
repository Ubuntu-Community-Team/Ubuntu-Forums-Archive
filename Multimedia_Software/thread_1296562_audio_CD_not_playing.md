---
title: "audio CD not playing"
date: 2009-10-20
forum: Multimedia Software
---

### Post by matthewds74 on 2009-10-20
**audio CD not playing** 			
 			 			 		   		 		 		Please help

here is the problem......

error message.
"could not open location 'cdda://sr0/'

failed to execute child process " sound
juicer" (No such file or directory)

please advice with a step by step guide on what I need to do......


All help will be greatly apreciated...

Hope to hear from some one soon..
matt

---

### Post by jmate24 on 2009-10-20
what version of ubuntu studio are you using? because if it is the beta 9.10 then there is no sound whatsoever because pulsecore9 is no longer supported and is obsolete therefore if this is the case then you will have to wait 8-9 days for the pulsecore9 to resolve certain dependencies with both your sound card, CD/DVD drive, and your earphone and mic jacks. so until then you'll just have to wait it out or you can down grade to 9.04. but if this is not the case then read the Comprehensive Sound Solutions Guide at the top of the Ubuntu Forums>Main Support Categories>Multimedia & Video.

jmate24--

---

### Post by matthewds74 on 2009-10-21
> **matthewds74 said:**
> **audio CD not playing**             
                                                                Please help

here is the problem......

error message.
"could not open location 'cdda://sr0/'

failed to execute child process " sound
juicer" (No such file or directory)

These errors are occuring on Jaunty version 9.04.

The base Ubuntu Desktop has been upgrade with all of the studio programs so that I would have openoffice installed along with other general purpose programs.


please advice with a step by step guide on what I need to do......



All help will be greatly apreciated...

Hope to hear from some one soon..
matt

..

---

### Post by tangocharlietango on 2011-02-14
I´ve solved this simply by typing "sudo apt-get install sound juicer" ):P

---

### Post by Tonyr63 on 2011-03-05
Yes this will let you play with Sound juicer however there are still problems as Rythembox still will not play.

What is causing this widespread reported problem?

---

### Post by CryNGRoad on 2011-03-07
on my system (Ubuntu 10.10) there is a key in **gconf-editor**:

[B]/desktop/gnome/url-handlers/cdda/command
[/B] 
with the value "**sound-juicer %s**"

Changing this to "**nautilus %s**" causes nautilus to open instead of the sound-juicer error.
Changing it to "**rhythmbox %s**" causes rhythmbox to open, with the cd selected, but it does not begin playing automatically.

I  imagine you can set this key to the program of your choice, *though the  "%s" parameter will most likely need to be changed depending on the  program.* 

Step by step:

[LIST=1]
[*]Start gconf-editor (press ALT+F2, type gconf-editor, then click Run)
[*]In the *left pane* of gconf-editor navigate to "**/desktop/gnome/url-handlers/cdda/**"
[*]In  the *right pane*, double-click **command**, then change "*sound-juicer %s*" to  the program you would like to run. (e.g. "nautilus %s")
[*]The change is immediate; Try inserting/opening an audio cd now.
[/LIST]
NOTE 1: Ensure the "*enabled*" key is checked, or you'll get another cryptic error.
NOTE 2: The "%s" is replaced with "cdda://<yourDeviceNode>/" when run ("cdda://sr0/" on mine), which may not be correct syntax for most programs other than nautilus/rhythmbox.

---

### Post by CryNGRoad on 2011-03-07
> **beendarzi said:**
> You can burn mp3's as an audio cd...

One of us misunderstood matthewds74's problem. If it was me, I apologize.

---

