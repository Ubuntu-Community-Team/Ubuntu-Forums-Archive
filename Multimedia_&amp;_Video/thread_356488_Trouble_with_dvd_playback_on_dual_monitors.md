---
title: "Trouble with dvd playback on dual monitors"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by Afkpuz on 2007-02-08
Hi, I'm extremely new to linux, so if you respond, please act like I know nothing about what you're talking about.

I'm on a quest to watch dvd's on my second monitor.  I have a laptop which has a default screen res of 1680x1050 and a giant crt monitor(really more like a tv) that has default res of 800x600.  Heres what happens when I play a dvd using mplayer.  

Linux has automatically cloned my laptop screen onto the crt. Right now, both screens are locked into the same resolution. I don't know how to set them up with seperate resolutions, so I lower the resolution to 800x600 (through System>Prefrences>Screen Resolution) and they both change.  I think, ok good, both displays look fine.  Then, I goto play the dvd using mplayer, or really any dvd player, and I can see the video on my laptop screen, but not on the crt.  I can see everything on the crt except the video.  It will show the mplayer window, but no video inside.  Can anyone help?  

Oh yea, i'm running dapper drake and have an ATI mobility x700 video card.

---

### Post by Afkpuz on 2007-03-27
Well, no one has replied to this, but I fixed it myself.  I thought I'd post what I did in case others have this problem.

The first thing I did was get a decent dvd player.  I've found that Xine seems to be amazing in terms of everything.  Just goto synaptic and search for "xine".  

Next, I updated my ATI driver with the driver from the ATI site.  Since I'm new to linux, I didn't know how to execute the darn thing, so it just sat on my desktop.  For all you newbies, heres how to execute an .sh file.



navigate to the directory of the file and type   

```
sudo ./filename
```


It's that simple.  If it doesn't work, you probably don't have permission to execute this file.  To enable permission, go into same directory and type
```

sudo chmod +x filename
```

Then, try the ./ command.  The ati install program should pop up.  Now we're cookin!

I installed that and rebooted.  Now, a sweet new button is added under the applications menu: ATI Control.  Open that up and set it to big desktop horizontal.  reboot and ubuntu should have picked some large resolution automatically.  I noticed that it stretched out my background picture.  Anyway, open up your dvdplayer and drag the WHOLE window onto your other monitor.  It should work fine now.  

Thats what fixed it for me.  I hope this helps someone.

---

