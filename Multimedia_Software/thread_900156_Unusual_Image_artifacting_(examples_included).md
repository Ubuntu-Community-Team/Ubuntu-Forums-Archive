---
title: "Unusual Image artifacting (examples included)"
date: 2008-08-25
forum: Multimedia Software
---

### Post by celestius on 2008-08-25
Ok, so I upgraded to Hardy. Yay. All was well in the land of linux till I tried to watch some videos. Then I realized something was amiss. Well, I'll cut right to the chase here and show ya'll what's happening.

This was a screen capture (using printscreen) from a high def video playing fullscreen at 1280x720 in VLC. My screen rez is set to 1360x768.
[[IMG]http://img98.imageshack.us/img98/943/disneylogoof1.th.png[/IMG]](http://img98.imageshack.us/my.php?image=disneylogoof1.png)

This is a comparison of a dvd screen capture taken in VLC and then opened in the default ubuntu image viewer.
[[IMG]http://img151.imageshack.us/img151/6171/uhhim3.th.png[/IMG]](http://img151.imageshack.us/my.php?image=uhhim3.png)

This is from fischerspooner's website. The same file was saved off the website and reopened in the image viewer included in ubuntu. Notice the aliasing of the image in the website compared to the one opened in the image viewer.
[[IMG]http://img80.imageshack.us/img80/3113/screenshotml4.th.png[/IMG]](http://img80.imageshack.us/my.php?image=screenshotml4.png)

So here are some notes on my system/what I've discovered:

1) This is definately a resize issue. It seems as though the video is being processed underneath some sort of square grid and the pieces are not being aligned properly when they're displayed on the screen. When I set my screen resolution to 1280x720 the first video looks fine at fullscreen but again has the artifacts in windowed mode.

2) This happens regardless of the player I use. Have tried vlc, gxine, and the default totem movie player.

3) As in the second example if I use vlc's built in screen capture utility the resulting image file produced has no artifacts, however if i screen capture using the printscreen button it captures the artifacts on the video.

4) Video looked fine in Ubuntu 7.10.

I am using a Radeon x1900 and all the videos are either files on my harddrive or dvds. The video driver I'm using is the one that ubuntu suggested installing after I setup the OS for the first time wherever that comes from. I installed the catalyst control center and it lists the driver version @ 8.47.3. Also, the artifacts can be seen the best if you click the thumbnail and then click the image again in the window that pops up to show the image in it's original size.

Any suggestions on where to start looking? Thanks in advance.

---

### Post by Cresho on 2008-08-25
not working.  cant...see pics

---

### Post by Cresho on 2008-08-25
It is an image.  A resize problem.  I dont know where you got this image or what ever but I am assuming you are having issues watching television.  you also need to state your card, drivers, methods of install, what software you viewing this, what video driver as well.

---

### Post by celestius on 2008-08-25
Just to clarify things, these the main focus is video playback artifacts. (sorry bout the misleading title, I've corrected it)

I noticed that this particular resizing pixelation happened on the fischerspooner website as well so I included an example of that in case it had any relevance or lead to any ideas of what the problem might be.

---

### Post by Cresho on 2008-08-25
I tried the fischerspooner website.  Appearantly, the web author does not know how to resize images correctly.

In this fischerspooner, if you copy the image to the desktop and then open it in mozilla, you can clearly see the real size.  In fact, look at the properties and look at the pixle size.  What the webauthor did was place an image on the html and asked it to have it resize it.  It's like telling it to show an image that is 100x100 to be viewable @ 1024x768.  This is completely normal.  The image viewed on our image viewing software uses hardware automatically to blurr pixles to show sharper images.  If you use software render, it looks pixlelated but no in it's original size but expanded.  This is normal.  The webauthor just did a botched job!  the jpegs are way to big in compression, it is not resized correctly clearly!

Now for your vlc, you need to set your native monitor resolution.  New monitors are 5:4 aspect ratio such as the sharp.  you most Likely are using a resolution that is not native to your monitor.  Very Likely.  This is a hardware issue.

You need to state default monitor resolution and your hardware graphics card capabilities along with hz potential.  Not only that, alsy vlc has settings.  you are most likely using a x video render of somesort that is not optimized for your graphics card.  x means unknown.  try opengl if your card supports it.  THe hardware will scale the image more appropriatly.  I am not familiar with vlc since I use a heavily modified xine ui with a total custom config file.  I have vlc and its not good enough for me but ill take a look at the settings and post later.

---

### Post by Cresho on 2008-08-25
go under settings->prefernces look for advanced settings on lower left and now select video and output modules.  you can now select video output module.  This will not necesserily fix or it could but it has lots of features.  under filter, this is where you might also take a look after going through all the settings.  Remember to restart application to take effect...i think.

---

### Post by celestius on 2008-08-26
I have tried selecting a different video output module to no avail. Both XVideo Extension Video Output and X11 Video output have no difference in rendering. I also tried the OpenGL Video Output but that causes VLC to crash. As a side note I discovered that in the preferences of Eye of GNOME there is an option to smooth images when zoomed. If this is turned off I get the same effect when images are resized so it seems like there is some kinda image scaling that is being applied to all images that are displayed in ubuntu. It's almost like a post processing effect that gnome is applying or something. I also tried disabling the ati accelerated graphics driver in System-->Administration-->Hardware Drivers and rebooting to see if the default video driver changed anything but it didn't. Anywho, any other suggestions are still welcome as the problem persists.

---

### Post by Cresho on 2008-08-27
have you tried finding your native monitor resolution and applying it to the graphics card?  if you are using a high definition tv as a computer monitor, this will cause the problem you see as well.  Also, non native monitor resolution.

---

