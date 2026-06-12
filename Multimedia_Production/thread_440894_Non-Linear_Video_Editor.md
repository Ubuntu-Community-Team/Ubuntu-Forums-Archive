---
title: "Non-Linear Video Editor"
date: 2007-05-12
forum: Multimedia Production
---

### Post by mike richards on 2007-05-12
hey, i was wondering.. since there is an amazing well supported and stable 3D production suite (Blender) for linux/cross-platform. and this program is definately comparable to commercial 3D packages (3DS Max, Maya, XSI, C4D).

is there also a good video editing tool? that perform basic operations (cuting/rearanging clips, fade transitions, text/titles, color correction, etc..) but with a good amount of flexibility and options. something like 'final cut' or 'premiere'? without all the extra ugly looking video filter effects that ill never use.. i've tried pitivi and kino, pitivi to me seems like its easier to work with.. but it cant do anything!! you cant even edit a video slightly.. you can only import video and then render it out, thats it.. as for kino. i cant make much sense of it either, and the UI is even worse than pitivi.. i also tried cineleraa, it seems like it can actually do something, but still not in comparison to commercial non-linear video editors.. is there a 'blender' of video editing for linux? or at least a project in the books for the future that can replace tools like 'final cut'?

thanks.

---

### Post by imon9 on 2007-05-12
Hi,

