---
title: "Blue overtone to all TV channels on MythTV...Bad audio too."
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by t00th on 2007-04-24
I recently got MythTV installed and running.  All of the channels are very blue, and the audio is also distorted.  It sounds tinny and incredibly compressed.  I have experimented with different audio encoding rates, as well as different settings in the capture card section of mythtv-config.  Any suggestions would be greatly appreciated!!

7.04
Hauppauge WINTV401 PCI Interface TV/FM Tuner Card

The card did not have these problems in Windows, so I am assuming the hardware is fine.

edit:  mythtv-setup instead of mythtv-config

---

### Post by superm1 on 2007-04-24
The video at least sounds to me like the famous bug with ATI Radeon's and broken video overlay for certain video types.[COLOR=Yellow] Correct?[/COLOR]

---

### Post by t00th on 2007-04-24
I'm guessing the phrase "famous bug" means I won't be fixing it any time soon.

---

### Post by NT4usB on 2007-04-24
I fixed the blue tint on mine by using the correct screen section tvoutformat and tvstandard options.
In my case, tvstandard HD480i fixed it.


superm1, are you physic? I don't see any reference to ATi in the original post, how did you know?

ed: the settings are in xorg.conf, btw.

---

### Post by superm1 on 2007-04-24
Well it broke for ATI drivers last year some time around 8.28.8 or so.  I've seen several instances of it.  It will effect other apps using the video overlay playing back that particular format too.

The solution described above is for when doing TV out and *everything* is blue, not just video which afaik is a different problem.  If that is your problem, use the above solution.  Otherwise, there is a specialized libmyth available on a bug on launchpad (i'll have to find it though) that is compiled with a workaround.  This will only make libmyth better however, and you will still encounter the problem with other video players.

---

### Post by t00th on 2007-04-24
I do indeed have an ATi card.  I probably should have included that.  I probably also should have said that the blue tint does not exist in other players such as TVTime.

---

### Post by NT4usB on 2007-04-24
It was tvout that was feeling down.
I spent hours and hours googling 'blue' (not a particularly discrete keyword to search with) before I found the solution to my blues.
So, I figure the more places it gets posted, the better luck the next guy googling it will have.

Why do I feel like I'm watching Jeopardy?
First, superm1 posts the answer, then t00th posts the information. *g*
btw, thanks superm1 for getting to know Myth and sharing what you've learned.

---

