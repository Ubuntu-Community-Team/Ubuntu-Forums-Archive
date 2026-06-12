---
title: "Problems editing photos"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by mhanraha on 2007-12-29
I'm having difficulty rotating photos taken with my digital camera.  The default image viewer will rotate the photo, but when i attempt to save it, my computer will start to lag, and eventually the program seems to exit.  If I attempt to even load the photo in gimp, the computer gets laggy.  I feel like I should have a sufficient system to do this.  Has anyone else experienced this problem?

---

### Post by FakeOutdoorsman on 2007-12-29
What is your system hardware?  Does it lag when doing other tasks other than image rotation?

Open a terminal and start the program from the command-line.  This way you can view any errors.  Open another terminal and run the command "top" while you are editing the image.  The program that is taking up the most CPU will be listed first.

---

### Post by mellowd on 2007-12-29
What application are you using to edit?

---

### Post by DirtDawg on 2007-12-29
If your camera is set to take high quality photos, the size of your photos may be very large. This can cause your computer to strain a bit. Try opening the photo in Gimp, then using Image>ScaleImage to reduce its size. It may then be easier to manipulate it further.

---

### Post by mhanraha on 2007-12-29
Alright, so system has never lagged like this before.  I first tried opening it with image viewer, and rotating it, the picture rotated without a problem, but when I tried to save the photo that's when the computer just got hung up on the "saving photo 1".  I also tried gimp, with this error

/usr/lib/gimp/2.0/plug-ins/jpeg

---

