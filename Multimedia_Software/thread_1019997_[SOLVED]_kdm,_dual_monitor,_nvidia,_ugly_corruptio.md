---
title: "[SOLVED] kdm, dual monitor, nvidia, ugly corruption"
date: 2008-12-23
forum: Multimedia Software
---

### Post by wd5gnr on 2008-12-23
This is a real nit pick, but here's my setup:

I have dual LCD monitors (total 2560x1024 using twinview). I have used nearly all the Nvidia drivers (the 177.x and the 180.x which work great). I use KDE 4.x (currently whatever ships with Kubuntu 8.1). 

All works well but there's one little annoying thing. When I am at the kdm login screen, the wall paper only goes so far. Maybe 2000 pixels or so (hard to estimate, but well into the 2nd screen). The rest of the screen is just a jumble of either noise (cold boot) or cut up pieces of what was on the desktop (warm boot). Which, of course, is a little security issue since people can see a jigsaw of what I had on my desktop when I logged off! Not that that really matters here, but still.

This has been true for all the 4.x kdm and all the NVidia drivers that I've used. The wall paper is an svg file so it should be scalable, but its like something won't stretch it past 2048 or some other magic number. Using the system settings to install new themes seems to be broken so I haven't tried a different wallpaper -- too lazy to do it manually.

So while this isn't the end of the world, I was wondering if anyone knew how to fix it or at least if anyone has the same problem?

<walks away, comes back 5 minutes later>

Ok found the problem. Edit /usr/share/kde4/apps/kdm/themes/oxygen/oxygen.xml as root. 

For example:

kdesudo kate /usr/share/kde4/apps/kdm/themes/oxygen/oxygen.xml

Find the lines near the top that say:

 <normal file="background.svg"/>
 <pos anchor="c" x="50%" y="50%" width="scale" height="100%"/>

and change the second line to say:

 <pos anchor="c" x="50%" y="50%" width="[COLOR="Red"]100%[/COLOR]" height="100%"/>

That's it!

Credit: [http://bugs.kde.org/show_bug.cgi?id=169772](http://bugs.kde.org/show_bug.cgi?id=169772)

---

### Post by Andre-D on 2009-01-15
anyone knows how to do this in Gnome ?

---

