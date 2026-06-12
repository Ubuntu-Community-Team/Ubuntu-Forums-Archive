---
title: "New problem listening to BBC radio"
date: 2009-08-26
forum: Multimedia Software
---

### Post by Janeleaper on 2009-08-26
Hi.

This problem is on 8.10 and 9.04.

No previous problems listening to BBC radio, but suddenly today can't get it to play.  I updated to 9.04 and ran through the comprehensive media how-to, but it made no difference.

When I select the "listen live" option on the BBC 4 home page the media player appears with the message: 

[I]For the best possible listening experience, please enable JavaScript.

Click here to launch BBC Radio 4 FM in Real Player."[/I]

When I select "click here" the message disappears but it does not play.  This happens on all BBC radio channels.

---

### Post by arky on 2009-08-26
Try any of these players gecko-mediaplayer, mozilla-mplayer or you can use totem BBC plugin to listen to these streams.

---

### Post by Janeleaper on 2009-08-26
Thanks but I already have Gecko installed.  It is that which is not working.  How do I install the other two?

---

### Post by Janeleaper on 2009-08-26
And I also have Totem video player with the BBC content plugin already installed.  Can't see any way to get it to play BBC radio.

---

### Post by Janeleaper on 2009-08-26
Ditto MPLayer, so installation is not the problem.

---

### Post by Janeleaper on 2009-08-26
I have another computer with 8.04 installed.  I'm not having any problem with listening to BBC radio on it.

---

### Post by Janeleaper on 2009-08-27
Does anybody have an answer to this?

---

### Post by oboedad55 on 2009-08-27
> **Janeleaper said:**
> Does anybody have an answer to this?

I'm listening as we speak using the mozilla-mplayer plugin on Firefox. I picked "listen using Realplayer" and then "use a standalone player".

---

### Post by Janeleaper on 2009-08-27
Solved.  I've been talking to myself, but I'll give the answer in case anyone reads this with the same problem.  It was a Java problem.  I went to Synaptic Manager and found that I had Sun Java 5 installed as well as Sun Java 6.  I uninstalled Sun Jave 5, restarted Firefox, and everything was hunky-dory. 

And I award myself a jam-donut.

---

