---
title: "AMR Files?"
date: 2009-09-29
forum: Multimedia Software
---

### Post by PerfectReign on 2009-09-29
I have tried this and not been successful.

Here's one search: [http://ubuntuforums.org/showthread.php?t=174215](http://ubuntuforums.org/showthread.php?t=174215)

I am using a Blackberry 8310 (Perl?) with voice recorder. It stores in .amr format.

I looked in Syanaptec and found that I have installed the amrwb (7.0.0.3-0.0medibun) package installed. I also have the amrnb package and the corresponding libamrwb3 and libamrnb3  files. (Same funky version number.)

When I save and double-click on an .amr file, a program called, Movie Player, comes up and gives me the error message, "The playback of this movie requires a Adaptive Multi Rate (AMR) decoder plugin which is not installed."

Any ideas?

---

### Post by Judo on 2009-09-29
Movie Player (Totem) uses GStreamer to load decoders.  You may have a working decoder but possibly not a GStreamer plugin for it.

I have no problem playing AMR files with libavcodec.  The GStreamer plugin for it being gst-ffmpeg, or something along those lines.  Although, I've compiled it from source so I can't say for sure if the one in the repositories supports AMR or not.

---

### Post by andrew.46 on 2009-09-29
Hi PerfectReign,

> **PerfectReign said:**
> I looked in Syanaptec and found that I have installed the amrwb (7.0.0.3-0.0medibun) package installed. I also have the amrnb package and the corresponding libamrwb3 and libamrnb3  files. (Same funky version number.)

When I save and double-click on an .amr file, a program called, Movie Player, comes up and gives me the error message, "The playback of this movie requires a Adaptive Multi Rate (AMR) decoder plugin which is not installed."

If you already have the Medibuntu repository enabled you can easily get amr playback:

```
sudo apt-get install mplayer smplayer
```

Then open the file using SMPlayer. You may get a warning about your version of MPlayer being a little old but you can safely ignore that for the moment.

Andrew

---

### Post by PerfectReign on 2009-10-15
Okay, it was mplayer to the rescue.

I have been using VLC for some time, but then just switched the association for amr files to mplayer.

All is good.

(Now I just need GNOME to provide a better method for associating files than having me go to /usr/bin/mplayer.)

---

### Post by andrew.46 on 2009-10-15
Hi PerfectReign,

> **PerfectReign said:**
> (Now I just need GNOME to provide a better method for associating files than having me go to /usr/bin/mplayer.)

If you have also installed SMPlayer you could simply associate this filetype with SMPlayer, it is simply a front-end for MPlayer.

Andrew

---

