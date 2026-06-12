---
title: "Extracting pictures from .MOV"
date: 2011-06-03
forum: Multimedia Software
---

### Post by diablofatt on 2011-06-03
Hello. It appears I thought I was taking photo's with my Nikon CoolpixS5 but they are saved as .mov files. When I watch file, I see the picture, and then it's over in a second. How can I extract the image from the .MOV file?

If it's of any relevance I used digikam to recognise my camera. 

Thank you for time and thought's.

---

### Post by Derxst on 2011-06-04
While playing the .mov file, pause the video, and press the "Print Scrn" key on your keyboard. A screenshot will be saved to your desktop. From there, you can use an image editor like GIMP to crop what you want to keep.

---

### Post by diablofatt on 2011-06-04
Thanks for the response. I thought of that and tried. I Used VLC and media parole (I think) and the video file goes so fast. The pause commands don't work. The clip is instantaneous and can't move through the video. Any more feedback would be appreciated.

Moderator - is there a better place for this post?

---

### Post by BobSongs on 2011-06-04
Here's a way to stop Auto-Play for VLC:

Start VLC.

View > Playlist

With the "Playlist" tab on the left selected, right-click in the white space under "Title" "Duration" "Album" and select **Add File** or **Add Directory**.

Once your .mov files are added you'll have the list queued.

Hit the space bar to start the film and space bar to pause.

---

### Post by diablofatt on 2011-06-05
> **BobSongs said:**
> Here's a way to stop Auto-Play for VLC:

Start VLC.

View > Playlist

With the "Playlist" tab on the left selected, right-click in the white space under "Title" "Duration" "Album" and select **Add File** or **Add Directory**.

Once your .mov files are added you'll have the list queued.

Hit the space bar to start the film and space bar to pause.

I did exactly that. Still no avail. I can't see the images that way was all. Again instantaneous. Thank you. Any other ideas?

---

### Post by mgmiller on 2011-06-05
Try opening the mov in a video editor.  I especially like openshot, but it may be overkill for this application.  Pitivi is supposed to work with mov and is installed by default.  Avidemux may also work.  You should be able to easily pause it in the preview window and then do a screen capture.  You may even be able to export a still from the video.  Good Luck.

---

### Post by sectshun8 on 2011-06-06
> **Derxst said:**
> While playing the .mov file, pause the video, and press the "Print Scrn" key on your keyboard. A screenshot will be saved to your desktop. From there, you can use an image editor like GIMP to crop what you want to keep.

That would have been my suggestion as well :)

---

### Post by s.fox on 2011-06-06
> **diablofatt said:**
> Moderator - is there a better place for this post?

Thread moved to  [Multimedia & Video]("http://ubuntuforums.org/forumdisplay.php?f=334")

---

### Post by shantiq on 2011-06-06
ok i was thinking  ffmpeg can convert mov to animated gif but if your gif contains only one image it should leave you with that


so maybe try    ( This is for bulk )


```
for f in *.mov; do ffmpeg -i "$f"  "${f%.mov}.gif"; done
```


**work from a copy of your original files as you never know what it might throw up or delete**

---

### Post by mgmiller on 2011-06-06
The problem the O.P had was that his videos are so short (about a second long) that he does not have time to pause them.  That's why I suggested opening them in a video editor which gives you frame by frame control of the video.  Once he has the frame he likes displayed in the preview screen, he can do a screen capture as mentioned earlier.  Some of the video editors may also allow you export the single frame as a jpeg.

---

### Post by FakeOutdoorsman on 2011-06-07
You can extract all of the frames from the video with FFmpeg. If the videos are about 1 second in duration then that's only 15-30 images each:
```
mkdir frames
ffmpeg -i input frames/screenshot%d.png
```
Now you can browse the images in the *frames* directory and choose whatever image(s) you want.

---

### Post by andrew.46 on 2011-06-07
MPlayer will also extract images using *-vo png*, *-vo jpeg* and a few others. Usage of the png video output is given in tip no. 5 of this old guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

---

### Post by diablofatt on 2011-06-13
> **mgmiller said:**
> Try opening the mov in a video editor.  I especially like openshot, but it may be overkill for this application.  Pitivi is supposed to work with mov and is installed by default.  Avidemux may also work.  You should be able to easily pause it in the preview window and then do a screen capture.  You may even be able to export a still from the video.  Good Luck.

I will try this and post back. I thought there would be a simple way! Thank you!

I missed the second page posts! Thanks for the link! I'll report back so the next poor soul knows.

---

