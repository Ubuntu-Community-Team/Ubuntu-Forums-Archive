---
title: "AVI Playback in Ubuntu"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by DasRoot on 2008-03-01
Kind of a newbie question, 
I've just finished a new clean install of 7.10 and I can't get any AVI playback. I'm using VLC and have enabled all the restricted formats and such but still nothing. Strangely though, I can get the thumbnails of the movies to display a snapshot of the movie halfway though so there has to be some playback in there somewhere. So in conclusion here is the long and short of it:

Open a video with VLC and correct codecs installed, just get audio and the player is the correct size for the video, but the video is black.

-DasRoot

---

### Post by pjbgravely on 2008-03-02
Have you tried Totem or Mplayer?.  It maybe a X-server or video driver problem. Also try running vlc in a terminal to look for errors.

Paul

---

### Post by songstruck on 2008-03-04
I could not play avi's with VLC (Ubuntu 7.1). On opening the file, I would see a brief green screen, then VLC would shut down. 

I found this suggestion for avi problems in another forum: **change the video output module to X11**. 

Here's how:
1) Open VLC
2) Choose "Preferences" from the "Settings" menu
3) Make sure the "Advanced options" box is checked at the lower right.
4) Expand the "Video" option in the list on the left
5) Click on "Output modules"
6) Change the Video output module to "X11 video output"

This fixed problems with some other file types as well.

Hope it works for others. Good luck. 

songstruck

---

