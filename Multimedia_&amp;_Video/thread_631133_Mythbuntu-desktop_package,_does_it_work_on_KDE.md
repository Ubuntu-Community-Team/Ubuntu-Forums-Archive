---
title: "Mythbuntu-desktop package, does it work on KDE?"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Mysticle31 on 2007-12-04
I have been trying to install MythTV.  I'm following these directions:

[https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Gutsy_Backend_Frontend_Desktop)

I've done this once before in another installation of Kubunut, and I can never find where it installs Mythbuntu.  There is no program icon for it. 

How do I run it manually?

Will it work on KDE?



That brings me to a general question.  I tried using Ubuntu for awhile and got frustrated with gnome.  There are things I like better about gnome though, such as nautilus.  What frustrated me about gnome was some minor gui issues, and that everything cool (Klipper, Kdirstat, krename, ksayit, and a couple others) are all for KDE.  There was a remote program for KDE that I needed to try and make my MCE remote work.  Does anyone know it? I forgot what it was and can't find it now.

---

### Post by barney_1 on 2007-12-04
Yes, mythtv works with KDE

Hmmmm... well, mythbuntu is really just a group of packages that help you install and configure mythtv.  If you install mythbuntu and also mythbuntu-control-centre you should have everything you need.

You should be able to configure the backend with the control center.  Try pressing alt-f2 and typing:
```
kdesu mythbuntu-control-centre
```

There should also be a menu entry for it.  In the K menu under either "settings" or "system".  

You will be able to launch the frontend from the K menu under multimedia.

---

### Post by Mysticle31 on 2007-12-05
Thanks for the info.

Nope, It isn't on any of the menus.  I could launch it manually though.  

This happens alot...

---

