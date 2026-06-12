---
title: "No sound from auidgy 1 under 7.04"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by xhero0 on 2007-08-19
greetings,

Now that I got my screen size almost right, it's time to tackle another major issue:

I am unable tog et my Creative auidgy1 to do something beside nothing, no sound, squat, I even get a nifty error msg: 
<>
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
<>
I get this example from when I go to SYSTEM/SOUND PREFERENCES and select test from my alsa driver. auto detect does NOT do this but I still get no sound.

Any ideas for help??

I have been here to t-shoot this and to no avail
[http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy](http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy)

Thanx!

joe

---

### Post by bakster on 2007-08-19
I have Audigy 1 and I also had no sound on first boot.Problem is spdif (digital output) that is turned on by default.Open volume mixer and uncheck Audigy Analog/Digital Output Jack.
(It's under switches tab).This problem is not Ubuntu specific.I had same problem in fedora 7 and PCLosOS.

---

### Post by xhero0 on 2007-08-19
Well I managed tog et sound to work... I installed 'jack' and played witht at for a bit... but whats the weird part I have to have it on autodetect for it to work, if I set it to alsa driver I still get the same error msg....

Friggin weird!

thanx for the assistance!

joe...

---

