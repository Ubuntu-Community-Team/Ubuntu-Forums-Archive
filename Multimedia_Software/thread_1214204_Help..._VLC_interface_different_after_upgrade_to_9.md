---
title: "Help... VLC interface different after upgrade to 9.04"
date: 2009-07-15
forum: Multimedia Software
---

### Post by BkkBonanza on 2009-07-15
Hello,
Finally upgraded to 9.04. I put it off for months because I always have issues I don't want to bother with. First one found within minutes...

VLC using default classic interface. Before had video in the same window as controls  - now puts the video in a different window. How can I get them both in the same window again. Have looked through prefs and tried changing options but nothing worked.

Also, full screen no longer has controls that show when the mouse moves. Why on earth would they get rid of that? It was great and now I have no controls at all except by right click menu. How can I get that back? 

I have full screen controls enabled in prefs but it doesn't work.

About box says I'm using version 0.9.9a

Anyone know what will fix these seemingly stupid changes?

Help much appreciated.
Chris :)

---

### Post by Labello on 2009-07-15
same problem. second window sucks as hell. i also want the old interface back!

---

### Post by BkkBonanza on 2009-07-15
I was able to fix this now by adding the PPA info to my sources so that VLC was updated using the PPA for the newer version 1.0.0. See the VLC downloads page for Ubuntu. They suggest adding the PPA line to your sources for 1.0.0.

After I used Synatpic to completely-remove the current (0.9.9a) version. I then installed again. Due to the new PPA (and you need to add the key), it will install 1.0.0. I found this version has the video integrated again and has the full screen controls. 

I don't know what got mucked up in 0.9.9a with Ubuntu 9.04 but I am getting correct desired behaviour now.

---

### Post by andrew.46 on 2009-07-15
Hi BkkBonaza,

> **BkkBonaza said:**
> I don't know what got mucked up in 0.9.9a with Ubuntu 9.04 but I am getting correct desired behaviour now.

You may be interested to know that vlc 1.0.0 is already in the repositories for Karmic Koala and it runs *very* nicely!

All the best,

Andrew

---

