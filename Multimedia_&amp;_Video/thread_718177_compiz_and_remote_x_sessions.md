---
title: "compiz and remote x sessions"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by nfox on 2008-03-07
Hi,

I have a laptop-dock at work and when I plug in the desktop monitor, I use XRandR to set up dual screen. I am able to (on the fly) load the laptop monitor as the bottom screen and the desktop monitor as the main (top) screen and loads accordingly to the Compiz desktop cube. When I rotate the cube, my screens are stuck cylinder-fashion to the desktop cube. Why am I telling this?

 I would like to use a remote x-server to act as that separate screen but do not know how to call it from bash.

Background:
I have 3 laptops and a desktop and have a (sexy) wrt54g connecting them. I want to be on Laptop A-C and remote-connect my Desktop D as a second 'monitor' and use XRandR to paste it onto my desktop cube.

Outcome:
I hope to be able to attach a PC's screen into my currently-in-use PC's Compiz cube.
I've seen Synergy able to use one set of inputs across many computers but I think this is cooler. 
The code I use for XRandR (if you're interested) is:

```
xrandr --output LVDS --pos 1280x0 --output VGA --auto --above LVDS
```

I would like to get a remote X session to replace 'VGA' in the above line. How would I even define an alias like that?



If I can get some help, I'm planning on releasing a tutorial since this would make sharing between PCs a breeze.

---

