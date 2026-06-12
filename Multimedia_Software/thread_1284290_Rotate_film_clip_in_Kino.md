---
title: "Rotate film clip in Kino?"
date: 2009-10-06
forum: Multimedia Software
---

### Post by eimiandra on 2009-10-06
I used a digital camera to film for this little project... the film shot virtically is not imported as such into Kino. So there are a bunch of people just floating on their sides, which doesn't work.

How do you rotate the clip? Can you? 

I would go back into my camera and do it, but some have been deleted and the camera is being buggy on top of that.

---

### Post by cotcot on 2009-10-06
Not possible with Kino.
Possible with Avidemux (and some other editors, but I think Avidemux is the easiest). Load the clip. Select a codec instead of 'copy' in the 'video' button left. Then you have access to the rotate tool in 'filters'. 
Save your rotated clip and you can use in kino.

---

### Post by eimiandra on 2009-10-07
Thanks so much!

> **cotcot said:**
> Not possible with Kino.
Possible with Avidemux (and some other editors, but I think Avidemux is the easiest). Load the clip. Select a codec instead of 'copy' in the 'video' button left. Then you have access to the rotate tool in 'filters'. 
Save your rotated clip and you can use in kino.

It's saving as an unknown format AND stripping the audio from the video in avidemux.  Anymore suggestions.

---

### Post by cotcot on 2009-10-07
> **eimiandra said:**
> 
It's saving as an unknown format AND stripping the audio from the video in avidemux.  Anymore suggestions.


Some more info would be nice to be able to help you. 'unknown' format is unknown for which application ? Renaming the file with .mpg extension if you used an mpeg codec will make the file recognisable.   What is the format you get from your camera ? (720x576 ? DV ?) What is the format you play to ?

I checked myself if it is possible.  Loaded a 1920x1080 clip; turned it 90°; resized it to 616x1080 (landscape to portrait using the Mplayer resize filter in avidemux) and added black borders of 412 to get 1440x1080 (using the Add black borders filter). I saved it with DVD(lavc) option for video and MPEG-TS(A+V) for format. Give the filename the extension .mpg. The resulting clip was accepted by kino including the sound. (It is the opposite of what you want to do, but the system works in both directions)

There are other ways but they are less easy (command line, blender, cinelerra).

---

### Post by eimiandra on 2009-10-07
when i save the clip in avidemux, it saves as an xml document, which, if opened in firefox or text editor reads:

"<?xml version="1.0"?>
<fliters Flighternumber="1">
[INDENT]<Filter Tag="27" Confi="Rotate 270 degrees">
[INDENT]<Parameters Number="3">
[INDENT]<width>480</width>
<heigth>640</height>
<angle>270</angle>[/INDENT]
</Parametes>[/INDENT]
</Filter>[/INDENT]
</filters>"

---

### Post by eimiandra on 2009-10-07
re other questions:
from my camera its in AVI, so i converted all the clips to DV for KINO (i've tried with clips in AVI and DV)

also, when I do exactly as you instructed, I get an assert failed message

---

### Post by cotcot on 2009-10-08
I do not know the meaning of 'assert failed' nor do I know the reason for the xml. 

Here is another possibility.

Kdenlive. I have checked an example and it is easy.
Kdenlive is in the repos. Put a clip on the timeline. Right click on it and select the 'rotate and shear' and shear effect under the drop down of 'add video effect'. You will get a window where you can choose the angle. Also in the 'add video effect' you need to apply a second filter 'zoom and pan'. You will see a red rectangle in a new window. Hoover over the border and you will see a possibility to scale the window to adjust the aspect ratio of you turned video. Finally render.

---

