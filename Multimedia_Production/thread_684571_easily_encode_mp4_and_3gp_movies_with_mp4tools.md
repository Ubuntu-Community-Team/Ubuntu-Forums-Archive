---
title: "easily encode mp4 and 3gp movies with mp4tools"
date: 2008-02-01
forum: Multimedia Production
---

### Post by rootkit on 2008-02-01
Hi,

I made some script to encode movies into MP4 in all its flavours (iPod, 3gp, PSP) for a site I work for,
and then I released them packaged for Ubuntu.

This is the homepage: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

I have repos for hardy:
```
deb http://ppa.launchpad.net/teknoraver/ubuntu hardy main
deb-src http://ppa.launchpad.net/teknoraver/ubuntu hardy main
```

The cool thing is that, even if they have very high quality (look at the samples in the homepage)
they are very simple to use, because there are presets for PSP, 3gp, Symbian phones and iPod.
Adding new presets is very simple, just edit one and see
Also, i added to them features that i have never found in any encoding script like:

[LIST]
[*]direct rip from DVD
[*]autocrop of black borders to have a bigger visual
[*]audio peak normalization to make audio sound louder, useful on devices with poor speakers
[*]ID tags for Symbian phones
[/LIST]

I hope you enjoy them, feedback is welcome

---

### Post by jexxie on 2008-02-18
Is bittrade detection working now?

---

### Post by rootkit on 2008-02-18
what?

---

### Post by nothing0011 on 2008-02-29
How do I go about authenticating your repo so I can install MP4tools? Every time I try to install anything from a ppa.launchpad.net repo it always comes up as NOT AUTHENTICATED in Synaptic.

---

### Post by rootkit on 2008-02-29
You can't
The ppa system doesn't allow me to have a PGP key on the repository, so you have to trust my packages

---

### Post by seventyeights on 2008-03-01
> The ppa system doesn't allow me to have a PGP key on the repository, so you have to trust my packages

With a username like *rootkit*? LOL

---

### Post by seventyeights on 2008-03-02
Wisecracks aside, your program is very easy to use, unfortunately I found out my samsung blast is locked to a substandard standard of h263.

Thanks anyway.

---

### Post by Duffman on 2008-03-22
Do you happen to have a script for the xbox 360 mp4 playback?

---

### Post by rootkit on 2008-03-23
> **Duffman said:**
> Do you happen to have a script for the xbox 360 mp4 playback?
An user submitted it, please try

---

### Post by Kenniej on 2008-05-15
This script is awesome !!!! 

Only thing is , i'm not that good with writing oneliners :s

Could you tell me if it's possible to convert an entire folder with vids using your script ?

Greetz,
Kenniej

---

### Post by Twiggy794 on 2008-06-17
I started using TwonkyVision to stream my H.264 movies to my Xbox recently but for whatever reason Twonky wants the files to be m4v instead of mp4.  Changing the filenames to m4v worked for about 50% of my movies but the rest still won't play.  Would this script allow me to safely convert from the mp4 container to an m4v container with some tweaking?

---

### Post by halfhaggis on 2008-07-14
Regarding the lack of authentication keys from ppa.launchpad.net, read this:
[https://bugs.launchpad.net/soyuz/+bug/125103](https://bugs.launchpad.net/soyuz/+bug/125103)

---

### Post by BilliShere on 2008-07-23
Just to let everyone know.. I have tried everything...scripts, mp4tools, nautilus actions, winff, mobile media converter, and 3gp amr enabled self compiled ffmpeg. While some of them might work they do not work completely on my cell phone. (like some videos get converter some get errors) Like moblie media converter, the 3gp results usually cannot be set to custom resolutions like 320*240 and usually the video quality is garbage..The best solution however that worked and worked 100% and all the time for me is running Freez 3gp video converter under crossover pro 7 or wine. It is flawless, easy to use, and all the videos now in 3gp are in good quality and work on my cell phone (samsung d900i)no sweat.

---

### Post by rootkit on 2008-07-24
What errors you have with mp4tools? what phone do you have?

---

