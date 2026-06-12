---
title: "Sirius Radio Integration with Mythbuntu"
date: 2008-12-20
forum: Mythbuntu
---

### Post by dmfrey on 2008-12-20
I wanted to throw this out there to the mythbuntu community.

I recently updated the following MythTV Wiki: [http://www.mythtv.org/wiki/index.php/Integrate_Sirius](http://www.mythtv.org/wiki/index.php/Integrate_Sirius)

I recently performed this install on my box and it is working great, but I didn't want to have to code all those menus by hand.  So I decided to try my hand at writing some python to generate the menus for me.

The script I attached goes out to the Sirius Channel Listing and scraps the data to produce a hierarchy of menus based on category and genre.  The python is not pretty(I am not a python programmer and there are probably better ways to do this out there :) ), but it is a nice repeatable script that can go out an update these files whenever their lineup changes.

As for the rest of the installation, some packages are not needed or named differently than what the instructions state. For instance, you would need to change notify-python to python-notify and wxPython is now python-wxversion.

I hope it helps others out.

---

