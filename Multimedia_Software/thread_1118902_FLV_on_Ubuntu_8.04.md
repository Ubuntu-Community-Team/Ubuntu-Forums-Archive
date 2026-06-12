---
title: "FLV on Ubuntu 8.04"
date: 2009-04-07
forum: Multimedia Software
---

### Post by Fisher on 2009-04-07
Hi.
For some time I have been able to just watch videos on Youtube and then get them from the Firefox cache.
For about 3 weeks I just can't watch them with the same programs I used before (toten and vlc) even the new videos' thumbnails don't appear. The older ones are fine and running well. Does anyone knows what is happening?? Thanks.

---

### Post by Mze on 2009-04-07
use mplayer

Suggested package:
The version of mplayer included in Ubuntu is a little bit old (1.0rc2). SMPlayer has support for some of the new features of mplayer, so a newer version is highly recommended.

find a link to it from this [site]("http://smplayer.sourceforge.net/downloads.php")

---

### Post by Fisher on 2009-04-07
Cool!! Now I can watch them again in mplayer, thankyou!!
But, there are no miniatures from the videos. Is there a way to fix that too??

---

### Post by Mze on 2009-04-07
> **Fisher said:**
> Cool!! Now I can watch them again in mplayer, thankyou!!
But, there are no **miniatures** from the videos. Is there a way to fix that too??

Can you explain what you mean?

---

### Post by Fisher on 2009-04-08
Normally you got a video frame instead of the file icon.
This isn't appearing in the flv files for now, but I can play then in mplayer.

---

### Post by Mze on 2009-04-08
Must be a codec issue.

Right click on your Flash Video file and click the Audio/Video tab. 

If there's no info in the video section, then Nautilus doesn't show any thumbnails.

You might have to run a search on Google for a possible solution.

---

### Post by Therion on 2009-04-08
Start by installing ubuntu-restricted-extras, if you haven't already:```
sudo apt-get install ubuntu-restricted-extras
```
If still no joy, open Synaptic and search on **gstreamer**.  

Install everything "codec" related (Good, Bad, Ugly sets, no dev-tools or docs needed).

One, or the other, should fix your online video issues.  

Also the Video Download Helper plugin for FireFox makes saving those .flv files sooooo much easier.

[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

---

### Post by Fisher on 2009-04-08
I already have all that plugins.
In fact, everything was normal some weeks ago.
Does anyone knows if are there any kind of changes on youtube's flv videos?
Maybe I should update gstreamer, what's the version that comes with 8.10?? Is there any backport to 8.04?

---

