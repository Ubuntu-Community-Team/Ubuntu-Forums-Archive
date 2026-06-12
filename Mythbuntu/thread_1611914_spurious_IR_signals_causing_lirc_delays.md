---
title: "spurious IR signals causing lirc delays"
date: 2010-11-02
forum: Mythbuntu
---

### Post by cedyathome on 2010-11-02
The behavior started a couple of months ago, but I don't know the exact update that caused it. I suspect it was right after I updated to 10.04

I use a StreamZap remote & it has been working just fine for most of the year.

It looks like my lcd TV generates random IR signals when turned on (after being allowed to sit idle for a few hours)

1. This causes the streamzap receiver's red LED to go into a random,  fast blinking pattern. Until this blinking stops, all Streamzap remote  button presses are ignored. irw & mythtv see no keys until this blinking stops.

 2. Once lirc & mythtv starts seeing the keys - after anywhere from 15 to 45 seconds, it works fine, until I stop watching & the TV is off for a couple of hours.

What could be going on? What component is responsible for filtering out the noise?

My [I]/etc/lirc/lircd.conf has one line 
include "/usr/share/lirc/remotes/streamzap/lircd.conf.streamzap"
   [/I]
I have not changed this file or the ~/.lirc file. I edited teh  ~/.lirc/mythtv file when I configured my remote and have made no other  changes
Using top, I see lirc in memory & running when the LED is blinking randomly

I've read another LIRC related topics recently, and this problem seems to be different.
[http://ubuntuforums.org/showthread.php?t=1596778](http://ubuntuforums.org/showthread.php?t=1596778)

Please help.[I][FONT=Arial]
  [/FONT][/I]

---

### Post by PhilWig on 2010-11-02
I'm almost afraid of introducing a total red herring, it's not your room lighting is it?  My MCE remote flashes continually if pointed anywhere near the new gas discharge based energy saving lamps mandated by European legislation.

Phil

---

### Post by cedyathome on 2010-11-02
It is definitely the TV. As soon as I turn it on, I can see the red-light on the IR receiver dongle start to flicker.

The question is - why is this causing an issue with LIRC? Can't it filter out the noise and focus on the signal from the remote?

And more importantly, is there anything I can do to fix this issue. It is a major annoyance, but doesn't affect functionality.

---

