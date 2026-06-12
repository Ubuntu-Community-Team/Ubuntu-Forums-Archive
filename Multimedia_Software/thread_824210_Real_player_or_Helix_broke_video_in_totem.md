---
title: "Real player or Helix broke video in totem"
date: 2008-06-09
forum: Multimedia Software
---

### Post by mynameisrodney on 2008-06-09
Hi guys,

I had an old .rm file that totem wasn't playing properly, so i tried installing real player 11 and helix. Neither of them would play it and now my video is stuffed in totem. It's done a kind of negative colour thing and it's not just for rm files, it does this for ALL video files.

[IMG]http://i119.photobucket.com/albums/o126/mynameisrodney/totem.jpg[/IMG]

I have uninstalled realplayer and helix and have tried re-installing totem and all my gstreamer plugins but the problem is still there. Anybody had this happen before? any suggestions?

Cheers,
Chris

---

### Post by zorba_the_greek on 2008-10-24
Did anybody know anything?? I am dealing with the same problem... :(:(

---

### Post by Sandworm on 2008-10-26
Same thing here.  Funny thing is that when I tried playing the same video twice, ie simultaneously in two windows, the second video was OK.

---

### Post by zorba_the_greek on 2008-10-26
> **Sandworm said:**
> Same thing here.  Funny thing is that when I tried playing the same video twice, ie simultaneously in two windows, the second video was OK.

I found some kind of solution.

[LIST]
[*]Press Alt+F2 in order to open "Run Application" and "write gstreamer-properties"
[*]Go to the "Video" tab
[*]In "Default Output" change the option of "Plugin" to "Custom"
[*]Write "videobalance hue=-1 ! autovideosink" to "Pipeline"
[/LIST]
This worked for me... :)

---

