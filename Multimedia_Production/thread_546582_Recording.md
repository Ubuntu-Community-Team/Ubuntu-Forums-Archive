---
title: "Recording"
date: 2007-09-09
forum: Multimedia Production
---

### Post by CapitanYochua on 2007-09-09
How do you record with Ardour 2 in Ubuntu Studio?
I made a track and it let me record, but playing it back I can't hear anything. Though my volume is on.

---

### Post by 5-HT on 2007-09-09
A couple things to check: 
-mixer levels
-output channels (configured via jack)
cheers,

---

### Post by CapitanYochua on 2007-09-09
Well everything in alsamixer is unmuted and around 80 in volume. How do output channels (configured via jack). I'm not that familiar with Jack either. I did start it though prior to opening ardour.

---

### Post by CapitanYochua on 2007-09-09
I think it has something to do with my setup in Jack. Any help?

---

### Post by krissovo on 2007-09-10
Open up Patchage and make shure that there is a connection to the main output

---

### Post by CapitanYochua on 2007-09-10
> **krissovo said:**
> Open up Patchage and make shure that there is a connection to the main output
Output from patchage command. 

Loading configuration file /home/joshua/.patchagerc
Unable to load file /home/joshua/.patchagerc!
could not connect to jack server.
terminate called without an active exception
Connecting to Jack... Aborted (core dumped)


 Now what?

---

### Post by stmiller on 2007-09-12
Use the program qjackctl to configure and start jack before Ardour.

---

### Post by CapitanYochua on 2007-09-13
I figured a way to make it work. I type in command aumix. Lower PCM and raise Igain and then I can record. Then go back and reverse what I did to hear it when I playback. Is that normal/ proper to do?

---

### Post by kayosiii on 2007-09-13
Very strange.... If jack is not running you should not be able to Ardour at all - are you sure you don't mean Audacity?

---

### Post by CapitanYochua on 2007-09-13
Positive.

---

