---
title: "Kino Video Filter &quot;Levels&quot; won't work"
date: 2008-06-12
forum: Multimedia Software
---

### Post by tigertom on 2008-06-12
Help, please.  I'm trying to correct the white balance on a video, part of which was shot indoors.  I can get the other video filters to work (make a section of the video black and white, or sepia, or jerky etc.) but the levels filter won't work.  I follow the instructions in the help file to set the white balance colour, but as soon as I start preview or start rendering, all the levels controls are returned to their defaults positions and greyed out so I can't change them.  The preview or the rendering then proceeds, applying no change.  I'm using a fresh install of Kino 1.1.1 running on Hardy Heron.

Is there a Kino forum or somewhere else I should post this?

---

### Post by kat_ams on 2008-12-19
I have the exact same problem.
I have a MPEG file that I imported into Kino, which separated it into a DV file.
When I try to use the Levels function this is grayed out.

Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

Kino 1.1.1 from the repositories.

---

### Post by kat_ams on 2008-12-19
== SOLVED ==

The trick to get levels to work is to go to the directory of the MPEG you imported. Close the MPEG in KINO and open de DV file that it seperated for you.
You can only adjust levels on Keyframes. You can add a keyframe by pushing the + button which is located right next to the Render button. So scroll with the preview button to a place you want leveled and push the + button and set your levels.
So set up the levels how you want them and render the movie. Go then to Edit and you can view the changes to your movie. Then save the movie.

---

