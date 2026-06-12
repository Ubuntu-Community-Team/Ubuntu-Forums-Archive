---
title: "Totem         Help"
date: 2005-12-21
forum: Multimedia &amp; Video
---

### Post by interse on 2005-12-21
When I try to start Totem from the Applications > Sound Video menu, I get the following message:

Totem could not start up
The video output is in use by another application.  Please close other video applications, or select another video output in the Multimedia Systems Selector.

WHAT IS THE PROBLEM BEING DESCRIBED?  There are no other applications running.  Is this because I do not have a video/sound card other than the one on the mother board?

I searched the forum, and this question has been asked before w/o an answer.  Can someone give us an answer.

Thanks

---

### Post by kairu0 on 2005-12-21
Do you have the totem-xine package installed? That might solve your problem as Xine handles the display better than Totem by itself.

---

### Post by interse on 2005-12-21
Thank you kairu0

I had the Breezy installation set-up: totem and totem-gstreamer.  I selected totem-xine for installation and synaptic indicated that gstreamer would be removed.

Now I can select Totem and the Totem window appears and stays w/o the 'totem could not start up' message.

At least now, I can work with Totem to set it up.  Curious, however, why would the default setup (original setup)  be Totem and totem-gstreamer which doesn't work?  The totem window in the default setup would instantly open & close and produce the  'could not start up' message.  Trying to understand what the problem was.

Thank you again.

---

### Post by kingsidy on 2005-12-21
i think that i had a problem with totem that was similar. It would close right after it opened. and gave so type of message. Turned out it happened when i was having a problem connecting to the internet through my router. I think that it was somehow connected to the networking interface. We i got online it stopped. I am not sure though but that is my explanation of the thing.

---

### Post by kairu0 on 2005-12-21
[QUOTE=interse]Curious, however, why would the default setup (original setup)  be Totem and totem-gstreamer which doesn't work?  The totem window in the default setup would instantly open & close and produce the  'could not start up' message.  Trying to understand what the problem was.[/QUOTE]

I am no authority, but I assume that it is because Xine has been around a lot longer and has had more time to work out X server intricacies and hardware-related bug fixes.

---

