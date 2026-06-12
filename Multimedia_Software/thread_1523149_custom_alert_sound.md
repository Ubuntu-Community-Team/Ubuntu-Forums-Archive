---
title: "custom alert sound"
date: 2010-07-03
forum: Multimedia Software
---

### Post by shantanu18 on 2010-07-03
I am using 9.10(64bit). I want to add custom .wav sound as system sound theme.i.e when i close a program ubuntu will play a sound(custom).
I can't find any option on sound preference menu. I searched in google but failed to find any useful post.
please help!;)

---

### Post by caspertk on 2010-08-05
I'm not sure if this will work in 9.04 because it's been a while since I've had that version. But in 10.04, I added a custom start up sound (imperial march :D)

So first off make your file, and make sure it is saved in ogg format. Then go to System => Preferences => Startup Applications. Once you have the window up scroll down until you find "GNOME login sound". Click so it's highlighted and press edit on the right side of the window. 

The part you need to edit looks like this --id="star-wars"
Mine says star-wars because that's the name of my ogg file. I think by default it's called login-sound or something like that. So change it to the name of your file, and exclude the .ogg. 

ie. your file name is "scapegoat.ogg" you need to type "scapegoat".

After that, navigate to /usr/share/sounds/ubuntu/stereo and paste your audio file in there. Close everything out, log out, make sure the volume is up, log in and you should hear your file!

---

