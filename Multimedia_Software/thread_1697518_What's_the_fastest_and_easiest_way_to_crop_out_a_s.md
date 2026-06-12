---
title: "What's the fastest and easiest way to crop out a section of an AVI file?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by Rodayo on 2011-02-28
I want to create a gif of a video using gifninja.com

Rather than going through the trouble of downloading and installing a graphical video editor, I was wondering if there's a tool that lets you do this with a simple command. Thus no need to download the graphical end; just the lib and the wrapper.

Thanks,
Dave

---

### Post by aeiah on 2011-03-01
well this is one of those things where its actually easier with a graphical editor. id use avidemux. its pretty quick. for best results, crop on keyframes.

for cli, use mencoder to play the section you want and output it to a new file

```
mencoder source.avi -ss 01:01:01 -endpos 33 -ovc copy -nosound -o output.avi


```

this starts recording at 01:01:01 and saves 33 seconds

---

### Post by mimor on 2011-03-01
This might be what you're searching for:
[http://blog.ahfr.org/2008/03/making-animated-gifs-with-free-software.html](http://blog.ahfr.org/2008/03/making-animated-gifs-with-free-software.html)
Hope it helps

---

### Post by Rodayo on 2011-03-02
> **aeiah said:**
> well this is one of those things where its actually easier with a graphical editor. id use avidemux. its pretty quick. for best results, crop on keyframes.

for cli, use mencoder to play the section you want and output it to a new file

```
mencoder source.avi -ss 01:01:01 -endpos 33 -ovc copy -nosound -o output.avi


```

this starts recording at 01:01:01 and saves 33 seconds

I got tired of waiting for replies so I went ahead and used OpenShot, took forever to figure it out. Honestly sometimes I use programs and I'm just appalled at the kind of obvious features the developers don't include.

Anyway, thank you for the reply. That is exactly what I was looking for. I anticipate I will make gifs more often so I'll try that right now.

---

