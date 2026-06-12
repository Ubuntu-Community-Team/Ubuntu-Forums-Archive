---
title: "looking for tool to quickly crop an image"
date: 2019-10-04
forum: Multimedia Software
---

### Post by Skaperen on 2019-10-04
i often have an image and want to crop out just part of it to post online because other parts i do not want to post for various reasons.  i have been doing this with [FONT=courier new][COLOR=#006400]**gimp**[/COLOR][/FONT].  with [COLOR=#006400][FONT=courier new]**gimp**[/FONT][/COLOR] it is not quick because [COLOR=#006400][FONT=courier new]**gimp**[/FONT][/COLOR] has so much for major image editing and compositioning.  for the quick crops i want a program that does cropping and nothing else.  that's what i mean by simple.  i would see the full image and outline a rectangle on it, crop it, then save the crop under a different name.  if it can do this with videos, that's a plus, but not essential.  it should show the size as the rectangle is being positioned.  being able to resize the rectangle or slide it around are essential controls.

---

### Post by malspa on 2019-10-05
I've been using Nomacs for quickly cropping images, but not for video.

---

### Post by TheFu on 2019-10-05
No GUI, but I use 
```
NAME
       **convert**  -  convert  between  image formats as well as resize an image,
       blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much
       more.

```
It is part of ImageMagick. There are a few front-ends to it, usually python with a simple GUI.  CropAll and "display" do that. With 'display', just click on the image to see lots of options.  Transform--> Crop.  Crazy tiny and fast.

gThumb and shotwell are other options. I've used shotwell, which has vastly improved the last 5 yrs if you haven't looked recently.

As for cropping videos, **handbrake** does that with a visual queue in the preview.  Some sports I enjoy aren't captured very well - they just setup a video camera to capture the entire area, when less than 25% of that size has any action for some events.  Cropping videos requires re-encoding the entire thing.  **Shotcut** is the new tool of choice for hobby media creators.  I usually do cuts using **mkvmerge** and **handbrake** to transcode down to 25-35% of the original size.

---

### Post by Skaperen on 2019-10-05
if i know in advance where to crop, convert is a great tool for repeated cropping, like a series of photos taken on a tripod, or similar screenshots.  but very often i need to find where to crop.

---

### Post by Skaperen on 2019-10-05
> **malspa said:**
> I've been using Nomacs for quickly cropping images, but not for video.

it's not as easy as i had hoped.  it does a lot more than just crop so i have to activate cropping.  but that's just press "c".  easier than gimp, for sure.  thanks!

---

### Post by Holger_Gehrke on 2019-10-06
> **Skaperen said:**
> if i know in advance where to crop, convert is a great tool for repeated cropping, like a series of photos taken on a tripod, or similar screenshots.  but very often i need to find where to crop.

Please read **all **TheFu posted. 'display' and '[CropAll]("https://github.com/pknowles/cropall")' are graphical frontends for ImageMagick/convert. 'display' is probably already installed on your machine since it's part of IM. Since it's a frontend to most - if not all - functions of IM and its GUI is IMHO somewhat fiddly, it's probably not quite what you're looking for. 'cropall' on the other hand does **cropping and resizing and nothing else**.

Holger

---

### Post by vanadium on 2019-10-06
> **Skaperen said:**
> i would see the full image and outline a rectangle on it, crop it, then save the crop under a different name.  if it can do this with videos, that's a plus, but not essential.  it should show the size as the rectangle is being positioned.  being able to resize the rectangle or slide it around are essential controls.
That is exactly what you can do in Gimp. Select the crop tool (Shortcut key Shift+C), outline your crop, optionally adjust by dragging the sides, and click in the middle when done (or press Enter). To save under another name, and optionally another format, press Shift+Ctrl+E.

---

### Post by ajgreeny on 2019-10-06
I use **gthumb** more than gimp for this simple job, largely because it is quicker to start than gimp, but both do a very similar job.

Unfortunately, in my opinion, gthumb has gone the way of many gnome applications making it more difficult to find your way around it; there are no menus so you have to hover over icons to see what they are, fine if you always use gnome, but for other DE users it's not quite so simple.

Even more simple is **viewnior**, a very small image viewer that has a few edit options including crop, and it works very well.

---

### Post by Skaperen on 2019-10-06
> **Holger_Gehrke said:**
> Please read **all **TheFu posted. 'display' and '[CropAll]("https://github.com/pknowles/cropall")' are graphical frontends for ImageMagick/convert. 'display' is probably already installed on your machine since it's part of IM. Since it's a frontend to most - if not all - functions of IM and its GUI is IMHO somewhat fiddly, it's probably not quite what you're looking for. 'cropall' on the other hand does **cropping and resizing and nothing else**.

Holger

i misread his post the first time - sorry about that.

i do have [COLOR=#006400][FONT=courier new]**display**[/FONT][/COLOR], but not [COLOR=#006400][FONT=courier new]**cropall**[/FONT][/COLOR].  there is no package with that name.  what package do i need to install to get it?  [COLOR=#006400][FONT=courier new]**apt-file**[/FONT][/COLOR] does not find "cropall".

[COLOR=#006400][FONT=courier new]**viewnior**[/FONT][/COLOR] (post #8 ajgreeny) installed (package name same as command) and displays even pnm format though not xcf.  pressing "c" to crop pops up a smaller image to draw the outline in.  i'd rather do that at full size or larger to be able to slice off edges better.

[COLOR=#006400][FONT=courier new]**gthumb**[/FONT][/COLOR] (post #8 ajgreeny) installs a bunch of extra package dependencies including 3 for CD/DVD that i can't use (no such device), spews lots of error messages when i try to view one image (it seems to be trying all of my images and has trouble with a few dozen), and has an unfriendly L&F (too much stuff).

ideally, i'd like to be able to just start drawing an outline for crop as soon as it loads, then press "c" to crop down to my outline.  once i drop the outline, it should stay and let me tweak it.  a nice extra feature would be a zoom in on the outline around where i am tweaking the outline to make it easier in tight pixels (so i can be sure undesired pixels are not inside).

[COLOR=#006400][FONT=courier new]**gimp**[/FONT][/COLOR] loses simplicity as soon as it opens a splash window then 3 running windows.  but [COLOR=#006400][FONT=courier new]**gimp**[/FONT][/COLOR] has its uses like correcting the color on my dog's image which was taken from a video that was too green in highlights.  BTW, she was originally named "Pixel" but everyone just started calling her "Pixie".

---

### Post by TheFu on 2019-10-06
Link to **cropall** provided by Holger_Gehrke, yes?
The GUI for **display** is very light. Use a mouse to control the crop.

---

### Post by Holger_Gehrke on 2019-10-07
cropall isn't in the repositories, it's a small(-ish) python script (~20kb, ~600 lines). One problem with it though: it has a bug in it's GUI, the crop-button is overwritten by the 'Perfect Pixel-Ratio' checkbutton. The fix is simple (and is documented in the issue somebody filed on this). Change the "8" for the position of the checkbutton to a "9" in line 248.

Holger

---

### Post by cruzer001 on 2019-10-07
> **Holger_Gehrke said:**
> Please read **all **TheFu posted. 'display' and '[CropAll]("https://github.com/pknowles/cropall")' are graphical frontends for ImageMagick/convert. 'display' is probably already installed on your machine since it's part of IM. Since it's a frontend to most - if not all - functions of IM and its GUI is IMHO somewhat fiddly, it's probably not quite what you're looking for. 'cropall' on the other hand does **cropping and resizing and nothing else**.

Holger

No more running to gimp for the quick crop, thankyou both.

Wonder if I can incorperate CropAll into Nemo.

---

