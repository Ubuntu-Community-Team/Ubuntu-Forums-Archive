---
title: "Creating video that ubuntu can display"
date: 2019-08-05
forum: Multimedia Software
---

### Post by cearlp2 on 2019-08-05
I need help with my process of creating a slideshow video dvd.
I used imagination to create a slideshow with music. I think I followed all the steps outlined in several tutorial videos I viewed online.
I get to the export step and get a 'VIDEO-NAME'.vob file on my desktop.
Using brasero to burn the .vob file to a dvd fails. Trying to open the .vob file with VLC fails (Unable to open the file).
Using the disk utility shows the blue-ray disk as being on /dev/sr0 but the partition shows 'No media'.
Trying imagination multiple times, sometimes getting a video file without the .vob suffix, still will not play with VLC or Video Viewer.
With the sketchy explanation of what happened, can anyone see where I am failing or offer any suggestions?

---

### Post by Autodave on 2019-08-05
*OpenShot Video Editor.*  I have used this in the past with no issues.  You may want to take a look at it.

---

### Post by mc4man on 2019-08-05
What are you trying to achieve here?

Your imaginations app is just creating a a video file, if you choose VOB (DVD VIDEO) then it's creating a mpeg2 (MPEG-PS format) file.
Whether you tell it to use an extension of .VOB or .vob or no extension is irrelevant.
If the file is created correctly then vlc should play it no issue

To burn  - 
As is you can only burn to a data dvd

For DVD_VIDEO you need to author that file in a dvd authoring app. This creates the needed .VOB .IFO and .BUP files in a VIDEO_TS folder  to actually be a DVD_VIDEO.
Then  an .iso is created of that folder (and usually an empty AUDIO_TS folder) to burn to dvd media (not blu-ray media)

(- if you actually can produce a playable file in imagination (vlc, mpv, mplayer) then you could simply add that file to devede, it'll create an .iso for you to burn

---

