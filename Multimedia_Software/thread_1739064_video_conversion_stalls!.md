---
title: "video conversion stalls!"
date: 2011-04-25
forum: Multimedia Software
---

### Post by btbaus on 2011-04-25
yup! video conversion stalls with oggconvet and transmageddon! ive attached  a screenshot. notice ZERO processor activity! ive successfully converted one video with oggconvert, and i havent been able to convert any others since!

---

### Post by handy on 2011-04-25
How much RAM do you have?

You could install htop, & have a look at the system resources being used when the video is being transcoded it may give you a clue.

---

### Post by btbaus on 2011-04-26
thanks ill look for htop and try it out. i got 8gb ram!! intel i5 processor

---

### Post by btbaus on 2011-04-26
i noticed that when the conversion stalls, the python process in the system shows no activity.
during conversion, the python process is using about 250-300% of the cpu. problem with python? wtf, this sucks. ima try only having one video conversion program installed. maybe its a conflict with library's or sumthin.

---

### Post by btbaus on 2011-04-26
okay doesnt matter if i only have one converter program, it still stops converting before finished.

---

### Post by handy on 2011-04-26
This is a shot in the dark.

I wonder whether there is any kind of problem relating to the python version being used & what your system supports? As python 3, has been out for a while now, & it is not backward compatible with python 2. (As I said, a shot in the dark.)

If you start the software from the Terminal, does it give you any messages that would give any clues?

---

### Post by btbaus on 2011-04-29
ohh yeah, starting it from the terminal: Message: pygobject_register_sinkfunc_ is deprecated (GstObject).

what does it mean??!??!?!?! running python version 2.6.6

---

### Post by handy on 2011-04-29
It sounds like the software you are trying to use may require Python 3.* to be installed on your machine.

On Arch I have both Python 2.* & 3.*, installed, they live happily together in the same system.

I just did a quick search & pulled this one off of the top:

[http://diveintopython3.org/installing-python.html](http://diveintopython3.org/installing-python.html)

If you scroll down the page it gets to installing Python 3. on Ubuntu.

***[edit:]** You don't need to install IDLE, unless you are going to be using it to write Python code.*

---

### Post by btbaus on 2011-05-07
hey thanks for your help. i think im just gonna use mencoder and ffmmpeg. theyre a lot quicker than transmageddon ever was.

---

