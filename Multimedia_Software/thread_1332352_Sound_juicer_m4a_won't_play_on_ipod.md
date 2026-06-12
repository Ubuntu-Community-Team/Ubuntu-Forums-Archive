---
title: "Sound juicer m4a won't play on ipod"
date: 2009-11-20
forum: Multimedia Software
---

### Post by WileyGaia on 2009-11-20
Hi
I have done lots of searching for this problem but can't come right. I have also followed the instructions written here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

but still no success.

I rip music cd's using Sound Juicer (in m4a format), they play just fine on Rhythmbox, but when I send them to my Ipod, the Ipod will not play them... (they are recognised by the ipod, just "ignored" when selected...

running 8.10
Anyone got a fix? thanks...

---

### Post by mc4man on 2009-11-20
It's been awhile but i believe gstreamer is using the wrong profile for aac.

Your easiest solution would be to use a better ripper, grip, rubyripper, abcde.
grip would be the easiest to use and is in the repo, look in synaptic.

Otherwise you could ck. on the gstreamer profile ( though I don't use gstreamer apps so maybe get some confirmation, a bit of a guess here

One way would be thru gconf-editor
See screen one, if your profile says ! faac profile=1 ! then edit the key and change the 1 to 2 ( and nothing else

I'd be careful editing gstreamer keys and again maybe see what others say.

(personally, any of the rippers mentioned are far superior to sound-juicer

---

### Post by WileyGaia on 2009-11-23
OK - thanks, I think I will try one of the other rippers... will provide feedback when done (may take a few days as the ipod has to go in for a battery problem)

---

### Post by WileyGaia on 2009-12-08
Well, the ipod is still not back - apparently they are waiting for a "spare part" (I guess the battery) - servie in Sth Africa isn't great at the best of times, but at least they are repairing it under warranty. but thats off topic. In the meantime, what I have found is that I do not have profile=1 OR profile=2 i.e. there is no "profile" at all in the conf setting you referred me to... - I guess I should add it in?
Original setting is:
audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4

I have checked out grip - I will use this now, but will only be able to test if it works with th nano when I get it back... will post feedback when I get that done... Africa time

---

### Post by WileyGaia on 2009-12-17
so - the ipod is back! in fact they replaced it...:-) 

and i have ripped a few cd's using grip, and dragged and dropped to the ipod, and it is ALL GOOD, problem solved! It seems that the m4a format that grip uses has sorted this problem out, thanks for the suggestion mc4man!

---

