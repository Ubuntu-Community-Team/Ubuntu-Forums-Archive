---
title: "Problem with Ardour/JACK"
date: 2007-06-17
forum: Multimedia Production
---

### Post by linuxmann on 2007-06-17
I installed ardour using synaptic. I have noticed that it has installed jack with it also. I clicked on the  ardour icon in the sound and video section, and it says the following. I tried the gtk and i686 versions and the same message shows up. I need help here.
--------------------------------------------------------
Ardour Unplugged

Ardour could not connect to JACK.
There are several possible reasons:

1) JACK is not running
2) JACK is running as another user, perhaps root.
3) There is already another client called "ardour".

Please consider the possibilities, and perhaps (re)start JACK.

---

### Post by christhemonkey on 2007-06-17
Please install qjackctl:
```
sudo apt-get install qjackctl 
```

Then launch it from:
"Applications" > "Sound and Video" > "JACK Control"

Then configure and start the JACK sound server,

finally start Ardour.

---

### Post by UncleFoo on 2007-06-18
Not to totally derail the thread, but I have a question about Jack/Ardour as well. When I start Jack/Ardour nothing else can use the sound card. Even after I shut both apps down, I have no sound. I need to re-boot to get my sound back. I looked to see what might still be running as a background process, but I didn't recognize anything.

Any thoughts?

---

### Post by christhemonkey on 2007-06-18
Sounds like JACK is still running somehow.

Try running:
```
sudo killall jackd 
```

---

