---
title: "Intel Driver 965GM Xv, compiz support HELP!!!!!!"
date: 2008-04-02
forum: Multimedia &amp; Video
---

### Post by dan33 on 2008-04-02
I am pulling my hair out. I have an intel 965GM X3100 card and am trying to get Xv support to work with compiz. Right now I am using the "intel" driver and compiz is working, but I am forced to use the X11/Shm driver for xine, mplayer, vlc etc....
when I add the Option "AccelMethod" EXA to the Device section in xorg.conf Xv works, but is really choppy. Can I fix the "choppiness"? When I use the default XAA Xv does not work. Is there a way to fix that? I tried using the i810 driver instead. For some reason with that driver if I enable compiz Xv wont work and if I disable compiz Xv will work. Any suggestions or direction would be great...

thanks

---

### Post by warp99 on 2008-04-03
This is a know bug with the current drivers, Compiz, and xv:

[https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel?highlight=%28965%29](https://help.ubuntu.com/community/CompositeManager/CompizFusionIntel?highlight=%28965%29)

---

### Post by dan33 on 2008-04-03
Thanks for the advice, but I already did that....I am using
- Intel GMA965 (X3100) Intel driver
- compiz is working
- using X11 for video.

I just wanted to confirm that there's no way to get Xv to work smoothly. Xv works if I use EXA instead of XAA, but everything is very choppy. 

I tried changing the driver to i810, but Xv only works if I disable compiz.

---

### Post by warp99 on 2008-04-04
> **dan33 said:**
> Thanks for the advice, but I already did that....I am using
- Intel GMA965 (X3100) Intel driver
- compiz is working
- using X11 for video.

I just wanted to confirm that there's no way to get Xv to work smoothly. Xv works if I use EXA instead of XAA, but everything is very choppy. 

I tried changing the driver to i810, but Xv only works if I disable compiz.

It's a known bug with the developers at [intellinuxgraphics.org]("http://intellinuxgraphics.org/"). They haven't implemented any changes as of this moment.

---

### Post by dan33 on 2008-04-04
I managed to find something on the web, which I tried and it resolved my issue.

I added the following to my device section in xorg.conf 
Option "AccelMethod" "exa"
Option "MigrationHeuristic" "greedy"
Option "ExaNoComposite" "false"
 
and

I've also added this:
INTEL_BATCH="1"
in /etc/environment

---

