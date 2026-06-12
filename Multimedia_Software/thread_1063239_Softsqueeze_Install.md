---
title: "Softsqueeze Install?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by Osamabingandhi on 2009-02-07
I'm so close i can almost smell it. I've got 64-bit java installed i can see the softsqueeze applet but there is a connection failure and when the applet starts all sound is gone.

So i have been trying to install the softsqueeze from the .rpm feodora file with alien but it don't work it says it ends too early when i am converting.

When i put this [http://localhost:9000/html/softsqueeze/applet.html](http://localhost:9000/html/softsqueeze/applet.html) in firefox the java just spins round and round and never stops loading. 

When i put this file:///opt/Softsqueeze/applet.html the applet loads but there is a connection problem and when i reload it says there is no soundcard. (Java works with sound in other applets)

Why oh why did i install 64-bit ubuntu....huge misstake, no advantages only more work!

I truly don't know what to do, install a broken rpm or is there a way to get the java applet to work?

Help would be awesome!!!

---

### Post by Osamabingandhi on 2009-02-07
I found the solution, i knew i was close but the last thing i did before i gave up worked! You simply have to start softsqueeze from squeezecenter in firefox under extras.Firstly it didn't recognize that i had the right java installed, but then it did...Then i pressed the button and a file pops up you have to open it with javaws. I installed java under /opt/jre1.6.0_12/javaws/javaws. Then it installs itself and an icon shows up on the Desktop....

I feel a bit foolish but anyway there was a simple solution, which is always good.

---

