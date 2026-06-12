---
title: "Basic Xinerama Setup, non Twinview"
date: 2006-06-01
forum: Multimedia &amp; Video
---

### Post by duckie68 on 2006-06-01
Greetings everyone.  I was a big fan of Xinerama long ago when I used a Linux flavor that set it up automatically.  Since then I've had a lot of trouble finding really clear and concise guides so I did a little footwork of my own to try and make a HowTo that I think is fairly easy to follow and just simple enough for the Linux beginner to use.  I've got it posted on my own blog for the time being, but I'd like any input; questions, concerns, critiques, whatever and then maybe see about posting it in the HowTo section of this forum or even the Ubuntu Wiki.

You can visit the guide I wrote at [http://duckie680.blogspot.com/2006/06/xinerama-in-ubuntu.html](http://duckie680.blogspot.com/2006/06/xinerama-in-ubuntu.html) .

Please leave me preferably constructive comments either here or on my blog.

---

### Post by andefeldt on 2006-06-10
Hi. 

I've been looking a little at Xinerama, but haven't tried to set it up yet. 

I have two screens. I would like them both to show the same desktop image (clone), but screen1 should show 1280x1024 and screen2 1360x768. It seems like it isn't possible with TwinView. Is this possible with Xinerama? And then how? Seems like you're the man to ask :)

Anders

---

### Post by duckie68 on 2006-06-10
Well, I haven't worked with Twinview (yet) but I can say for sure that Xinerama will allow two different desktop geometries, as long as your video card and monitor can in fact handle them.  When I first started experimenting with it I was often limited by really outdated hardware so the differing geometries were nescesary for me.

If you want to go ahead and try a setup, just follow the guide I made for a basic Xinerama setup.  I've tried to keep it simple enough and leave you enough instructions in case it doesn't work out for you.  The worst that can happen is you'll be left with a command prompt but things should be clear enough to allow you to return to a working config... just in case ;)

When it comes to setting up the config you are looking for, the part you will need to work on in /etc/X11/xorg.conf is Section:Screen, SubSection:Display.  I assume that you know your cards and monitors will handle the resolutions you desire, so I'd suggest simply setting up the currently unused display ONLY with the resolution you want to use.

If things do not work out, try starting out with the same resolution and go from there.  I know diferent resolutions will work, but I also know that some things just need to be tweaked.

For a final note, both displays will carry the same desktop image (background) but they will effectively be one big desktop.  Applications showing up on one will not be cloneed to the other.  I like this setup myself because it allows me to effectively have a 2048x720 display.  I can have a gimp workspace in one with the tools in another, or watch tv on one with my browser in another.  If you need one screen to have a literal copy of the other, then Xinerama is not for you (sorry).

Good luck, and if you have any problems, please feel free to write back and I'll help however I can.

---

### Post by andefeldt on 2006-06-13
Hi again,

I've been looking at your page, and the Xinerama howto. I can't seem to find anything about cloning the desktop in different resolutions. Can Xinerama do that or can't it?

If it can't, then I don't really know how to setup my system. Maybe then I just want to extend my desktop, meaning that all my icons, menubars etc. can just be found on my main monitor and only the background image can be seen on my 16:9 screen.

Any suggestions?

Anders

---

