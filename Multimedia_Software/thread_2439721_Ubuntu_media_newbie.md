---
title: "Ubuntu media newbie"
date: 2020-03-31
forum: Multimedia Software
---

### Post by xcfstarflight1 on 2020-03-31
Hi guys!
I own a Nikon DX45 camera and had the software for windows. 
Is the software available in Linux?
Also I need a good tool to convert .wav to .FLAC and .MOV to .avi.

Anything that you guys think a newbie should learn or tools I need please post on my thread!

---

### Post by CelticWarrior on 2020-03-31
> **xcfstarflight1 said:**
> I own a Nikon DX45 camera and had the software for windows. 
Is the software available in Linux?

What software? For what purpose?
No special software is needed to access its internal storage.


> Also I need a good tool to convert .wav to .FLAC and .MOV to .avi.

First you need to install additional codecs. Running ```
sudo apt install ubuntu-restricted-extras
``` should be enough for the vast majority of uses.
Then you need software tools for conversion. Many audio conversion tools and at least one video conversion tool (Handbrake) are available in the repositories, just open the Software app, search and install what you want.

---

### Post by mc4man on 2020-03-31
wav to flac is simple
```
sudo apt-get install flac
```
Then open terminal &  obviously replacing whatever.wav with actual name
flac /path/to/whatever.wav

In a few seconds there will be a same filename.flac in same folder as the .wav is.

---

### Post by Autodave on 2020-03-31
If you are meaning to get the pics in RAW format, then check out Darktable: it is in the repositories.  Personally, I have not used it, but I do see people that have had good luck with it.

---

### Post by TheFu on 2020-03-31
.MOV to .avi is just a container change.  Did you want to change the v-codec and/or audio codecs used too?

.avi is seldom used container for the last 10 yrs.  it was popular from 2005-2010-ish with divx/mp3 videos.  After that, mp4 and mkv containers took over.    mkv can hold pretty much any vcdeo or audio or other sorts of files for playback.  mp4 containers are more open than avi, but very much restricted when compared to mkv.

Most container changes are handled most efficiently using ffmpeg.  Almost all other tools that convert video files uses ffmpeg.
```
ffmpeg -i   some-file.mov  some-file.avi
```
That uses the default conversion settings.  Most people need a little more control.

Aren't the ubuntu-restricted-extras  for DRM stuff, which i assume you want to avoid. I’ve only needed that package when reading commercial movie DVDs.

For a GUi tool, there are a few.   avidemux, handbrake, openshot.  There are others like mkvtoolnix-gui if you don't want to transcode the audio or video codecs used.

For photo stuff, shotwell is where I’d start.  Then use "shotwell vs" in a google query to see competition.  i have hundreds of thousands of photos, but always avoid using any organization  tool due to their lack of being cross-software. Data goes in, but never comes out.  Best to just manually setup a directory structure and use EXiF data inside the files to hold any metadata.  Any external DB will become useless in a few years and all that entered data will be lost.
IMHO.

---

