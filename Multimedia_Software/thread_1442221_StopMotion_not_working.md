---
title: "StopMotion not working?"
date: 2010-03-29
forum: Multimedia Software
---

### Post by Scris101 on 2010-03-29
so i installed stopmotion because i always used to do this on my windows machine, im using a logitech quick cam for it and for some reason, when i load up stopmotion the screen where the image should be is just black, can anyone tell me why this is happening. i went to prefrences and made sure my webcam is selected

---

### Post by Scris101 on 2010-03-29
bump, can anyone please help me?

---

### Post by Scris101 on 2010-03-30
really no one is even trying to help me?

---

### Post by LuridCinema on 2010-03-30
Can you get any other program to "see" your cam ? are you getting video from it ? Cheese ...etc ? Maybe google ubuntu and the name & model # of your cam and see what turns up.


Please post any error messages and the settings you selected in the setup on StopMotion

Id also make sure you have all of the "depends" & recommended progs installled at: [http://ns2.canonical.com/karmic/x11/stopmotion](http://ns2.canonical.com/karmic/x11/stopmotion)

---

### Post by Scris101 on 2010-03-30
yes, in cheese i can use my webcam, on stop motion i cant. im not getting any errors, just nothing shows up

---

### Post by Alan A on 2010-04-02
It could be that your webcam does not use any of the colour pallets supported by vgrabbj (the utility used to do the actual image capture).
This seemed to be the case for me when I first tried the stopmotion application with a cheap no-name webcam.

Try running the following from the command line to see if it reports any errors:-

```
vgrabbj -i vga -o png -d /dev/video0 -D 7 > temp.png
```

where video0 is your web cam device (probably video0).
If this works, it should create a new image called temp.png in the current directory which has been "grabbed" from the webcam.

If this does not work, try running the following:-

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so vgrabbj -i vga -o png -d /dev/video0 -D 7 > temp.png
```

Again, this should create the temp.png image in the current directory.
If neither of these work, you are probably out of luck for this particular application.

---

