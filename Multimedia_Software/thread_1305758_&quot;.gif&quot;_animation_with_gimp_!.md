---
title: "&quot;.gif&quot; animation with gimp !?"
date: 2009-10-30
forum: Multimedia Software
---

### Post by mechanicaldesign on 2009-10-30
Hello to everibody,

Can somebody tell me how I can create some ".gif" animation using multiple layers, like pictures (.jpg, .png,etc.).

I waiting yours suggestions, opinions and ideas.

Thank you in advance for yours supports.

Best regards.:(

---

### Post by kaibob on 2009-10-30
I don't know how to create animated gif's with gimp. You can do it with the Imagemagick convert utility as shown below. You have to change *.png to *.jpg or whatever applies.

```
convert -delay 100 -loop 0 *.png output.gif
```

BTW, I'm not sure what you mean when you refer to multiple layers. Perhaps I don't understand what you want to do.

---

### Post by mechanicaldesign on 2009-10-30
Hi [kaibob]("http://ubuntuforums.org/member.php?u=595193"),

Maybe my explication is not clear, admit this. [SIZE=4]**In fact I have 30 pictures, which I want to assembly in an animation. This animation I want to be ".gif" format**[/SIZE]. I hope in this moment everything is very clear for all people who want to help me and to offer me an real support.

I waiting yours suggestions, opinions and ideas.

Thank you in advance for yours supports.

Best regards.:sad:

---

### Post by kaibob on 2009-10-30
> **mechanicaldesign said:**
> Hi [kaibob]("http://ubuntuforums.org/member.php?u=595193"),

Maybe my explication is not clear, admit this. In fact I have 30 pictures, which I want to assembly in an animation. This animation I want to be ".gif" format. I hope in this moment everything is very clear for all people who want to help me and to offer me an real support.

I waiting yours suggestions, opinions and ideas.

Thank you in advance for yours supports.

Best regards.

The command line I included in my earlier post will do exactly what you want.

---

### Post by mechanicaldesign on 2009-10-31
Hi [kaibob]("http://ubuntuforums.org/member.php?u=595193"),

I try the command indicated by you, but I obtained a gif picture, not a gif animation. I need maybe an command which I can create an gif animation with my pictures.

Best regards.:(

---

### Post by kaibob on 2009-10-31
I have used the command in the past to create animated gifs, and ran a test with a few jpg files just a few minutes ago, so I know that it does work. Are you sure that you are using a viewer that will display animated gifs? Not all do. Try opening the gif in firefox.

---

### Post by emigrant on 2009-10-31
@ [mechanicaldesign]("http://ubuntuforums.org/member.php?u=884788") as far as i know this is impossible in gimp.
you have to have adobe photoshop and adobe imagready (CS).
once the layers are set in the proper order in PS, take them to IR (by clicking go to image ready at the bottom of the tool box).
there in the animation window click the arrow button at the top right corner and select 'make frames from layers" and you see all your layers are brought in to the animation window.
and also you can set the timing for each frame.
now if you click play, all the frames would play,

NB: iv tried installing PS and IR (IR CS usually automatically get installed along with PS CS if you are in windows) through wine in fedora and ended up in only PS working.
not sure how it goes in ubuntu.

the only option is to do it in MS.

hope that helps.

---

### Post by braete on 2009-10-31
EASY
just put the pics you want to animate in different layers and in the layer name add at the end ```
(100ms)
``` or any other delay you want(in ms). that will be the time the animation displays that frame

also from the filters menu, chose animation then do both optimizations to get smaller files

edit: dont forget at the end to save in .gif format :)
i usualy forget ahaha

---

### Post by emigrant on 2009-10-31
wow so this is one of the things i ever wondered to do in linux and is now there in gimp :D

---

### Post by mechanicaldesign on 2009-10-31
Hello to everibody,

I made the gif animation.

I will put here the very steps which I followed to made the gif animations.

But not now. Tomorrow.

Best regards

---

### Post by heartsoulofra on 2009-11-27
Gimp is a good software and are fairly recommended in creation of animated gifs. If you want you can also create gifs via website tool in wegif.

---

### Post by ceciliaFX on 2009-12-08
> **emigrant said:**
> wow so this is one of the things i ever wondered to do in linux and is now there in gimp :D
GIMP has been able to make gif anims for years

what I WANT it to do is make APNGs (animated pngs)

---

### Post by fatboxes on 2009-12-08
> **ceciliaFX said:**
> GIMP has been able to make gif anims for years

what I WANT it to do is make APNGs (animated pngs)
Gimp can't do this... YET!
-\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/\/-
Here are the complete steps for making a .GIF file. All the other instructions on here miss a step or not helpful.

1. Open all the picture's you would like to use in your animation as Layers (**FILE>OPEN AS LAYERS**) you can open multiple at a time (<shift> or <ctrl> +click)
2. After you have the layers in the order you want (note: you can reverse the order by LAYERS>STACK>REVERSE LAYER ORDER), you can adjust the time of each frame by **RIGHT CLICK>EDIT LAYER ATTRIBUTES** then change the time (in milliseconds) to a different number 
3. Save as (**FILE>SAVE AS**) You can either click on the **SELECT FILE TYPE** and choose .GIF or just type .GIF at the end of your file name.
4. You must click **SAVE AS ANIMATION** then **EXPORT** then **SAVE**
(also, to save a huge amount of space make sure to optimise both for "gif" and "difference" (**FILTER>ANIMATION**)

---

