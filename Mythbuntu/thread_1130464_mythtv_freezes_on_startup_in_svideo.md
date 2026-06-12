---
title: "mythtv freezes on startup in svideo"
date: 2009-04-19
forum: Mythbuntu
---

### Post by poerschr on 2009-04-19
After installing mythbuntu, I have slowly worked through many problems and been able to fix them all, except for a problem when the computer is hooked up to a CRT TV using s-video out.  Mythtv freezes on start up of the frontend. Look at the picture below:   

[IMG]http://kimogg.com/mythtv.jpg[/IMG]

Mythtv works perfectly when hooked up to a LCD monitor.

I have added the following lines in xorg.conf as follows:

```

Option "TVOutFormat" "SVIDEO"
Option "TVStandard" "NTSC"
Option "ConnectedMonitor" "TV"

```

Nothing works.

System specs:
mac mini, core 2 duo
mythbuntu 9.04 RC
mac dvi to s-video adapter

Thank you...

---

### Post by nickrout on 2009-04-20
It looks as if it is at the point where the system resizes the theme images. That usually takes a while to happen. How long have you left it?

---

### Post by poerschr on 2009-04-20
One time I left it sit for about 3 hours - nothing happened.

I really cannot narrow down whether it is a problem within xfce, unbuntu, or mythtv alone.  The modifications I made to the xorg.conf file have no effect.  But I did realize that may need to make the tvout specifications for DVI instead of s-video, becasue the mac mini uses a DVI to s-video converter.  The video is still going through the DVI.

Thank you..

---