i would recommend LiVes which is easiest to be installed using the .deb automatic installer file from [http://www.getdeb.net/](http://www.getdeb.net/)

However, here is a few facts before u jump into the bandwagon:
(1) Lives does not have good interface... to me, it look ugly
(2) Clip editing and timeline editing is separated into 2 modes, so u have to work seperately on each clip before arranging in timeline... may be hard for ppl sometime if they cant visualize stuff in their head before hand

Good side:
(1) if you plan NOT ONLY work with just DV files, than LiVes will be your best bet! It uses mplayer/mencoder to handle all the media files so whatever supported by mplayer will be supported by it (of course, if our country dont have the strict law about installing propertiery software in ubuntu, you would have great support by installing 32bit windows codec from mediubuntu

(2) it has a lot of filter which i think is useful, but it takes time to discover and learn it... so i hope u give it a bit of patience

(3) By far is a stable and full-featured editor compared to any other video editing programs...

(seriously, i have tried all the popular one including pitivi, kino, cinerella, kdenlive, lives...etc)

NOTE:
kdenlive has better interface and good feature, but i never get it to run properly on my machine due to a lot of dependency and tweaking problem...

as for Jahshaka, i never got it running, such a mess and hassle not worth trying to install

---

### Post by P_Badger on 2007-05-12
Truth, video editing has been my biggest bane with Linux. The only semi-professional, and properly working, video editor for "the common folks", Mainactor, has just recently been discontinued. [http://www.mainconcept.com/site/index.php?id=15](http://www.mainconcept.com/site/index.php?id=15)

So yeah, the only thing Linux users can do now is cross their fingers and hope something decent gets released eventually by one of the multitude of developers hacking away at nle's. That, or fork out big bucks for an extremely expensive piece of software like Shake or what-have-you.

---

### Post by kelvin spratt on 2007-05-12
Cinelerra is far better than mainactor ever was for mp4 and is up with sony vegas in the windows world its the only
true alterative with linux, i use sanyo vid cam, using and cinelerra and de ve de work excellent with both, 
most others wont even load and kaffine plays them raw mind had more probs in xp

---

### Post by heimo on 2007-05-12
If I remember correctly, [UbuntuStudio]("http://www.ubuntustudio.org/") (temporarily down) chose [Pitivi]("http://www.pitivi.org/") as their main nonlinear video editor.

---

### Post by P_Badger on 2007-05-12
@Kelvin Spratt

If you can give me any hints on how to get Cinelerra to even work, I'd be happy. As it stands, besides looking awful, it has a tendency to start playing and not stopping when I want it too. Mainactor, unlike most Linux nle's, used to actually work as it should.

@Heimo

Ubuntu Studio does indeed use Pitivi, but I stand by my opinion that it's an ***-useless nle. No saving, no effects, crashes like crazy, and the last release was January 31st, so its release schedule isn't very good.

---

### Post by jiminycricket on 2007-05-12
Diva was supposed to be very good, but it hasn't been updated recently I think

---

### Post by kelvin spratt on 2007-05-12
P_BADGER i just spent 1 hr trying  to explain to you how i use cinelerra to find the forum had cut me of so i will start again
as it takes me a long time to write

---

### Post by P_Badger on 2007-05-12
> **kelvin spratt said:**
> P_BADGER i just spent 1 hr trying  to explain to you how i use cinelerra to find the forum had cut me of so i will start again
as it takes me a long time to write

Don't worry about it, man. I just spent on hour trying to install a "Fiesty version" of Cinelerra, and it won't even start up, now. Some sort of silly "faacDecOpen" error I've never seen before. I've had nothing but problems with cinelerra right from day one.

---

### Post by kelvin spratt on 2007-05-12
This is the link i used about Cinelerra [http://flavor8.com/index.php/category/scitech/software/linux/page/3/](http://flavor8.com/index.php/category/scitech/software/linux/page/3/) 
this shows how to use 2 clips to make a movie
This is the 2 links i used to put Cinelerra into synptatic deb [http://www.kiberpipa.org/~gandalf/ub...per/mjpegtools](http://www.kiberpipa.org/~gandalf/ub...per/mjpegtools) ./  and deb [http://www.kiberpipa.org/~gandalf/ub...inelerra/i686/](http://www.kiberpipa.org/~gandalf/ub...inelerra/i686/) ./
I've found for me DeVeDe will join files that don't need editing with hardly any noticable effect so i only use Cinelerra if the file needs editing. Sorry for the delay but the forum keeps cutting me of i think its because i've got multible pages open i F.F.

---

### Post by kxs on 2007-05-12
Does anyone know about pitivi relase with New, Save, etc enabled? Without those it`s quite useless. :(

---

### Post by P_Badger on 2007-05-13
> **kxs said:**
> Does anyone know about pitivi relase with New, Save, etc enabled? Without those it`s quite useless. :(

It doesn't look like they've had a release since January 31st, so no, the current release is still the one with the options greyed out.

---

### Post by alegallo on 2007-05-15
If it can be of interest to you, I am just giving a chance to kdenlive.

It's still in its 0.4 release, but they say rel. 0.5 should be out very soon.

Basically, it tends to be quite similar to the similar Windows apps, and I find it quite intuitive (nothing professional, of course, and not as "naked" as Kino)

I had a small difficulty in letting the firewire capture work without root privileges, but it's nothing that can't be solved spendig some time on it.

The interface looks nice, although it crashes a little too often to my taste #-o 

You have to install quite a lot of dependencies to make it work properly, but it does its honest job, provided you (well, I) export your work in .dv or .avi. 
I'm saying so because whenever I try to make a .mpg or .vob file it simply skips the audio track, except for the last second or so.

There are some nice installation tutorials in the French Ubuntu Wiki.

On the whole, it's worth a try IMHO ;)

---

### Post by ahlich on 2007-05-16
Video, video, video. 
Serious video work is why there's still a NTFS partition taking about 2/3 of my hard drives. It took me two years to be able to break away from Photoshop and manage to achieve similar performances with GIMP (though honestly I achieved it mainly by not having to work professionally in image editing anymore...) but with video it feels we are light years away and unless somebody starts to do something about it we are really talking about a far far distant future.
Projects like UbuntuStudio are the way to go and having something like that dedicated to video would be awesome. I mean something aimed aiming at broadcast video demands and not just to put together a couple of video editing capable applications, plugins and encoding tools. Something that might compete with FCP, Adobe Premiere and After Effects, Canopus, AVID or Newtek stuff. I would even go for linux versions of those any day.
I tried almost everything that is mentioned in this thread. Cinelerra if correctly compiled and setup is an interesting exercise in what might become possible to achieve in a Linux box, if and when a project is to be maintained and upgraded periodically. Any serious attempt to bring video users into Linux would have to be cutting edge and dead stable at the same time - meaning a big investment in all possible senses.

---

### Post by eye208 on 2007-05-18
> **mike richards said:**
> is there a 'blender' of video editing for linux?
Yes, and its name is ... Blender! :)

[http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing](http://wiki.blender.org/index.php/Manual/Video_Sequence_Editing)
> In addition to modelling and animation, Blender has a fully functional Video Sequence Editor as well as an advanced node-based editor that also manipulates a video stream. Compositing Nodes operate equally well on images or video streams, and can apply detailed image manipulation on the stream.

[...]

The VSE within Blender is a complete video editing system that allows you to combine multiple video channels and add effects to them. Its functionality has been inside Blender since the beginning. Even though it has a limited number of operations, you can use these to create powerful video edits (especially when you combine it with the animation power of Blender!) Furthermore, it is extensible via a plugin system to perform an unlimited number of image manipulations.

Using the VSE, you load multiple video clips and lay them end-to-end (or in some cases, overlay them), inserting fades and transitions to link the end of one clip to the beginning of another. Finally, add an audio track so you can synchronize the timing of the video sequence to match it. The result of using the VSE is your finished movie.
If you are familar with Blender's user interface, there's no need to look any further. You can even do fancy stuff by using video clips as animated textures in 3D scenes. Blender supports a large number of video formats through ffmpeg.

---

### Post by imon9 on 2007-05-18
wow...i din't know blender can edit video.. gonna try it out soon... (though i suppose a little digging will be needed to find its functions :p)

great info

---

### Post by drosky on 2007-05-18
> **eye208 said:**
> Yes, and its name is ... Blender! :)



Actually, Blender + Cinelerra is a great combination.  Personally, I think Cinelerra is arguably better as an NLE at this point, but Blender is a great complement.  My son and I (he's the Blender expert) have done several dozen projects in Cinelerra, from 5 minute shorts to 2-hour videos, and in most cases, we use Blender as an enhancement.  In particular, for titling, credits, and transitions, Cinelerra doesn't offer more than basic functionality, and Blender can be used to really add a lot in those areas, especially with Blenders ability to map video onto 3D objects.

---

### Post by mike richards on 2007-05-20
wow, thats awesome, i never knew blender has a built in NLE. im moving from windows to linux, and i used to use 3DS Max 8. and it didnt offer anything like that. man.. blender is such a great package. and to top it all off, its Free OSS!
hopefully i can learn it a bit more over the next few days.

thanks for the info guys.

---

### Post by ideasman42 on 2007-11-22
Hey Guys, for the peach project Blenders NLE has got some attention, snapping, time editing tools, info stamp, markers... better handling of still images,
 see this interview.
[http://peach.blender.org/index.php/making-the-animatic-with-sacha/](http://peach.blender.org/index.php/making-the-animatic-with-sacha/)
We also use ubuntu, and edited some of the interviews with blender (kdenlive too)

---

### Post by Porpoise on 2008-02-01
My main question would be; how many layers of overlay can these editors handle. I have 7 layer projects (produced in Ulead Video Studio (Windows) which can produce multiple picture-in-picture effects (like sports programme title sequences type of thing) - so I'm really looking for a Linux version of that.
 
So far, I've not found anything comparable and that's the main stumbling-block to people being able to ditch windows - there are just still things that you can't get the equivalent software tools for under linux.
 
I'm running Gutsy x64on my hybrid (self-build) PC dual-boot with Vist Ultimate x64 and the multimedia capabilities just have no comparison - I still haven't managed to find linux equivalents to everything I use.

---

### Post by eye208 on 2008-02-01
> **Porpoise said:**
> My main question would be; how many layers of overlay can these editors handle. I have 7 layer projects (produced in Ulead Video Studio (Windows) which can produce multiple picture-in-picture effects (like sports programme title sequences type of thing) - so I'm really looking for a Linux version of that.
There is no limit to the number of overlays that Blender can handle. Simple picture-in-picture effects can be achieved using the [transform](http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Transform_Built-in_Effect) and [alpha over/under](http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Alpha_Over.2C_Under.2C_and_Over_Drop_Built-in_Effects) effects. The transform effect will scale, move and rotate the image, adding alpha transparency to the unused areas of the frame so you can overlay it. You can apply any number of effects in any order. For sports programmes you may find the [speed control](http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Speed_Control_Built-in_Effect) effect useful.

An alternate way of creating overlay effects is by using [compositing nodes](http://wiki.blender.org/index.php/Manual/Compositing_Nodes). The [translate](http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Translate_Node), [scale](http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Scale_Node) and [rotate](http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Rotate_Node) node types will transform the picture. [Matte nodes](http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Mattes) can be used to create chroma-key (also known as "green screen") and similar overlay effects. Think of the silhouette effect in an iPod ad.

If that's not fancy enough yet, you can use Blenders rendering engine to project video footage onto planes and other objects and modify them in 3D space. Imagine a video sequence of a room with a TV screen showing another video sequence. In fact there is hardly anything in Adobe After Effects that you can't do with Blender as well.

Entry-level applications such as Ulead Video Studio or Apple iMovie are "one-trick ponies", i.e. they provide a fixed set of prefab effects with very limited customizability. They target an audience that is looking for instant gratification without a learning curve.

Most of the tools in the open source world do not work like that. For example, there are no wizards in Blender. On the other hand there are no limits either. If you want to create a scene like [this](http://www.youtube.com/watch?v=iN1wAZS-sWI) or [this](http://www.youtube.com/watch?v=5XCCv4_S1rQ), Blender has all the tools you need, and you can combine them in any way you want.

---

### Post by gratefulfrog on 2008-02-03
Well here are my 2 euro-cents thrown into the eternal *Linux video editor debate*. 

I've used Avid on Windows, Cinelerra and Kino on Ubuntu on an AMD64bit machine. I've compiled both Kino and Cinelerra (thanks to the great support that the Cinelerra boys provide!).

My view is this:
[LIST]
[*]big or complex movies: use Cinelerra
[*]simple things: Kino
[/LIST]

Both of these tools can now be installed directly from the Ubuntu repositories (no more compilation needed). If they can work on my platform, then I'll bet with some patience they can work on anyone's box - the key word is *patience*.

I've posted to my website beginner's instructions on how to use Kino. There's also a very old page on using Cinelerra, but most of the details have become obsolete. Check it out at:
[http://gratefulfrog.net]("http://gratefulfrog.net")

I think that the the truth is that anything but the most straightforward video editing is just not easy!

---

### Post by eye208 on 2008-02-04
> **gratefulfrog said:**
> big or complex movies: use Cinelerra
Has anyone ever actually edited a large project with Cinelerra?

I tried to find out by browsing Cinelerra's website, but it's only offering me .php3 files for download. Wtf? Cinelerra's Wikipedia page doesn't name any projects either.

Given the fact that many people fail to install Cinelerra or run it in a reliable way, I can hardly imagine anyone using it for serious stuff.

---

### Post by cotcot on 2008-02-04
> **eye208 said:**
> Has anyone ever actually edited a large project with Cinelerra?

I tried to find out by browsing Cinelerra's website, but it's only offering me .php3 files for download. Wtf? Cinelerra's Wikipedia page doesn't name any projects either.

Given the fact that many people fail to install Cinelerra or run it in a reliable way, I can hardly imagine anyone using it for serious stuff.
What do you mean with large ? I have edited video up to 20 minutes. 
Cinelerra from the repos does not give OpenGL enable. I compile it from source (svn). Check carefully the missing dependencies from what the ./configure command is giving and google on the couple of errors you might encounter during make. 

Kdenlive is also pretty good.

---

### Post by Porpoise on 2008-02-10
> **eye208 said:**
> There is no limit to the number of overlays that Blender can handle. Simple picture-in-picture effects can be achieved using the [transform]("http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Transform_Built-in_Effect") and [alpha over/under]("http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Alpha_Over.2C_Under.2C_and_Over_Drop_Built-in_Effects") effects. The transform effect will scale, move and rotate the image, adding alpha transparency to the unused areas of the frame so you can overlay it. You can apply any number of effects in any order. For sports programmes you may find the [speed control]("http://wiki.blender.org/index.php/Manual/VSE_Built-in_Effects#Speed_Control_Built-in_Effect") effect useful.

An alternate way of creating overlay effects is by using [compositing nodes]("http://wiki.blender.org/index.php/Manual/Compositing_Nodes"). The [translate]("http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Translate_Node"), [scale]("http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Scale_Node") and [rotate]("http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Distort#Rotate_Node") node types will transform the picture. [Matte nodes]("http://wiki.blender.org/index.php/Manual/Compositing_Nodes_Mattes") can be used to create chroma-key (also known as "green screen") and similar overlay effects. Think of the silhouette effect in an iPod ad.

If that's not fancy enough yet, you can use Blenders rendering engine to project video footage onto planes and other objects and modify them in 3D space. Imagine a video sequence of a room with a TV screen showing another video sequence. In fact there is hardly anything in Adobe After Effects that you can't do with Blender as well.

Entry-level applications such as Ulead Video Studio or Apple iMovie are "one-trick ponies", i.e. they provide a fixed set of prefab effects with very limited customizability. They target an audience that is looking for instant gratification without a learning curve.

Sorry, I meant Ulead Movie Studio Pro is what I use for capture and doing multi-layer stuff, then Video Studio for stitching and exporting/burning to disc (as Movie Studio doesn't do that bit - and Video Studio doesn't/didn't do that multi-layer stuff)

> Most of the tools in the open source world do not work like that. For example, there are no wizards in Blender. On the other hand there are no limits either. If you want to create a scene like [this]("http://www.youtube.com/watch?v=iN1wAZS-sWI") or [this]("http://www.youtube.com/watch?v=5XCCv4_S1rQ"), Blender has all the tools you need, and you can combine them in any way you want.Thanks for that info. I've installed Blender and managed , so far, to import an existing video clip but I'm blowed if I can figure out how to preview it or get it to display the frames on the timeline so you can actually see what you're doing. It looks like it does a multitude of stuff but it looks like it's not exactly intuitive.

Are there any help files/walkthroughs anywhere?

---

### Post by Porpoise on 2008-02-11
Well, following on from my previous posts (and replies thereto), I installed Cinelerra and was pleasantly surprised by a decent editing interface compared to Blender (i.e. one that makes sense!). At first glance, it looks like it'll cover my present needs - I'll y'all know how I get on.

---

### Post by thedaemon on 2008-02-12
> **Porpoise said:**
> Well, following on from my previous posts (and replies thereto), I installed Cinelerra and was pleasantly surprised by a decent editing interface compared to Blender (i.e. one that makes sense!). At first glance, it looks like it'll cover my present needs - I'll y'all know how I get on.


Blender's interface does make sense, you just are used to a bad interface design. Blender has non-overlapping windows and is very customizable. Most people open it up and play with Blender for about 1 minute then give up and bitch about the interface. I say less noobs asking questions.

---

### Post by eye208 on 2008-02-13
> **thedaemon said:**
> Most people open it up and play with Blender for about 1 minute then give up and bitch about the interface.
That's the curse of free software. You'll never find people bitching about the interface of Adobe AfterFX because its price tag keeps the noobs off the lawn.

---

### Post by Porpoise on 2008-06-29
> **thedaemon said:**
> Blender's interface does make sense, you just are used to a bad interface design. Blender has non-overlapping windows and is very customizable. Most people open it up and play with Blender for about 1 minute then give up and bitch about the interface. I say less noobs asking questions.

Yes, well, most people who do video editing AFAIK are used to working on a timeline with all the track/time/frame information in the window.

However, I did finally discover (totally non-intuitive) that Blender actually has several interfaces - the one for video editing (SR:4-Sequence) is not the one that opens by default, so most people (video-editors) wouldn't know what the hell they're looking at or where to go with the default 3D modelling interface or that they need to change to the other interface.

Hardly intuitive.

Cinelerra is more intuitive but much more clunky than the Windoze options (still! unfortunately) although you can produce work with it, it takes days rather than hours with the "Dark Side". And you have to go through so many different stages and programmes to get to the end result.

---

### Post by Jamin3D on 2008-06-30
> **Porpoise said:**
> Yes, well, most people who do video editing AFAIK are used to working on a timeline with all the track/time/frame information in the window.

However, I did finally discover (totally non-intuitive) that Blender actually has several interfaces - the one for video editing (SR:4-Sequence) is not the one that opens by default, so most people (video-editors) wouldn't know what the hell they're looking at or where to go with the default 3D modelling interface or that they need to change to the other interface.

Hardly intuitive.

Since Blender's primary purpose is 3D modeling and animation, it totally makes sense that it doesn't open to the sequencer by default.

As one goes through the online manual (or tutorials) they will not only quickly learn there are different Screens, but that they can create new ones and even save any screen as the default (ctrl-u = save user options).  These things are all covered in "The Interface" section of the online manual.

(on this page, specifically:
[http://wiki.blender.org/index.php/Manual/PartI/Interface/Window_system](http://wiki.blender.org/index.php/Manual/PartI/Interface/Window_system))
[SIZE="1"]
*btw, I do video editing, graphics & 3D animation for a living, and I use Avid for all editing, and Blender for all 3D animation.*[/SIZE]

---

