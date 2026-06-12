---
title: "vidcutter alternatives"
date: 2020-05-30
forum: Multimedia Software
---

### Post by aeronutt on 2020-05-30
Loved vidcutter, but  appimage is giving me a lot of problems of late, and no repository for 20.04.

Other than command line (ffmpeg), is there an alternative to vidcutter?

---

### Post by jp41 on 2020-05-30
OpenShot

[https://github.com/OpenShot](https://github.com/OpenShot)

---

### Post by aeronutt on 2020-05-30
Thanks, I should have been more explicit. 
vidcutter is (was) an excellent fast efficient tool for (only) cutting/splicing/pasting various video formats, It is far from a full fledged editor. I'm aware of openshot, kdenlive, etc.

---

### Post by deadflowr on 2020-05-30
vidcutter has both a snap and a flatpak version.
[https://github.com/ozmartian/vidcutter]("https://github.com/ozmartian/vidcutter")

---

### Post by TheFu on 2020-05-30
> **deadflowr said:**
> vidcutter has both a snap and a flatpak version.
[https://github.com/ozmartian/vidcutter]("https://github.com/ozmartian/vidcutter")

The snap version doesn't support removable-media connections and hasn't worked over remote X11 ever.
The Appimage version is little better.

Often, we can run the programs outside the snap tool by directly running from the /snap/ location. i don't know whether vidcutter can work easily, but chromium-browser does. That's something to consider, though i expect it works easiest for KDE users, since vidcutter uses Qt for the GUi.

For something similar, i'm embarrassed to say *VideoReDo Suite* - a commercial Windows program.  it is actually much better than vidcutter and 1 reason i still have Windows.  There are 2 other reasons.  if i don't want to re-encode anything, then I&#8217;ll use VDP to create a vprj and feed that into **mkvmerge** which can do lossless cuts without transcoding.  The effective speed is like a file copy.  mkvmerge also handles all audio and subtitle track cuts perfectly, which other edits miss/don't.

Every other linux-based video editor I&#8217;ve seen the last 20 yrs transcodes even when the codecs don't change.

i looked at creating a front-end for mpv to create cut points (EDL) which many playback programs honor, but it wasn't as trivial as I&#8217;d hoped.  EDL can be easily converted to mkvmerge split parts format.

---

