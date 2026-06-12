---
title: "ATI Card - Choppy Full Screen Video"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Artsaypunk on 2007-12-04
Hi Folks,

It's the same old choppy full screen video problem with an ATI card.  I'm almost embarrassed to post this.

I know this is a common dilemma on these forums, but I have sifted through so many threads that my eyes are going buggy.  So, I decided to make my first post.  I have just recently installed Gutsy on an Inspiron 9300 (approx. 1.73 ghz - 1,256 gb Ram), and am very impressed so far, despite some video card problems.  As this forum is littered with ATI problems, you would think I could find an answer, but nothing yet.

I have an ATI Mobility Radeon x300, which gave me some initial problems which I solved along the lines of [http://ubuntuforums.org/showpost.php?p=3547657&postcount=7]("http://ubuntuforums.org/showpost.php?p=3547657&postcount=7")

That seemed to clear most things up, got compiz working and everything else is fairly smooth.  However, I still get a lot of choppiness in full screen mode of any video player I've tried.  It's watchable, but annoying.

Keep in mind that I'm relatively computer savvy, but new to ubuntu and linux.  Any help would be much appreciated!

So, here is the fglrxinfo:

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6473 (8.37.6)


and the glxinfo

> name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------



Let me know what else you might need

---

### Post by cipher_nemo on 2007-12-04
I don't know your entire history with this issue, so excuse me if I'm a bit off in my suggestions.

The problem you describe sounds more like it's related to video codec issues and/or compatibilities than an ATI issue. If Compiz is working, then obviously 3D and OpenGL is working well. If you can move windows around using the wobbly window component of Compiz, then 2D acceleration is probably fine too.

What media player(s) have you tried? Which codecs and plugins? Is this specific to DVD playback, or just a regular mpeg2 video, etc.?

---

### Post by Artsaypunk on 2007-12-05
I would love it if it's just a codec issue, since that would hopefully make my life easier!

Yes, as far as I know (which isn't much) compiz is working well.  The wobbly windows work as well as the cube etc.

I would like to use VLC as my default video player.  I have played around with the settings a bit, video outputs for example, but I've only managed to make it marginally better.  

I've tried video files and DVDs with the same result.

This is more of a newbie question, but is it okay that the Direct Rendering is off?  Is that covered by the proprietary ATI accelerator driver?

---

### Post by tiachopvutru on 2007-12-05
Well, do you turn Compiz off when you view video?

As for a player suggestion, I would recommend SMPlayer, which is an mplayer frontend. Also, you may or may not want to try the newest driver which can be received from ati website.

---

### Post by Artsaypunk on 2007-12-05
It doesn't seem to matter whether compiz is off or on.  Same choppiness either way.

---

### Post by iblazev on 2007-12-05
Hello!
I have a similar problem although I use newest ATI drivers and Kaffein. Movies are in AVI format and w32codecs from mplayer site are installed. 
Picture was a little less choppy  when I was using VESA driver just after installing Kubuntu but still it was irritating. Unfortunately most of my movies are in AVI. 
Any suggestions?

---

### Post by eye208 on 2007-12-05
Have you enabled XVideo?
```
sudo aticonfig --ovt Xv
```

Without XVideo, most video players will resort to X11 output which is slow, esp. when direct rendering is disabled.

---

### Post by cipher_nemo on 2007-12-05
As eye208 suggested, video acceleration may not be enabled or configured properly. Even if ATI chips have a more tainted history in Linux, they do have more advanced built-in video acceleration.

---

### Post by iblazev on 2007-12-06
> **eye208 said:**
> Have you enabled XVideo?
```
sudo aticonfig --ovt Xv
```

Without XVideo, most video players will resort to X11 output which is slow, esp. when direct rendering is disabled.

Haven't tried that yet. Going to try it today and see what happens:)

---

### Post by Artsaypunk on 2007-12-06
Ok, well, here's something interesting.  Dealing with an unrelated issue, I completely crashed the whole system, so since my data is all on my external HD, I decided to do a fresh install.  This time around, I decided to load the official ATI drivers, as several people have suggested.  I painstakingly made my way through the entire manual installation process via the official wiki, and successfully installed the drivers.  I have to say I was quite proud of myself.

Anyway, with the "real" drivers, compiz worked, but much worse than it did with the repository drivers.  Wobbly windows, for example, were definitely wobbly, but they were choppy as well.  Playing a video file (the reason for this post in the first place) barely worked at all.  Even in a small window, the video was black and the only way to see the video was to resize it manually and for a split second you could see a few frames of what was playing.  I messed around with some driver settings, but still couldn't increase the performance.  Then I crashed the whole system again, and said, screw it, fresh install again.  (I think this is my 8th install... good thing I'm stubborn).  

So, as it stands, the repository drivers make everything work, except some choppiness on full screen video.  The ATI downloaded drivers make nothing work and everything choppy.

So, it looks like I'll go back to the repository route.  It's certainly easier to install.

Any other suggestions?

---

### Post by eye208 on 2007-12-06
> **Artsaypunk said:**
> So, as it stands, the repository drivers make everything work, except some choppiness on full screen video.  The ATI downloaded drivers make nothing work and everything choppy.
Did you test the downloaded drivers with XGL or with X.org? As far as I know, AIGLX support has been added to fglrx, so it should work fine with Compiz on X.org now.

---

### Post by kelvin spratt on 2007-12-06
try installing [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
this is ENVY will download and install the correct drivers for Nvidia and ATI.

---

### Post by cmpn76 on 2007-12-06
I had the same problem and my solution was simple going back to opensource driver.

---

### Post by teabeartom on 2007-12-06
> **cmpn76 said:**
> I had the same problem and my solution was simple going back to opensource driver.

Do you have the x300 mobility?  With the X300 mobility, the open source driver runs compiz kind of slowly and it's not pretty.  With lower cards, the open source driver works great I hear.  

Since I have the x300 and haven't found a solution, I either have to use xgl and not play videos fullscreen, or use the opensource driver and have choppy effects with good video.  I guess the other option I have is to ditch compiz completely.

---

### Post by coskierken on 2007-12-07
Had the same video playback problem with my mobility x1700.  The Ubuntu rescticted drivers loaded work fine.  I worked with it and racked my brain. I finally got it.  It is mostly the codecs and the player combined.  Here is a:lolflag: solution.  Go to the cafe and get uBackup!  It is more than a backup as my buddy wrote it and put in utilities.  One is to install totem-xine with codecs for mp4 and dvd playback.  you can do it yourself through synatic.  Try it first and see what happens.  Xine will uninstall gstreamer codec.  I got it to work great with smooth video playback even at full screen.  It is just my 2 cents worth and I hope it works for you!

---

### Post by teabeartom on 2007-12-08
Hmm... I've already been using the totem-xine backend, but like any other video player on my system, it displays video choppily.  The video I found isn't so bad now that I've upgraded to gutsy, but in high-action scenes, or when an object is moving across the screen fast, the choppiness is noticeable.  

Thanks for your help!  Any other suggestions?

---

### Post by Yellow Pasque on 2007-12-08
Are you running xgl? Perhaps try removing it so you can use direct rendering..
```
sudo apt-get remove xserver-xgl
```

Also, make sure this is tacked on to your /etc/X11/xorg.conf
```
Section  "DRI"
Mode 0666
EndSection
```

---

### Post by iblazev on 2007-12-15
> **Artsaypunk said:**
> 
...
Anyway, with the "real" drivers, compiz worked, but much worse than it did with the repository drivers.  Wobbly windows, for example, were definitely wobbly, but they were choppy as well.  Playing a video file (the reason for this post in the first place) barely worked at all. 
...

Any other suggestions?

Just to say tha I managed to work things right on my comp with X1300 card. I used newest ATI drivers installing .run file. Didn't try compiling from source. And I didn't install Compiz.
To play video I use mplayer and w32codec from mplayer creator pages and that's about all. Now video is great (I watched 3 seasons of LOST again just to make sure:) ) and a few other movies while Kaffein is somewhat choppy reproducing the same files.
So, try this solution. Mplayer seems to work nicely.
Good luck!

---

