---
title: "MIcrophone Help"
date: 2009-11-05
forum: Multimedia Software
---

### Post by Waldvogel on 2009-11-05
I have an inbuilt microphone on this laptop which works fine when I am on Windows but is inactive on Ubuntu. Can I activate it?

---

### Post by ajgreeny on 2009-11-05
If on karmic, I think the easiest way is to use alsamixer and make sure the mic sliders are set high enough.  Alsamixer is a terminal app, so you need to use the cursor arrows to move from slider to slider, and raise or lower the sliders, and "M" to mute or unmute things such as the mic.

---

### Post by Waldvogel on 2009-11-07
I don't know what karmic is.
I just upgraded to ubuntu 9.10 but it still is the same problem.

---

### Post by Waldvogel on 2009-11-08
Please help!

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-11-08
I have the same problem on my laptop. 
The internal microphone when boosted records only white noise.
However plugging in an external one works just fine .

---

### Post by Waldvogel on 2009-11-13
OK then, perhaps Ubuntu isn't as good as I hoped.

Luckily  I still have Windows.

---

### Post by ScribeAmos on 2009-11-13
An issue might be telling ubuntu to turn your mic volume up.  If you open your terminal and run the command:

alsamixer

then it brings up the alsamixer so that you can turn your mic up.  Just scroll right and left to the device you want to adjust the volume, up and down arrow key to adjust the volume, and escape to exit.

---

### Post by Waldvogel on 2009-11-14
It doesn't recognise a microphone though.

---

### Post by Waldvogel on 2009-11-15
What I mean is, it doesn't recognise the *internal *microphone.

---

### Post by Jimtheplanner on 2009-11-15
Ok Try this....

Go to system => preferences => Sound then look at the input tab does it list your microphone?

If so you can make sure the mute is not checked. You can also increase the gain by moving the slider up from left to right.

Any good???

---

