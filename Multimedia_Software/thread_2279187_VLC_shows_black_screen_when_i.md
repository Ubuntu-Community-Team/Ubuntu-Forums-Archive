---
title: "VLC shows black screen when i"
date: 2015-05-21
forum: Multimedia Software
---

### Post by esmarra on 2015-05-21
[COLOR=#000000]I am facing a problem,..
When i open any movie in vlc i can see [/COLOR][COLOR=#000000]perfectly, but when i pause the movie and [/COLOR]I start surfing the internet or doing something for a while, then when I go back to watch the movie again the screen show me in black!
If i go back to turn off the VLC program, and put on again continuous the screen black again.
To solve the problem I have to restart the laptop
Anyone know how to solve this problem?

---

### Post by esmarra on 2015-05-22
To fix it: go to Tools -> Preferences -> Video. At the Output, choose &#8220;X11 video output (XCB)&#8221; from the dropdown list.

---

### Post by systematic2 on 2016-01-15
Thanks esmarra.  Your suggestion solved my problem with vlc as well.  I had a black screen from the start.  I did not test any that were not x.264 encoded so I do not know if the problem exists with other codecs.  Can you explain how you knew that Video Output "X11 video output (XCB)" would solve that type of problem.  Your support has been most helpful.

---

### Post by Rob Sayer on 2016-01-16
Setting the output video module to x11 doesn't actually have anything to do with codecs.  VLC comes with its own codec library, and it's a very good one.

If you're using the x11 module you're using the basic linux x11 video server with no hardware acceleration at all.  I.e. the CPU is actually moving all the pixels around.  This is best avoided.

If using x11 output solves the black screen problem, what that is saying to me is that you either need to change some video settings or your video adapter won't do 3D hardware acceleration in linux.

There's not much video info posted.  Open a terminal and copy/paste these:

sudo lshw -C video

For the next one I don't remember if glxinfo is installed by default so first copy/paste this and it'll tell you if it's already installed:

sudo apt-get update
sudo apt-get install mesa-utils

And then (glxinfo is part of the mesa-utils package):


glxinfo | grep OpenGL

---

