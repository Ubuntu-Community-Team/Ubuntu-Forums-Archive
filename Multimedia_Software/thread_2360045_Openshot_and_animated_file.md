---
title: "Openshot and animated file"
date: 2017-05-01
forum: Multimedia Software
---

### Post by satimis on 2017-05-01
Hi all,

Ubuntu 16.04

Please advise how to make gif file (animated file) to work on OpenShot? When importing gif file it popup "OpenShot does not support this file type"

Thanks
satimis

---

### Post by ajgreeny on 2017-05-01
What do you want to do with the gif?

There are many applications that will show you the animated gif, for example ristretto from xfce, and probably eog from Ubuntu, though I do not use that so can't test it.

---

### Post by satimis on 2017-05-01
> **ajgreeny said:**
> What do you want to do with the gif?
- snip -

Hi,

I have a title created (please refers to attached file).  But I am not allowed to import it to OpenShot

Regards
satimis

---

### Post by #&amp;thj^% on 2017-05-01
GIF's are not well supported in openshot...but converting them to other formats works if done corectly.
Here's what worked for me: BTW it has been a year or more since I last done this.
```

ffmpeg -i animated.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" video.mp4
```
And Why:
**movflags **– This option optimizes the structure of the MP4 file so the browser can load it as quickly as possible.

**pix_fmt **– MP4 videos store pixels in different formats. We include this option to specify a specific format which has maximum compatibility across all browsers.

**vf – MP4 **videos using H.264 need to have a dimensions that are divisible by 2. This option ensures that’s the case.

Video Animated GIFs: A Terrible Hack of Convenience:
Source: [http://rigor.com/blog/2015/12/optimizing-animated-gifs-with-html5-video](http://rigor.com/blog/2015/12/optimizing-animated-gifs-with-html5-video)

---

### Post by satimis on 2017-05-01
> **1fallen said:**
> GIF's are not well supported in openshot...but converting them to other formats works if done corectly.
Here's what worked for me: BTW it has been a year or more since I last done this.
```

ffmpeg -i animated.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" video.mp4
```
And Why:
**movflags **– This option optimizes the structure of the MP4 file so the browser can load it as quickly as possible.

**pix_fmt **– MP4 videos store pixels in different formats. We include this option to specify a specific format which has maximum compatibility across all browsers.

**vf – MP4 **videos using H.264 need to have a dimensions that are divisible by 2. This option ensures that’s the case.

Video Animated GIFs: A Terrible Hack of Convenience:
Source: [http://rigor.com/blog/2015/12/optimizing-animated-gifs-with-html5-video](http://rigor.com/blog/2015/12/optimizing-animated-gifs-with-html5-video)
Hi,

Your advice works for me.

The attached link is very interesting.

Lot of thanks for your help.

Regards
satimis

---

