---
title: "zynaddsubfx and keyboard input"
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by mizar001 on 2007-07-31
Hello. I'm using zynaddsubfx with jackd in realtime mode. I use the keyboard (well the pc keyboard) to test some melodies, but if i press a key for more than 1 seconds or two the sounds are like restarting at random time, like i pressed again and again the key.

The problem was the same without jack and with other keyboard as well.


Anyone experienced this problem ? I have the same problem at work with a really different hardware.

---

### Post by stateq2 on 2007-08-11
I'm having the exact same problem.  I'm guessing that it's because when you hold a key down, it automatically repeats that input....like it does when you type text.  Anyone have any solutions?

---

### Post by mizar001 on 2007-08-13
Not really, Typing on a window event is not like typing on a text window. The time from the irst pulse and the second are the same. 

However that's would be a problem for the first time i press a key, but my problem is that the sound is self restarting indefinetely when i maintain the key down.

For example i take the Q key down and it play C note... and after some time it restart the note like i was tapping the key... and this is repeating randomly.

What the hell is this ?

---

### Post by stateq2 on 2007-08-20
I understand what you're saying.  As I said before, I'm having the exact same problem.  It's probably because of the automatic repeating of the keyboard input that is handled at the xorg level.  

The fact the it repeats randomly shows that it's a bug in the virtual keyboard code, and the input is not properly handled at the application level.....especially considering that this problem doesn't exist when using the mouse to hold down the keys on the virtual keyboard.  

It probably hasn't been addressed because most people use zynaddsubfx w/ a midi controller.

---

