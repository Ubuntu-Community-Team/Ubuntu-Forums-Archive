---
title: "GIMP and GIF animations"
date: 2012-11-28
forum: Multimedia Software
---

### Post by Omo on 2012-11-28
I was trying to use GIMP (v.2.6.8 in Ubuntu 10.04) to copy one frame from a GIF animation, and the process was a fail. I couldn't bring up any frame to view, other than the initial frame, showing as background, no matter what I clicked on, in the Layers window. I don't remember this problem in the older version I use with Ubuntu 8.04. Absent any useful advice online or in their manuals, it looks like I may have to try an older Windows version in WINE or the Paint Shop Pro I used in Windows. (I'm assuming from the get-go that an attempt to install GIMP 2.4 in Lucid would be a fail because of dependencies)

---

### Post by shantiq on 2012-11-28
hi omo   [**this**]("http://askubuntu.com/questions/101526/how-can-i-split-an-animated-gif-file-into-its-component-frames") should help you

```
convert animation.gif target.png
```


will split it in png[s] pick the one you want delete the rest
you will need > sudo apt-get install imagemagick if not yet installed

---

### Post by Omo on 2012-11-28
Thank you kindly. It appears that GIMP's capabilities are more geared to the creation of new animations, using their own image formats, instead of any real ability to manipulate existing GIF animations, as was effortlessly done with Paint Shop Pro's companion Animation Shop.

---

### Post by SeijiSensei on 2012-11-28
Open the Layers window and push the frame you want to manipulate to the top of the stack using the up arrow button.  Once it's on top, you can edit it to your hearts content.  Then push it back down to its correct location when you are done.

If you want to add a frame to an existing animated GIF, you need to be working with an animation that has not yet been differenced.  If all the frames of the original are intact, open the source material, use Select All, then Copy, move to the target and choose Paste As Layer.  Now use the up/down arrow keys in the Layers window to put the new layer where you want it in the sequence.

If you're not sure what I mean by "differenced" take a look at this avatar (from [Summer Wars]("http://www.funimation.com/summer-wars/videos")):

[img]http://www.takinganimeseriously.com/images/avatars/summer-wars-daisuke-fan.gif[/img]

Open this in GIMP and look at the layers.  You'll see that most frames are not intact; each frame only contains differences between it and the background frame.  Adding layers to an already-differenced GIF like this is pretty much impossible.

---

### Post by shantiq on 2012-11-29
wow   Sensei indeed!!   thanx for the info Master
Imagemagick might be a tad faster here but the question was about Gimp
Gimp is an astounding program with many hidden doors:)

Once brought to the top copy layer/edit/paste as new image 

Nice!

---

### Post by Omo on 2012-11-29
> **SeijiSensei said:**
> Open the Layers window and push the frame you want to manipulate to the top of the stack using the up arrow button.  Once it's on top, you can edit it to your hearts content.  Then push it back down to its correct location when you are done.

If you want to add a frame to an existing animated GIF, you need to be working with an animation that has not yet been differenced.  If all the frames of the original are intact, open the source material, use Select All, then Copy, move to the target and choose Paste As Layer.  Now use the up/down arrow keys in the Layers window to put the new layer where you want it in the sequence.

If you're not sure what I mean by "differenced" take a look at this avatar (from [Summer Wars]("http://www.funimation.com/summer-wars/videos")):

[IMG]http://www.takinganimeseriously.com/images/avatars/summer-wars-daisuke-fan.gif[/IMG]

Open this in GIMP and look at the layers.  You'll see that most frames are not intact; each frame only contains differences between it and the background frame.  Adding layers to an already-differenced GIF like this is pretty much impossible.Thank you for the explanation of the differenced GIF. The incomplete look of some of the frames I saw now makes sense. I did try to convert the GIF to something more GIMP-friendly by saving it as a XCF file, but doing that failed to give 'proper' names to each individual frame, as subsequent error messages informed me.

Since I am somewhat deficient in command-line operations, I'm still looking for a GUI for animation manipulation, as my attempt to use Paint Shop Pro 7 in WINE 1.0  was a fail (it installed but the programs don't open beyond the intro window)

I see that there is a GUI offered for Imagemagick named Converseen, that may provide me with a workaround for my current difficulties with GIMP. Has anyone here ever tried it?

---

### Post by SeijiSensei on 2012-11-29
As I said, if the original animated gif is differenced, your options for editing are *very* limited, regardless of the software you use.  If you have access to the original pre-differenced source where each frame is complete, you should be working with that.

---

