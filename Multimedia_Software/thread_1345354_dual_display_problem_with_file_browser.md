---
title: "dual display problem with file browser"
date: 2009-12-04
forum: Multimedia Software
---

### Post by jonbitzen on 2009-12-04
I am having a subtle problem with the file browser on the secondary display in my dual-head setup in Ubuntu 9.10.

When I open a file browser from the Places menu, and attempt to click the little triangles to expand the file hierarchy (my default file view is "List View", and my behavior setting is to "Always open in browser windows"), Im finding that it accepts the first click, but after that I cant interact with any of the triangles or buttons on that browser window anymore until I have moved the browser window over a few pixes from its previous position.  I have also noticed that raising and lowering the window from the bottom bar doesnt work properly either.

What is more interesting is that if I open an application on the second display, for example netbeans or firefox, I can interact with all its controls satisfactorily.  Except for the bottom bar to raise or lower the app, which again wont work without moving something in the window a few pixels.

None of these problems occur on the primary display, only the second display.

Im using the "Separate X-Screen" Desktop, I have an 8800 GT / 512Mb, I've tried 3 versions of the Nvidia driver (officially supported 173 and 185, as well as a 195 package I found elsewhere).  I've tried turning display special effects off.  Oh yes and Im using whatever version of Gnome desktop comes with Ubuntu 9.10 x64.

Has anyone else seen this problem?  It sounds like a window manager issue since normal client apps work fine except for controls related to the frame, but Im not sure how I'd fix it.

Thanks

jonbitzen

---

### Post by jonbitzen on 2009-12-05
bump.  

I'd add that I've continued to experiment with this, and I find that moving the cursor anywhere outside the offending file browser's client space also does the trick.

---

### Post by statictonic on 2009-12-06
I have this same problem, it occurs on screens other than my primary one, I can't click buttons on a window until i either move the window or move my cursor to my primary screen then back to the secondary screen.  Also using a 8800gt video card and nvidia 173 driver on 9.10.

---

### Post by macanudo on 2009-12-07
I have the same problem. Im using a 4 monitor set up, 2 X sessions, one nvidia 9500GS and one nvidia 6200.. Im running the 190.42 drivers with Compiz.. Compiz works fine, its just this annoying problem with the file browser.. just as you detailed. I noticed it because the mouse scroll wheel dosent work after clicking on a dir in the browser, but its just as you describe.

---

