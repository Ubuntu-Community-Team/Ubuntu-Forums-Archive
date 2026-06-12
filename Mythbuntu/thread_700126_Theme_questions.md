---
title: "Theme questions"
date: 2008-02-18
forum: Mythbuntu
---

### Post by Caps18 on 2008-02-18
This is a pretty minor thing, but it would be cool if I could fix these two things.

The first question is when I go to the videos I have and look at them using the Gallery view, there are these yellow folders behind each movie poster. Is there a way to remove these in the theme easily, or is there a setting someplace to do it?

The second thing is I was wondering if there is a way to prevent the OSD menus from fading away? For some reason, my system has a problem with frames being dropped for the few seconds while it is happening.

Thanks.

---

### Post by Caps18 on 2008-02-18
This question was answered on the MythTV forum.  I haven't tried them out yet, but it sounds like they should work.

[http://www.mythtvtalk.com/forum/viewtopic.php?p=28866#28866](http://www.mythtvtalk.com/forum/viewtopic.php?p=28866#28866)

> It's easy to stop the OSD themes being 'animated' just by editing the osd.xml file.

Make <fadeaway> 0 and <fademovement> 0,0 throughout the osd.xml file (there are likely to be more than one instance).

In 0.21 it'll be possible to do that just by editing a playback profile.

As for the horrbile yellow/orange folder images - you can certainly change them but I wouldn't recommend removing them since they're needed to highlight the gallery item selected.

Copy your own files into the root directory of a theme called mv_gallery_back_reg.png and mv_gallery_back_sel.png - The _sel image is the one used to highlight a selected item.

Likewise there are mv_gallery_folder_reg.png and mv_gallery_folder_sel.png files which are used for representing directories.

Oh and lastly there's mv_gallery_dir_up.png which is the 'up one dir level' icon.

It kinda sucks that the theme is supposed to define all images & fonts but some are still hard-coded.

---

