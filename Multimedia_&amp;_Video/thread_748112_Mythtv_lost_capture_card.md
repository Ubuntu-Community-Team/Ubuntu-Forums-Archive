---
title: "Mythtv lost capture card"
date: 2008-04-07
forum: Multimedia &amp; Video
---

### Post by kbehel on 2008-04-07
My Mythtv frontend/backend system just lost the capture card two days ago. My mythbackend.log says:

ERROR: no valid capture cards are defined in the database.

mythtv setup sees the card and starts to let me add it, but it doesn't appear in the list of capture cards when I go back to that screen. So it appears that it is refusing to actually add the card.

I didn't change anything on this system when that happened - I absolutely refuse to install any software on this system or do any other sort of change since anytime I have done that with Ubuntu bad things have happened with my Mythtv setup.

The only thing that did happen that day is I added MythVideo to a backend server on the network.
 I have seen some postings about the database getting problems that can cause the capture card to disappear ([http://ubuntuforums.org/showthread.php?t=692070&page=2](http://ubuntuforums.org/showthread.php?t=692070&page=2)) , but since I didn't change a thing on the frontend and my backend does not have a capture card I don't see how this would make that happen. I should be impossible for a backend to corrupt the frontend's capture card database.

Does anyone have idea what can cause this and how to fix this?

thanks,

Kevin

---

### Post by blcvegas on 2008-04-07
Does it appear that your database is still good?  Are you able to see a list of your recorded programs and are you able to play them?

---

### Post by kbehel on 2008-04-07
All that works fine. All the shows are there, my secondary frontend can even access all the videos over my network. It just seems confused about the card. 

very confused.

thanks,

Kevin

---

