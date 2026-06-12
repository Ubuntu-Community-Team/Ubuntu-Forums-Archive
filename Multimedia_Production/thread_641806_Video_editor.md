---
title: "Video editor"
date: 2007-12-15
forum: Multimedia Production
---

### Post by piratesmack on 2007-12-15
Well I hear the best video editor for Linux is cinelerra, but I'm having problems with it. So I'm wondering if anyone has successfully run Adobe Premiere in crossover.

Or if you can recommend a good video editor that would be nice.

Thanks in advance

---

### Post by omega_user on 2007-12-16
i hadn't heard of cinelerra, I'll check that out

---

### Post by NullHead on 2007-12-16
kino ```
sudo apt-get install kino
```

---

### Post by rsambuca on 2007-12-16
> **piratesmack said:**
> Well I hear the best video editor for Linux is cinelerra, but I'm having problems with it. So I'm wondering if anyone has successfully run Adobe Premiere in crossover.

Or if you can recommend a good video editor that would be nice.

Thanks in advance

Problems with the program working properly, or problems with using the program?

---

### Post by piratesmack on 2007-12-16
I don't know what formats are supported, but the problem I had was editing avi and ogg

---

### Post by Prospero2006 on 2007-12-18
Cinelerra is a pure pain to learn, but once you master it, you'll have a hard time finding an open-source video editing program that will compete with it.

---

### Post by dad311 on 2007-12-18
> **Prospero2006 said:**
> Cinelerra is a pure pain to learn, but once you master it, you'll have a hard time finding an open-source video editing program that will compete with it.

I agree and there are a lot of how-tos on the WEB to get you started.

---

### Post by eye208 on 2007-12-19
> **piratesmack said:**
> Well I hear the best video editor for Linux is cinelerra
I'd say Blender is the best one.

---

### Post by Prospero2006 on 2007-12-19
Blender is more about 3D modelling.
I wouldn't say it's a video editor. 
Am I missing something?

---

### Post by steevc on 2007-12-19
I've played with Kino a bit, but you have to accept that it is fairly limited in what it can do. I needed some extra features like adding music and titles. I tried Kdenlive and I'm impressed. It seems to offer all that I need, but does suffer from the occasional crash. I used the built-in effects to lighten some DV footage of dancing at a wedding so that you can actually see the people now. This has saved my bacon as I've been nagged to do something with this recording for a while.

I'm still working out how to use some of the features as the documentation seems to be patchy for now. I will be trying to produce a DVD at the end. This is something I have no experience of.

---

### Post by brennydoogles on 2007-12-19
+1 for KdenLive

---

### Post by eye208 on 2007-12-20
> **Prospero2006 said:**
> Blender is more about 3D modelling.
I wouldn't say it's a video editor. 
Am I missing something?
The fact that Blender is also a 3D modelling application and image compositor is what makes it so powerful at video editing. If the built-in effects are not enough you can create your own. You can use the rendering engine and chroma key effects to create all kinds of animated 2D and 3D overlays, e.g. logos, fancy subtitles or karaoke. You can put video on a mesh as a texture, deform it in various ways while playing, and pipe the result back into the video sequence editor. You can timestretch video (with optional frame blending) to synchronize it with audio, speed it up, slow it down or even play it backwards, controlled by an interpolation curve. You can add Z-buffer info (i.e. depth) to a video clip and use it for defocus effects etc. None of the other editors on Linux offers this degree of flexibility and stability.

Blender can handle hours of video footage and audio clips within a single project. Thanks to FFMPEG integration it can import all the formats supported by FFMPEG, including Ogg Theora. It can read and write both 32bit and float images, DV, MJPEG, MPEG-1, MPEG-2, MPEG-4 ASP and H.264.

That's why I consider Blender the best (free) video editor on Linux for both large and small projects.

---

### Post by steevc on 2007-12-20
> **Prospero2006 said:**
> Blender is more about 3D modelling.
I wouldn't say it's a video editor. 
Am I missing something?

I was just listening to the latest LugRadio and they mentioned that Blender has some non-linear video editing features, i.e. you can load in a DV file and edit. I'm guessing this is useful to those building a movie with it so that they can edit the results.

EDIT:Only just noticed the post from eye208

---

