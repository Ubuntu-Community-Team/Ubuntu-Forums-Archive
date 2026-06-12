---
title: "reload .asoundrc without logging out and in"
date: 2009-07-20
forum: Multimedia Software
---

### Post by 4dplane on 2009-07-20
Hi,

my Ubuntu setup will be used by multiple people and at different places and some people will want to use HDMI audio and other will wan to use the 1/8 inch audio jack(analog). All of my sound is working except I have to change this line of my .asoundrc to switch to either HDMI or analog.

```
HDMI
pcm "hw:1,3"

Analog
pcm "hw:0,0"
```

So I am looking to set up a script that I can call from a button that will use different .asoundrc files or an .asoundrc file that has a conditional in it that switches the output. How can this be done? Can the .asound file use conditionals like "if" and how can I tell Linux to re-read the updated .asoundrc file.

Thanks,
4dplane

O' by the way, all of this is being run with Fluxbox but I don't think that will make a difference.

---

