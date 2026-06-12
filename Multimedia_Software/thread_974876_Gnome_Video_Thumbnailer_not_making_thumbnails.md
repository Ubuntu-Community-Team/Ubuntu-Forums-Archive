---
title: "Gnome Video Thumbnailer not making thumbnails"
date: 2008-11-07
forum: Multimedia Software
---

### Post by euxneks on 2008-11-07
Hello all, I've recently been having issues with gnome-video-thumbnailer not actually creating thumbnails for all my videos.

Did a search and found a few things I could try:

I've tried the different options for gnome-video-thumbnailer ala:
```
sudo update-alternatives --config gnome-video-thumbnailer
```
(tried both options to no avail)

I've also removed ~/.thumbnails in combination with the above and it's removed some thumbnails that were there previously, and not regenerated them!

Most of my video files are .mkv, and over 1 GB.  I also have a couple of .avi files under 1GB but they're not getting thumbnails either. :(

This seems to have happened after I upgraded from Hardy to Intrepid.

Anyone have an idea on how I might solve this particularly annoying yet minor issue?

Edit: It seems like the movies won't play in totem and it can't find the codecs for them, yet Mplayer plays them fine (as far as I know I've got all gstreamer video codecs packages installed)

Edit2: I've solved this by using a set of scripts I found here:
[http://me2030581.googlepages.com/download_mplayer](http://me2030581.googlepages.com/download_mplayer)
which uses mplayer to thumbnail the video files. I know that mplayer works and this thumbnailer also works.  I am annoyed that I had to use this script however.

---

