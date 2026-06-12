---
title: "No blank CD detected in drive by buring programs"
date: 2011-05-21
forum: Multimedia Software
---

### Post by nbolds442 on 2011-05-21
I am using both K3b and Basero to try and burn a DVD Iso.  Both programs show that I need to insert blank media in the drive, however the disk utility shows that I have an unformatted disk in the DVD-RAM drive. Using Ubuntu 10.10 with wine installed.  I mention wine because I remember messing with it a while back to get a multi disk install to work and needing to mess around with mounting the disks in odd configurations however cant remember exactly what I did. (It was a late night)

---

### Post by mc4man on 2011-05-22
Don't think wine did anything though you may have...?
Seeing as though you have wine you could try ImgBurn - if you get the idea and your drive/media/iso image are  good should work just fine as things are now.

If so  -  (if not, then I don't bother much  with linux burners though K3B seems okay in general, don't know much about...
[URL="http://fileforum.betanews.com/detail/ImgBurn/1128426215/1"]
 Download here[/URL], then r. click on the .exe > properties > permissions > 'Allow exec...', then install using wine.

During install just click the defaults presented till screen 1 - uncheck the boxes, then finish. (if on natty unity I'd decline to run 'now', close out installer then use desktop icon, - otherwise either way.
Launcher will show up on desktop ready to go.

First time opening go - Tools > Settings > I/O and switch to 1st. choice - screen 2 (ASPI-WNASPI32.DLL

Your drive(s) then should be recognised - ImgBurn log (switch even if the drive was recognised

If you have an .iso ready then on main window just click 'Write Image File to Disc' and in burn window click on yellow folder to browse and select the .iso 
You can use the dropdown browse tree though keep in mind the default shown, "My Documents" is actually your home folder.

Also on burn window is the Settings box - defaults to max write for the media detected, (above box - will show supported write speeds ect. Leave or choose new speed, 
The default is also to verify. leave or uncheck
click burn - screen 3

If needing to create an iso first then whenever possible let ImgBurn create - particularly when or if doing a dual-layer - you want Imgburn to set the layer break, on dvd/blueray video burns you can preview and select the break from an available layer break screen.
( when burning dual-layer you give ImgBurn the created .mds as selected instead of iso, you'll get corrected if you don't. 

Lots of info if needed here of how to use, ect
[http://forum.imgburn.com/index.php?showforum=4](http://forum.imgburn.com/index.php?showforum=4)

Note - ImgBurn has extensive setting - the defaults are always good - be educated about any changes

---

### Post by nbolds442 on 2011-05-22
Solved--  Had a stack of bad media.

---

