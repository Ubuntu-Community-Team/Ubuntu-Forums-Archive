---
title: "Sound is Mute at 75%"
date: 2012-04-30
forum: Multimedia Software
---

### Post by marshalldc on 2012-04-30
I just finished installing 12.04 on my laptop and everything works fine but the sound. If you look at the sound meter at 75%, it's totally off. And at the 100%, it's as loud as it can be. There is no sound at 0% to 75%.

If you go into alsamixer, and press the volume buttons, you can see it makes jumps of about 20% every time the volume button is pressed until it reaches zero. 

Does anyone know how to adjust this?

---

### Post by Enigmapond on 2012-04-30
Try deleting the file .pulse in your home folder. It's hidden. It will just redo itself but with default parameters.

---

### Post by marshalldc on 2012-04-30
I deleted the directory and even rebooted. It's still the same.

---

