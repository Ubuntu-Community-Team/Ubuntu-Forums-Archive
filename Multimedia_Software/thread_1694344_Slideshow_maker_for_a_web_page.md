---
title: "Slideshow maker for a web page?"
date: 2011-02-24
forum: Multimedia Software
---

### Post by PDA1 on 2011-02-24
Can you recommend a good slideshow maker that'll make great slide shows to be used on a web page?

I need a slideshow maker that resides on my computer and not a web based one.

---

### Post by perspectoff on 2011-02-24
Most of the CMS programs (Drupal, Joomla, WordPress) have modules to do this. I have one on my Drupal website, for example.

You can have a WebDAV repository and store all your images there, and can just load them (in slideshow mode) from the WebDAV repository from the website. That's one easy way.

---

### Post by PDA1 on 2011-02-24
Those programs are web based makers and not what I want.

DigiKam has some that create an html gallery and are basic....and it has others simply don't work.

---

### Post by lykeion on 2011-02-24
I haven't tried it myself, but **videoporama** may be what you're looking for:
> Description: Make and export image slideshows
 Videoporama is a software designed to make image slideshow and export to video file.

 The following options are available:
  * With or without transitions between images.
  * Image geometries: 4:3 or 16:9.
  * Display time is set image by image.
  * Transition type is defined image by image.
  * Add a sound to slideshow (wav, ogg ou mp3).
  * Output in PAL (720x576), NTSC (720x480), SECAM (720x576), Web (384x288),
    HD 720 (1280x720) or HD 1080 (1920x1080).
  * Output file format : Raw dv (.dv), AVI (codec dv),
    MPEG (VCD, SVCD et DVD), FLV (Flash video format) and
    H264 (MPEG4 part 10 AVC).
  * Add a background image (For images which are in portrait) or add a
    background color. (Notice : The image should have the same geometry than
    the other images.

Videoporama is installed easily via Ubuntu Software center.

---

### Post by PDA1 on 2011-02-24
Neat idea but it doesn't work on my machine.  I really wish when people wrote programs for Linux that'd make sure they worked or could explain, in simple terms, what you have to do to get it to work....or install it.

---

### Post by FakeOutdoorsman on 2011-02-24
> **PDA1 said:**
> Can you recommend a good slideshow maker that'll make great slide shows to be used on a web page?

I need a slideshow maker that resides on my computer and not a web based one.

I'm not totally clear on what you're asking. You don't want to use anything like Flickr or Animoto?

You could try to use FFmpeg to make a movie where each frame is displayed for *x* seconds. If I have 25 images (named from *image001.png* to *image025.png*) and want to display them for 1 second each, and have the output be 25 fps:
```
ffmpeg -r 1 -i image%03d.png -r 25 [output options] output
```
**Note:** I didn't test this example.

---

### Post by cotcot on 2011-02-24
[[COLOR="Red"]http://www.getdeb.net/app/Smile[/COLOR]]("http://www.getdeb.net/app/Smile") is a specific slide show maker. 
You can make slideshows with most video editors. I have made slideshows with kdenlive, blender and cinelerra. Kdenlive is the easiest of the 3. 
What I do not know is what video format you need for web sites. Most editors can render to a lot of formats.

---

### Post by PDA1 on 2011-02-24
[QUOTE=FakeOutdoorsman;10491071]I'm not totally clear on what you're asking. You don't want to use anything like Flickr or Animoto?

No....Flickr's TOS allow them to take you pictures and use them for whatever purposes they want.


Also, I don't want a video output- just pictures in a gallery you can click on to get a bigger view of the picture.

---

### Post by PDA1 on 2011-02-24
Found a great one- JALBUM

---

