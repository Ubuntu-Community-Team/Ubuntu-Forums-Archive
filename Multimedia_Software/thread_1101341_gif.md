---
title: "gif"
date: 2009-03-20
forum: Multimedia Software
---

### Post by uttaran on 2009-03-20
why don't animated gif images animate in ubuntu?

---

### Post by albandy on 2009-03-20
could you describe your problem

---

### Post by mcduck on 2009-03-20
> **uttaran said:**
> why don't animated gif images animate in ubuntu?

Yes they do. You just have to open them with some program that support animated gifs.. ;)

Firefox, for example.

---

### Post by lukjad on 2009-03-20
Go to the terminal and type:
```
animate
```

Then, when you are prompted to *Browse and Select a File*, do just that. The select the file and click on Animate.

---

### Post by uttaran on 2009-03-21
I used gthumb instead.Yet thanks

---

### Post by neu2buntu on 2009-04-15
i tried both "animated" and "gthumb" and "animated" was exactly what i was looking for to play animated .gif images with no strings attached.

 "gthumb" was more of a file browser than anything,but may suit some peoples needs...   "animated" ran a program "Image-Magick" (not sure if i installed this myself or it is part of the default ubuntu8.10 install) and it wrapped a frame around my .gif that i created in "GIMP"

i then used the command ```
animate ~/Desktop/MyFile.gif 
```obviously my .gif was on the Desktop and the "image-magick" search window was not needed as the path was set in the command above......    anyway thanks guys now i can have my .gif images play right from startup,no more need to load with my web browsers.):P

---

