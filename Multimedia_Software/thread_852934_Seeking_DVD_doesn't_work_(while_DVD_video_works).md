---
title: "Seeking DVD doesn't work (while DVD video works)"
date: 2008-07-08
forum: Multimedia Software
---

### Post by kimolias on 2008-07-08
I've successfully installed libxine1 packages and Movie Player (xine-backend) for playing DVD and indeed, DVD does play. The problem occurs when I want to skip forward in the seek bar.

The movie I chose is Layer Cake (just in case it matters).

Totem
Once I click any position in the bar, the movie skips to the beginning and after a few seconds a message pops up and says "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

From the console when I run totem and click to play the disk it will print :
"libdvdnav: Using dvdnav version 1.1.11.1 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/pek/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00e50000. Regions: 2 4 5

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0001162c
libdvdread: Elapsed time 0

yada yada yada (a lot of libdvdreads)

demux_wavpack: (open_wv_file:127) open_wv_file: non-seekable inputs aren't supported yet.". 

When I forward the movie, no error in the console exists. Just the pop up one. Totem works with DVD menus ok, and the movie starts playing all right, with subtitles etc. It's only when seeking the error occurs. Also, skipping chapter has no problems.

SMPlayer
I can't make SMPlayer work at all with DVD. When I click "DVD from drive" it plays a black screen for some seconds (I'm assuming this would be the main menu of the dvd) and then it will play the first 7 seconds of the movie until it simply freezes. When running SMPlayer from the console, there are a bunch of messages which print various information but none indicate the error. Especially when the freeze occurs, there is no extra output in the console.

VLC
VLC behaves even worse when seeking. The movie starts, I click the seek bar in a random position, the movie continues to play until, a few seconds later, the movie just stops playing (no image is displayed, it's like I clicked stop).

When running vlc from the console it prints the same messages as Totem (probably because it uses correctly xine). The dvd menu is displayed correctly and the movie starts normally. Once I click the seek bar vlc prints in the console:
[00000394] main decoder error: decoder is leaking pictures, resetting the heap
[00000387] main video output error: picture to date 0xf4db60 has invalid status 6
[00000387] main video output error: picture to display 0xf4db60 has invalid status 6
[00000387] main video output error: picture 0xf4db60 refcount is -1
[00000289] main playlist: nothing to play

(at last, some response in the console).

So, to conclude, in players where I can play DVD normally (Totem, VLC) seeking is broken.

Any help?

As always, thank you in advance.
Panagiotis.

---

