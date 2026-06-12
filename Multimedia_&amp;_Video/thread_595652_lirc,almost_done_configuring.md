---
title: "lirc,almost done configuring"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by metalspider on 2007-10-29
got to the final stage of configuring lirc on ubuntu,buttons presses are read however whatever i do i cant get rid of them repeating to fast,
for example i press pause and it pauses for half a second and then continues playing.
tryed editing the .lircrc file values of repeat and delay but it hasnt helped,how do i get the buttons to work properly?

thanks

edit:
probably should mention this,when i check the output with irw each button press gets 2 lines of output no matter how fast i press,lircd.conf shows my remote has no stop bit.

---

### Post by metalspider on 2007-10-29
anyone?

---

### Post by metalspider on 2007-12-08
anyone?

---

### Post by Mohonri on 2008-03-30
I might be able to help  (I'm struggling through some of my own lirc problems at the moment).  In your .lircrc file, you can add a "repeat = x" for each button, where x is the number of repeated commands to ignore.  So, for example, for one key you might have:
```
begin
  prog=mythtv
  button=vol-
  repeat=3
  config=F10
end
```

---

### Post by chocolatetoothpaste on 2008-04-08
I am also having issues with repeating commands.  Setting repeat seems to do nothing.  This issue is expressed across several threads, and no one seems to know what is up.  I wonder if it may have something to do with the hardy package.  I may try compiling from source, as this is a frustrating issue.  If anyone has some ideas, please, enlighten us.

---