### Post by Prospero2006 on 2007-12-20
Sounds like I am missing something.
I've been teaching myself the basics of the blender because I want
to do some basic level animation lessons with my kids, but that functionality
sounds straight up sweet.
Is there a tutorial online that talks about overlaying a video and creating a mesh somewhere. Do you have any specific tips?

Thanks, I'm a blender newb.

---

### Post by KCPokes on 2007-12-20
> **steevc said:**
> I've played with Kino a bit, but you have to accept that it is fairly limited in what it can do. I needed some extra features like adding music and titles. I tried Kdenlive and I'm impressed. It seems to offer all that I need, but does suffer from the occasional crash. I used the built-in effects to lighten some DV footage of dancing at a wedding so that you can actually see the people now. This has saved my bacon as I've been nagged to do something with this recording for a while.

I'm still working out how to use some of the features as the documentation seems to be patchy for now. I will be trying to produce a DVD at the end. This is something I have no experience of.

Personally, I use Kdenlive to edit my videos and ManDVD to create the output DVD (burn).  Like most things, there are a 101 different ways to go about this, but I've found that not one application does everything I want, the way I like it anyway, thus I choose to use multiple applications to accomplish it.

---

### Post by eye208 on 2007-12-21
> **Prospero2006 said:**
> Is there a tutorial online that talks about overlaying a video and creating a mesh somewhere.
[http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor](http://wiki.blender.org/index.php/Tutorials/Video_Sequence_Editor)
[http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)
[http://wiki.blender.org/index.php/Manual/Compositing](http://wiki.blender.org/index.php/Manual/Compositing)
[http://wiki.blender.org/index.php/Tutorials#Compositing](http://wiki.blender.org/index.php/Tutorials#Compositing)
[http://wiki.blender.org/index.php/Manual/Animated_Image_Textures](http://wiki.blender.org/index.php/Manual/Animated_Image_Textures)

---

### Post by ugm6hr on 2007-12-21
> **steevc said:**
> I tried Kdenlive and I'm impressed. It seems to offer all that I need, but does suffer from the occasional crash. I used the built-in effects to lighten some DV footage of dancing at a wedding so that you can actually see the people now. This has saved my bacon as I've been nagged to do something with this recording for a while.

I have just started messing around with video editing - and managed to edit a home video within a few hours of installing kdenlive.

It is pretty strightforward to cut film, separate audio and control video and audio transitions, and arrange the clips on a simple time-line with just a few clicks.

The documentation may not be complete, but you can work it out with almost no instructions apart from the 2 video tutorials on the website.

I've given up on trying to install Cinelerra (which just refuses to start on my laptop), which I gather is more powerful but also more complex to use.

---

### Post by kkkkatie on 2007-12-31
just installed kdenlive.  It seems really good,epesially as i just want to put together clips into a soundtracked sequance and cut out my dodgy filming.

---

### Post by steevc on 2008-01-01
I managed to produce a basic DVD of a wedding using kdenlive. I managed to include titles, some music and some basic effects. Due to lack of time I didn't play too much with the DVD options. I would have liked to include some chapters, but could not see how.

The DVD was exported straight from kdenlive and burned with k3b. I couldn't seem to play it on any of my Linux players, but it worked in my Sony apart from not being able to fast-forward. Is this a known big?

I have a load more DV tapes to edit when I have time. I just want to get them down to a reasonable length so that we will actually watch them. Ideally I would put a few on each DVD with a simple menu. I would probably want to do each as a separate project. Is kdenlive capable of this?

---

### Post by ugm6hr on 2008-01-01
> **steevc said:**
> I just want to get them down to a reasonable length so that we will actually watch them. Ideally I would put a few on each DVD with a simple menu. I would probably want to do each as a separate project. Is kdenlive capable of this?

Not sure - but DeVeDE can definitely add a simple menu screen with multiple "Titles" and equal chapter spacing (e.g. every 5 mins).  So you could export all the kdenlive files as .avi (not sure if DeVeDe can use DV files), and then tell DeVeDe to move from one title to the next at the end of playing (so the whole DVD plays continuously, but you can go to the Menu screen and select specific Titles by name).

---

### Post by cotcot on 2008-01-01
I capture with kino and edit most of the time with cinelerra. 

You can find the way how I compiled cinelerra WITH OpenGL on a 64bit gutsy [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=586370")

I also tried kdenlive. Kdenlive is fine. However after spending time to learn cinelerra it is clearly my preference. I have not explored Blender yet.

---

