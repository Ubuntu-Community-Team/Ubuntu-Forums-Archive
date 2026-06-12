---
title: "ffmpeg / libav-tools nightmare fix"
date: 2014-04-18
forum: Multimedia Software
---

### Post by slumbergod on 2014-04-18
Just in case anyone has problems fighting with the ffmpeg/libav-tools that is included in the Trusty repos. My audio conversion script stopped working. In the end I gave up. (

(Sorry if I have made a cardinal sin in my less than elegant solution but I learned long ago that asking for help on these forums often attracted some nasty comments from people who really don't have the right personality type to be contributing here).

1. Get rid of the mess the repos cause: sudo apt-get purge ffmepg libav-tools
2. Get the static build or ffmpeg from [http://ffmpeg.gusari.org/static/](http://ffmpeg.gusari.org/static/)
3. Extract then rename the folder to ffmpeg.
4. Move the folder to /opt (or somewhere else): sudo mv ffmpeg/ /opt/
4. sudo ln -sT /opt/ffmpeg/ffmpeg /usr/bin/ffmpeg

That got it working like it should have for me.

---

### Post by andrew.46 on 2014-04-18
> **slumbergod said:**
> Just in case anyone has problems fighting with the ffmpeg/libav-tools that is included in the Trusty repos. My audio conversion script stopped working. In the end I gave up. 

Good to see that you have solved your issues but it would be interesting to see if your script simply required some modification to work with Trusty's avconv package?

---

