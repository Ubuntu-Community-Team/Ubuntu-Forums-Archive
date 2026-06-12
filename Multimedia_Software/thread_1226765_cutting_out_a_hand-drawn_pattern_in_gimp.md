---
title: "cutting out a hand-drawn pattern in gimp"
date: 2009-07-29
forum: Multimedia Software
---

### Post by iochinome on 2009-07-29
hey guys, so i am working with gimp on my first project here and wasnt able to figure this out: i want to cut out everything from an image but a tree, and leave the rest of the image as just a white (clear would be nice, as i intend to put it into another image) background. i know how to draw a lasso around it, telling the program that i have selected the region, but the crop tool seems to only accept square regions. how do i do this?

just for further info, if anyone can suggest a way to do this, what i am trying to do is cut out a tree from one image and put it into another. thanks!

---

### Post by SteveDee on 2009-07-30
I hope I understand your question.

I've just tried this, and it works as follows:-
- Select the "Free Select" tool
- press & hold left mouse button while drawing around the object
- when you get back to the starting point, release mouse button (the selected area should be enclosed by a dashed line)
- select menu Edit > Copy
- open a second image file or create a new blank image
- select menu Edit > Paste Into

The pasted image will be just what you selected, but with an outer rectangular selection box (which allows you to move it around).

You may have been selecting your object then going to menu Image > Crop To Selection. This does give a rectangular selected area, which is not what you want.

---

