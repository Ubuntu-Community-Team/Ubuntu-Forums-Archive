---
title: "qsynth + jack"
date: 2010-11-24
forum: Multimedia Software
---

### Post by thesuker on 2010-11-24
I run jackctl, start the server, works fine.  I run qsynth, in setup I set audio driver to jack.  I go to jackctl and check the connections, but qsynth doesnt appear in the list :S  rakarrack, for example, appears fine, so i'm guessing its not a jack problem.  not a clue what to do.  

btw, I keep getting this message: fluidsynth: error: Help! Lost the connection to the JACK server

fixed it by changing timeout on jack to 2000ms

---

