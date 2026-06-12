---
title: "Mythtv - local channels only?"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by Copland Audio on 2007-06-11
Anyone run into this?  I'm only getting (it seems) local channels - not my basic cable channels (Comedy Central, Discovery, etc) I'm getting static with those. Is this something with the lineup retrieval, input connections, or video source possibly?  It seems a bit odd, because our local Fox affiliate over the air is channel 32, but I get reception through cable (and also MythTV) on channel 6, so I am getting something through the cable, just not everything...

---

### Post by barney_1 on 2007-06-11
I ran into the same problem you're having.  You need to make sure that your fequency tables are set for cable, and not for bcast:

There are two places to do this; a global setting and an input setting:

From the desktop of your backend machine choose "System-->Administration-->Mythbackend Setup"

Select "General" and go forward to the third page of settings.  Choose "us-cable" for channel frequency settings.

Finish through until you get to the main menu of the backend settings again.  Go into your Video Sources and choose the source you have setup.  This also has a channel frequency table setting.  If it is set to default it will use the global setting we just checked on above.  You could also choose to set it to us-cable by default

That should fix you right up.  Good luck!

---

### Post by Copland Audio on 2007-06-11
SUCCESS!!!

Thank You, Thank You, Thank You!

---

### Post by barney_1 on 2007-06-11
No problem, glad you've got it up and running.

---

### Post by kroenecker on 2007-09-16
What hardware are you using in order to view cable channels?

---

### Post by pheno on 2007-10-05
i noticed there are two other cable options for the channel frequency table setting, something like "us-cable-hrc" and "us-cable-irc" (?). does anyone know what those are for?

---

