---
title: "[SOLVED] Free program to compile indiviual images as video?"
date: 2007-07-15
forum: Multimedia Production
---

### Post by sci-fi guy on 2007-07-15
Like the title says, I am looking for a (preferably open-source) program that can take a series of still frames and put them together as a video. I am not talking about a slide show, where an image is visible for a few seconds, but rather each image is one frame. I ask because I occasionally make small animations in [Blender 3D]("http://www.blender3d.org") and I:

1. Have trouble with the export codecs creating lousy videos, but individual images are fine. If I can just export as a bunch of images and put those together later, I should be able to prevent lousy clips

2. One semi-recent animation had 50 purely black frames at the beginning, and because I was rendering as a video, each of those frames got rendered individually, rather than just creating a blank frame and duplicating it alot. This may not seem like a big deal, but because I was getting lousy videos, I re-rendered the whole clip several times in different codecs, and the time adds up.

3. Also, in that same animation, I fiddled around a few times with different lighting while rendering. But those 50 frames were never changed. So I could have just made 50 black .PNG's and used those over and over again with the different animations, saving more rendering time.

Any ideas?

---

### Post by maiatoday on 2007-07-16
I was looking for the same thing yesterday and found it in Blender. :)

If you go into the Video Sequence editor and add a file and then go to the directory where the files are, you choose all of them with Ctrl A. Once you accept it will give you a strip in the Video Sequence editor. When you go to the Render Tab you can chooseyour AVI setup, click the Do Sequence button, press the Anim button and it will make an AVI.

Alternatively have the GIMP installed with the GAP add on. Open the first image and then there will be a Video option on the toolbar. From there you can export to Video.

Hope this helps.

Now to get the sound added, mmm I haven't cracked that one yet.

ALso Avidemux does an ok job of doing conversions for me.

---

### Post by sci-fi guy on 2007-07-16
Thank you. I knew that Blender could insert images into a video with Video Sequence, but I though I would have to add each individual image manually.

BTW, have you had any trouble with your video codecs screwing up output?

I haven't figured out inserting sound either. I used to use the Elements version of Adobe's video editor (whatever it is called) to add in the final cut, but I no longer have access to that. I think that [Cinelerra]("http://heroinewarrior.com/cinelerra.php3") can do it, though I haven't tried and it is supposed to be very demanding with your hardware.

---

### Post by maiatoday on 2007-07-22
I am also  still relatively new at this and had the same problem, I tried to do an all ubuntu animation but had to put the final sound to the final video on my win2k box due to deadline pressure. Blender cannot add the sound in the avi contianer as far as I have read in their wiki. I tried pitivi, I could add it but not save the file. bleargh.

I have read that avidemux  could do it but haven´t managed it yet.

I have Cinelerra installed but have yet to work through a tutorial or something to figure out how to do it.

oi I guess that doesn´t help much but I´ll keep you posted

---

### Post by luisbg on 2007-07-29
have you tried stopmotion?

luisbg

---

### Post by sci-fi guy on 2007-09-03
Nice. Thank you!

---

### Post by eye208 on 2007-09-04
**mencoder -o clip.avi -fps 29.97 -noskip -audiofile soundtrack.mp3 [encoding options ...] "mf://*.png"**

will mux all the PNG files from the current folder and the audio file "soundtrack" (which can be WAV, MP3 or Ogg Vorbis) into a video file "clip.avi" of 29.97 frames per second (NTSC framerate).

---

