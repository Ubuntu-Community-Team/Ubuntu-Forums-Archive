---
title: "Adobe Digital Editions refuses to recognize Nook Color"
date: 2011-09-13
forum: Multimedia Software
---

### Post by siren625 on 2011-09-13
Hello all,

First, if this is in the wrong place, my apologies and feel free to move it.

Now, to the fun stuff... I recently bought a Nook Color and up until a couple days ago I haven't had a problem with it. Unfortunately though, I bought it for school and could only find a book I need with DRM and this has proven to be quite the obstacle and has left me pulling my hair out...

It all began with the Adobe Digital Editions software... Finally found an ebook copy to purchase, and it sent it to me in *.acsm format so,

Begin internet digging >> Find out I need ADE. 
Dig >> Install WINE >> Install ADE
Authorize ADE >> .acsm still won't work
Dig >> Install updated version of ADE >> Book works! Huzzah!

Being the "try this first and ask questions later" type (bad habit, I know) I open Calibre, load my new book onto the NC, and... No luck. It attempts to open it, but instead pops up with "Error: User not activated" and so...

Resume digging >> Find multiple sites that insist that [these directions]("http://www.hooverlibrary.org/node/1132"), or some variations of them, will solve my problem. >> Follow directions >> Failure.
Dig, find out that it's some sort of registration thing >> Change email address on Nook to match the one used to register ADE. Nothing.
Save everything on Nook and reset back to new, reregister/activate with new updated info to match ADE, follow instructions from the webz. Nada.

Commence searching >> Find out there's a problem with WINE recognizing USB connections. Install Crossover, remove ADE, install new fresh copy of ADE with Crossover. Reset Nook again to factory settings, because at this point, why not? Register Nook again with fancy new settings, authorize ADE with the same settings... 

Nothing.

Since then, I have begun my own trial and error. Plug Nook in, start ADE... Start ADE, plug Nook in... Start ADE, plug Nook in, close and restart ADE... I have been banging my head against the wall in frustration over this. I even went so far as to delete virtually any Nook/PC file that the letters 'ADE' in them, in hopes that it would fix the problem. Every Adobe folder/file has been trashed/reloaded/fixed/etc and all to no avail. I have a sinking feeling that I'm missing something painfully obvious, but I can't figure out what it could possibly be.

I can view the book fine within ADE itself, I just can't seem to get it over to the Nook. Everything I've read says that ADE will automatically begin some sort of prompts in order to authorize the Nook for content, however I've never seen anything like that. Curiously enough though, every time I have the Nook mounted and then run ADE (or vice-versa) the "problem" file (.adobe-digital-editions) mysteriously shows back up on the Nook. 

Also, I'm not sure if it's relevant, but when I connect it to my laptop it shows up with two drives in the file manager, only one is completely inaccessible. I don't have the slightest idea what that means and it could be irrelevant, but better safe than sorry.

If anyone out there has had a similar problem or can shed some light on this, I'd greatly appreciate it. I'm about to dig out an old windows vista installer and try and dual boot into that if I can't figure this out, though I really would prefer not to have to gunk up my new hard drive with it [-( I know this is tl;dr territory, so apologies for that as well.

Thanks ahead of time though to anyone who can help!



Nook Color: 1.2.0
ADE: 1.7.2.1131
OS: LinuxMint 10

---

### Post by Kantis on 2011-11-27
A bit late, but I ran into a similar problem with my Cybook Opus and Wine 1.2.2 on Ubuntu 10.04. I found the solution in [http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545](http://appdb.winehq.org/objectManager.php?sClass=version&iId=15545)
where the user David Egts writes: 

"What I do is plug in my nook so Linux mounts it as /media/nook. Then I run winecfg and go to the Devices tab. I'll see drive E: mapped to /media/nook. Then I'll select E: and then Show Advanced and set the Type to Floppy disk and hit Apply and *not* OK. If you do OK, the winecfg window will be dismissed and the settings presumably lost and not written to disk. Hitting Apply will keep the winecfg window in place and the settings presumably in memory. With the winecfg window up with the right setting for E: as a Floppy disk, I then run ADE and the nook will show up every time."

Works for me!:D

---

### Post by reader4 on 2011-12-20
I got ADE to work with my nook a while back by this same method.  However, after upgrading to the new nook firmware (1.4) ADE in WINE crashes if the nook is connected.  I removed the old ADE settings/folders, but that did not help.  Are you still running the old firmware, or have you seen this problem before?  Even my XP VM would not read the nook due to "I/O errors"...

---

