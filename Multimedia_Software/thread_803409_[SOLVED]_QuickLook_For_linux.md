---
title: "[SOLVED] QuickLook For linux"
date: 2008-05-22
forum: Multimedia Software
---

### Post by badchoice on 2008-05-22
[COLOR="Red"][COLOR="SeaGreen"][B]THIS THREAD IS CLOSED! -> PLEASE USE THIS ONE:
[http://ubuntuforums.org/showthread.php?t=828774](http://ubuntuforums.org/showthread.php?t=828774)[/B][/COLOR][/COLOR]



Hi everyone,
I'm developing a free opensource **QuickLook for linux** in openGL (c++), 

There are the links for download, screencast and launchpad page:

  Launchpad:   [ http://launchpad.net/gloobus]( http://launchpad.net/gloobus)
  Screenshots: [http://sourceforge.net/projects/gloobus](http://sourceforge.net/projects/gloobus)
  Screencasts: [http://www.youtube.com/profile_videos?user=badchoice](http://www.youtube.com/profile_videos?user=badchoice)
  External Downloads: [https://edge.launchpad.net/gloobus/+download](https://edge.launchpad.net/gloobus/+download)

  **Donate:** [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)

Now I have it in a very good way but there are a couple of things I would like to do and I don't know how, maybe you can help me.

First one: How to bind space key in nautlius to launch my own nautilus-script (this will be used for bind space key to preview file)

Second : How to add a button on the toolbar that lauches my own nautilus-script (this will be used for launch folder coverflow)

If anyone of you know how to do this It will be one of the remaining points solved!

**Some information about**:Now I can preview, any kind of images, any kind of plain text files and pdf. It supports mp3 (album coverts and song preview)
and I'm working on video files support and plugin architecture. 

I also would like to know your ideas so this way we can make it beat apples one!!!!

Thank you!

---

### Post by rpage on 2008-05-22
wow that is pretty cool! any ideas on your release time frame?

Rick

---

### Post by badchoice on 2008-05-22
I hope in a week or two I can upload the first relase
but it wont be a final version, just for developers and beta testers!

I have somte things to add before, like put the filename name in coverflow and make mp3 playable!

I'll post it here for you all to know!

Thanks!

---

### Post by davim on 2008-05-23
Great work! I was hoping someone would implement this!

Thanks.

---

### Post by iamah on 2008-05-23
looks cool

---

### Post by zekopeko on 2008-05-24
can't wait for it. looks great. you could add a button in nautilus for quicklook.

how about moving to launchpad for the development? you get great infrastructure and can create your own repository with PPA service.

---

### Post by davim on 2008-05-24
I think moving  to launchpad would be a good idea :)

you could also integrate your project with this one:

[http://ubuntuforums.org/showthread.php?t=486359&highlight=factory](http://ubuntuforums.org/showthread.php?t=486359&highlight=factory)

to bind it to a key I think you have to make some kind of a daemon to listen for the pressed keys.

Nautilus supports plugins, maybe this could be made as a nautilus plugin...

---

### Post by zekopeko on 2008-05-24
i know that you can put a button in nautilus toolbar since timevault did it. but timevault is written in python so i would guess that the developer used nautilus-python bindings for this.
post on the nautilus mailing list your question. i'm sure that they will provide and answer.

---

### Post by badchoice on 2008-05-25
Ok! I'll put my project to launchpad, and ask to nautilus mailing list how to do this two things!!

Now I'm doing some last retouches and I will upload the first alpha release! I hope I get some feedback to keep me working on it!

Thanks!

---

### Post by davim on 2008-05-25
don't forget to give us the launchpad link when your project gets there :P

---

### Post by badchoice on 2008-05-26
Hey! thanks for the support!

I created a launchpad account and uploaded a new video!

[http://www.youtube.com/watch?v=jdKFhkX9VAo](http://www.youtube.com/watch?v=jdKFhkX9VAo)
[https://launchpad.net/gloobus](https://launchpad.net/gloobus)

Now I'm sending to nautilus-list and e-mail and hoping to get the answer!!

In a few days I'll upload the first alpha-release, with still a lot of things to do but functional!


Thanks again!

---

### Post by spg76 on 2008-05-26
The videos look great, badchoice. Nice work.
I'd read on Launchpad that you need a logo, and I made one. If you want, I can send it to you.

---

### Post by badchoice on 2008-05-27
Thanks!

Of course I want it! you can send it to me at:

** guitarboy000 at gmail dot com**


For information about the project, files I can preview now 
Images
Pdfs (just the first page, in a future i will do it to preview all)
Plain txt (Just the fist page again)
MP3 -> loads the cover art and if not found loads an standard (Needed a good loking standar cover!!!!)
MPG -> on developmen, it will play the movie in the coverflow and int the preview!!

I hope this week I can post the first release!!

---

### Post by davim on 2008-05-28
I've noticed that you are not using all the Launchpad's features are'nt you going to put your code there?

---

### Post by davim on 2008-05-28
could you add an option to have a full screen mode?

And another one to hide the cover flow window when the preview shows up?

any news from the nautilus mailing list??

---

### Post by badchoice on 2008-05-29
I'm really new to launchpad I still don't know how it works...
This week I'll upload the first version (yesterday I finished the thread) I just missed a couple of things, then I will upload the code to launchpad and start to request new features (mpeg in process for the next release).

Theres no problem for fullscreen!!

---

### Post by aantn on 2008-05-29
Do you have any experience with bzr? It's the easiest version control system I've used, and I can dig up a few links for you if you would like.

I haven't looked at the code yet, but are you using a plugin based architecture? It would make sense to separate the code for viewing individual file types from the core.

---

### Post by badchoice on 2008-05-29
Hey, no I have no experience... I would like the links to know how to use it.

I also would like to know how to develop a plugin structure, now I use a separate class called load that looks the filetype and loads it for each type with a design pattern

Something like this
previewStructure = load.loadFile(file)

and load file is something
if file = mp3 return loadMP3(file)
if file = jpg return loadJPG (file)
if file = .....

and in the preview I do diferent actions depending on file type..  . like music or MPG.

If you know a better way, or a easy way to use plugins I would be verye pleased to implement it!!

Thanks a lot

You can se a video of the last version here:
[http://youtube.com/watch?v=VCKzV7k7MrU](http://youtube.com/watch?v=VCKzV7k7MrU)

It uses threads to load the files so it shows up imediatly!!

---

### Post by aantn on 2008-05-29
> **badchoice said:**
> Hey, no I have no experience... I would like the links to know how to use it.

I also would like to know how to develop a plugin structure, now I use a separate class called load that looks the filetype and loads it for each type with a design pattern

Something like this
previewStructure = load.loadFile(file)

and load file is something
if file = mp3 return loadMP3(file)
if file = jpg return loadJPG (file)
if file = .....

and in the preview I do diferent actions depending on file type..  . like music or MPG.

If you know a better way, or a easy way to use plugins I would be verye pleased to implement it!!

Thanks a lot

You can se a video of the last version here:
[http://youtube.com/watch?v=VCKzV7k7MrU](http://youtube.com/watch?v=VCKzV7k7MrU)

It uses threads to load the files so it shows up imediatly!!

I'm not sure about the plugin system. I don't have any experience with C++. Have you tried asking on any of the GNOME or gtkmm mailing lists?

[You can find the five minute guide to bzr here.](http://doc.bazaar-vcs.org/latest/en/mini-tutorial/index.html)

---

### Post by davim on 2008-05-29
> **badchoice said:**
> 
You can se a video of the last version here:
[http://youtube.com/watch?v=VCKzV7k7MrU](http://youtube.com/watch?v=VCKzV7k7MrU)

It uses threads to load the files so it shows up imediatly!!

It's looking great :) will you provide support for compressed files? maybe you could treat them as folders...

About the plugin system, I think you could have a deamon that would receive and display the images and the plugins would be small modules that are responsible for generating the images and sending them to the core daemon.

There would be one plugin for each file type.

The daemon would be always running in the background and it could wait for a key-combo, then it would check the file type and call the corresponding plugin/module sending him the file(s) path(s), and the issued module would send the generated image/texture back to the core daemon.

I don't know how the modules would communicate with the core daemon to send the images, maybe it is possible with dBus or corba I don't know, I hope someone can help you with that, maybe someone in the compiz-fusion forums...

I hope you understand my idea :P

---

### Post by davim on 2008-05-29
just a few links for inspiration:

[http://developer.apple.com/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/chapter_1_section_1.html](http://developer.apple.com/documentation/UserExperience/Conceptual/Quicklook_Programming_Guide/Introduction/chapter_1_section_1.html)

[http://www.vvi.com/products/vvidgetcode/quicklook.html](http://www.vvi.com/products/vvidgetcode/quicklook.html)
[http://www.quicklookplugins.com/](http://www.quicklookplugins.com/)
[http://en.wikipedia.org/wiki/Quick_Look](http://en.wikipedia.org/wiki/Quick_Look)

---

### Post by yelo3 on 2008-05-29
I have an idea instead of doing the
if then return:

0) an abstract class/interface Plugin that offers the method supportedFileType() and startEffect()
1) at least one implementation of the Plugin class for each file type
2) a PluginRegistry class with register(Plugin, priority) to let the user say which plugin he prefers, unregister(Plugin) and getPlugin(fileType) in which you scan the plugin registry till you find the correct plugin to return (maybe you could store the plugins in a map<fileType, Plugin>).

I think this is a more clean way... Every time you add a plugin the only thing you have to do is to write a new class, and that's it! you don't have to change anything else!

What do you think?

---

### Post by yelo3 on 2008-05-29
I have an idea instead of doing the
if then return:

0) an abstract class/interface Plugin that offers the method supportedFileType() and startEffect()
1) at least one implementation of the Plugin class for each file type
2) a PluginRegistry class with register(Plugin, priority) to let the user say which plugin he prefers, unregister(Plugin) and getPlugin(fileType) in which you scan the plugin registry till you find the correct plugin to return (maybe you could store the plugins in a map<fileType, Plugin>).

I think this is a more clean way... Every time you add a plugin the only thing you have to do is to write a new class, and that's it! you don't have to change anything else!

What do you think?

---

### Post by davim on 2008-05-29
I agree with yelo3, you should do some kind of a library (the abstract calss/interface) so you could reuse some common code.

---

### Post by eluminx on 2008-05-29
First time i see the video and i must say, what you showcased in there, it actually looks alot better than quicklook in OS X, of course this is my opinion.  Great work hopefully this is done soon and we can all get advantage of it, once again great work...

---

### Post by badchoice on 2008-05-30
Plugin architecture is essential for this project so I'll investigate how is the best way to do it, easy and scalable.
but I don't think that a daemon is the best way...

There are minor things for this first release to be done, but I hope this weekend I'll post it!!!!!
I havn't found how to do that on nautilus and it still has to be launch with right click... 

Things to do for the next release (not this):
	.Scale the texutres to use as minium memory as possible.
	.Load just a determined number of photos depending on where you are (there is no reason for having on memory hundreds of photos when you're only 	viewing 10 or 12)
	.Do the multiple slide (now you only can slide again when transition is done)
	.Mouse support (now only works with keyboard)
	.Plugin Architecture
	.Mpg Support
	.Multipage preview support (now just loads the first page of pdf an txt files)

So there is still a lot of work to do!!!! but everything will be done!!

Thanks again for you support!

I'll give launchpad some love and learn how it works!! :D

---

### Post by yelo3 on 2008-05-30
I also think that a daemon is not useful in this case

---

### Post by davim on 2008-05-30
> **yelo3 said:**
> I also think that a daemon is not useful in this case

It was just an idea :P

---

### Post by badchoice on 2008-05-30
Hey! I've been searching on how to make a good plugin architecture based on design patterns and the one you mentioned is the best I think!
When this first version works well I'll put my efforts on design the plugin architecture and documentation so we can add a lot of diferents functionalities!!

Thank you all for the help!!!

I think it can be a great project!!
If any of you wants to contribute I'll add him in launchpad (If I find out how :lolflag:)

---

### Post by badchoice on 2008-05-30
First Version Uploaded!!

There is the code, and binaries!
I want to upload it to sourceforge but it gives me some trouble!!

I'll try again later.
[B]
[https://code.launchpad.net/gloobus](https://code.launchpad.net/gloobus)[/B]

---

### Post by k99goran on 2008-05-30
> **badchoice said:**
> Hi everyone,
I'm developing a free opensource **QuickLook for linux** in openGL (c++), you can see a demo of a little old version here:
  [http://www.youtube.com/watch?v=fo09GRwbokU]("http://www.youtube.com/watch?v=fo09GRwbokU")

and the project sourceforge page here:
  [http://sourceforge.net/projects/gloobus]("http://sourceforge.net/projects/gloobus")
Looks really nice, though I would prefer to see the coverflow animation rendered inside the Nautilus window, and to have it activated either by a button or an option in the "View as..." menu. Meaning, for this to be treated more as a view-mode in Nautilus than an external application.

Not sure if it's even possible at all...

---

### Post by davim on 2008-05-30
> **badchoice said:**
> First Version Uploaded!!

There is the code, and binaries!
I want to upload it to sourceforge but it gives me some trouble!!

I'll try again later.
[B]
[https://code.launchpad.net/gloobus](https://code.launchpad.net/gloobus)[/B]
Great news :)

I think aantn is the Launchpad expert here :P At least he must be used to working with it from his work with screenlets and awn send him a PM asking for some guide lines. :P

---

### Post by davim on 2008-05-30
I don't think that's a good idea to have the compiled binaries in the code repository...

I think you should use the download section ([https://launchpad.net/gloobus/+download](https://launchpad.net/gloobus/+download)) and put there a tarball

---

### Post by yelo3 on 2008-05-30
I've downloaded the code, and I noticed a thing that should be fixed soon if we want this package to be accepted into nautilus, or into ubuntu main. It has some dependancies that I hope can be changed:

libsmpeg0, libsdl-mixer1.2 (that can I think be replaced by gstreamer)
libmagick++10, libsdl-image1.2 (I don't know which library can replace these)
maybe others that I didn't mention, and are not installed by default in ubuntu or other distros

---

### Post by spg76 on 2008-05-30
I need some help.
I can't get Gloobus to work on my laptop (I tried on my desktop and it worked fine).
I followed the steps on the readme file and I can launch the preview (and coverflow), but I can't see any file (PNG, MP3 or PDF), only a blank rectangle. I installed the dependencies, and I think that I didn't miss anything. Maybe someone could list the dependencies?
One more thing, when I launch preview or coverflow the brightness of my screen it's reduced.
Thanks.

---

### Post by badchoice on 2008-05-31
Hey, yea, I have to change sdl_mixer and smpeg or ffmpeg for gstreamer...

the libraries that it uses now are:
GLU             (opengl)
GL              (opengl)
SDL             (easy way to use opengl)
SDL_Image       (easy way to load images)
SDL_mixer       (easy way to play mp3)
SDL_ttf         (easy way to use ttf fonts in opengl)
magick++        (to convert pdf and txt to images)
magic           (to know the true filetype)

I'll be adding some fixes from now to the next version to improve the performance, then I'll do mpg supprort and then I'll do the plugin architecture!!

Thanks a lot!

Referent to integrate it with nautilus, I think it should be made apart depending on the desktop manager cause this way it can be used both in gnome kde or other desktop. but of course it must be integrated :D

---

### Post by yelo3 on 2008-05-31
> SDL_mixer (easy way to play mp3)
you can use also gstreamer here
> magick++ (to convert pdf and txt to images)
maybe poppler can be used here instead of magick++

for the gstreamer help you can install the package gstreamer0.10-doc. You can simply play audio/video and embedding the output in your window using the gstreamer pipeline.

I also hope that you can purge SDL in the future...
I found this for loading images, if it can help you: [http://www.nullterminator.net/gltexture.html](http://www.nullterminator.net/gltexture.html)

Bye!

---

### Post by zekopeko on 2008-05-31
i'm getting this when trying to run gloobus:

:~$ gloobus Pictures/Ex-Desktops/
Error loading font: Couldn't open /usr/share/gloobus/font.ttf
Segmentation fault

EDIT: i'm running compiz if that matters.

---

### Post by spg76 on 2008-05-31
I installed all the dependencies and still and I can't get it to work.
When I'm trying to preview an image or a text file I get this:

```
preview alien-blood-2_0.jpg
Loading Music: alien-blood-2_0.jpg
```

With a PDF I get:

```
preview case_Contact.pdf
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Cancelado
```

In both cases, a blank rectangle it shows instead of the file.
And when I'm trying to preview an MP3 file I get:

```
preview 09-Nosotros.mp3
This file has no preview function
Fallo de segmentación
```

---

### Post by badchoice on 2008-06-01
Yes, it's a bug, cause a normal user hasn't privileges under /usr/share/gloobus for this it can't load the font.tff and when tring to preview a mp3 file that has no cover it tries to loat nocover.jpg under the same folder...

to solve this for now.. sudo chmod 777 -R /usr/share/gloobus

It will be fixed for the next release!

---

### Post by teolemon on 2008-06-01
On my side, I can run Gloobus and preview, but while the shapes and their reflections are here, have the right size (same ratio as the original file), there's no preview, just a blank space.

I think I've installed all the required libs.

Thanks a lot for all the work you're putting in the app. If you need help translating it into French, I'm willing to do it :-)

EDIT: the 1st post of the thread should be edited to include the adress of the Launchpad project and all new relevant information.

---

### Post by badchoice on 2008-06-01
Allways appears with a blanc shape? try diferent types of files:

   PDF
   TEXT FILES
   MP3 with cover associated and without
   IMAGES FILES

And tell me if allways appears a blank shape!

Thanks!

Remember that now you can use launchpad for bugs and new features comments! :D

---

### Post by spg76 on 2008-06-01
badchoice, I'm having the same problems as teolemon. I posted the output that I get for different files at [http://ubuntuforums.org/showpost.php?p=5085363&postcount=39](http://ubuntuforums.org/showpost.php?p=5085363&postcount=39)
Thanks.

---

### Post by teolemon on 2008-06-01
I've turned the whole thing as a bug. Feel free to add your own input.

---

### Post by Redrazor39 on 2008-06-02
WOW! That is so awesome! I would like to make a few recommendations though:

1) I was thinking of adding an elegant and unobtrusive border at first (like the black border in Apple QuickLook), but then I decided we should be unique. I think you should add a VERY heavy drop shadow (heavier than that of the active window in Mac OS X Leopard) in order to create a sense of knowing exactly what the Gloobus window is.

2) Make it so the Gloobus viewer opens in the exact center of the nautilus window. Also, I LOVE the idea of opening coverflow when showing a folder in gloobus instead of just showing folder info. AWESOME, but make it so that coverflow opens in the exact center of the nautilus window and the Gloobus preview from the coverflow opens in the exact center of the coverflow window. That would add some professionalism and make it easier for the user to find instantly.

3) I love your idea of coverflow for Gloobus-ing folders (as I said before), but I don't think we should copy Apple's coverflow style. I think we should have something slightly different somehow. I'm not saying it's bad-- keep the coverflow if we can't think of anything else, but maybe two stacks of files or pictures on either side of the file you are viewing, and a nice, smooth, flowing effect from face up vertical on the card flippig up and out into view of the user.



I'll keep this remembered-- Good luck!

---

### Post by davim on 2008-06-03
just found a QT version of coverflow -> [http://code.google.com/p/pictureflow/](http://code.google.com/p/pictureflow/)

[http://ariya.blogspot.com/search/label/pictureflow](http://ariya.blogspot.com/search/label/pictureflow)

the cool thing about it is that it is a QT widget, meaning it could be embed into QT windows (and it doesn't use OpenGL) it would be cool to make gloobus as a GTK+ widget....

---

### Post by teolemon on 2008-06-04
For a quick summary of all available solutions, see:
[https://blueprints.edge.launchpad.net/ubuntu/+spec/hardy-sparkle](https://blueprints.edge.launchpad.net/ubuntu/+spec/hardy-sparkle)

---

### Post by zekopeko on 2008-06-08
any word on the progress of this?

---

### Post by badchoice on 2008-06-08
Hi!

Just now I've uploaded a video on youtube showhing the new features:

[http://www.youtube.com/watch?v=qwM4B7DJr6w](http://www.youtube.com/watch?v=qwM4B7DJr6w)

Document Multipage preview (Smooth Transition)
Folder Preview (The filen cover.jpg inside the folder)

Fixed some bugs, a lot of code formatting and cleaning so.

Next 3 primordial steps:
 1. fix the blanc shape bug
 2. load mpg filesa es
 3. Plugin Architecture

I'll be post here in ubuntu forums the news, and you can download the cod e of the last version at launchpad!!

[http://launchpad.net/gloobus](http://launchpad.net/gloobus)

---

### Post by zekopeko on 2008-06-08
last code added to bzr was 6 days ago so I'm guessing that you didn't push it just yet or the system need some time refresh.

anyway could you compile the new binaries and post them on lp or here?

---

### Post by davim on 2008-06-08
Very cool! The multiple page preview is very cool :)

---

### Post by Redrazor39 on 2008-06-08
Have you uploaded your project to launchpad yet? Maybe you could get some more devs and others to help you out (unless you want to work alone for some reason)

---

### Post by badchoice on 2008-06-09
You're right, it **wasn't uploaded right on launchpad** code, anyway I'll post the binaries but remeber it's still an **alpha version** with a lot of bugs to be solved.:KS

I haven't any problem if anyone wants to collaborate, I would like to work with more people on it cause it will speed up the development, provide new ideas, fresh air etc...

---

### Post by aantn on 2008-06-09
Have you read Karl Fogel's excellent book Producing OSS? [There's an online copy available here](http://producingoss.com/), and I think you'll find it quite useful.

---

### Post by Nergar on 2008-06-09
It would be nice if you could upload the source to launchpad. It would help testing and others can cooperate at least with some patches.

---

### Post by badchoice on 2008-06-10
The code is already uplodad at launchpad!
There is not the last version cause I had an issue and I havn't get home till then so I couldn't fix it! as soon as I get home I upload the last version with folder preview and document multipage!

---

### Post by aantn on 2008-06-10
You can download a copy of the source with *bzr branch lp:gloobus/0.1* and use *bzr pull* to update.

---

### Post by badchoice on 2008-06-10
The last version code is now in launchpad, I'll upload binaries as soon as I can.

Anyway I created a paypal account for donations, I put a lot of time and effort on this project so if anyone wants to contribute economically here you have the direction.


**[http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**


Thanks a lot!

---

### Post by goanga on 2008-06-10
Hello,

Gloobus seems to be a great project, however I can't get it to work :)
I installed all dependencies but i get the same errors as [Bug #236596]("https://bugs.launchpad.net/gloobus/+bug/236596") - white squares instead of previews, no fonts and no shadows.
Also preview opens a window but crashes immediatly with a seg fault.
Trying to run them from the command line shows no errors. Disabling compiz also doesn't help. 
I tried compiling the code, but I don't have all the dev libs. I'm now trying to identify and install them, but it'll be a while :)

Update: managed to compile the code, same behaviour. Also, when gloobus-ing large directories, the programs hangs with 100% CPU.

---

### Post by badchoice on 2008-06-10
It's a very annoying bug... I don't know why it happens and I only have two computers to test it...

My proposed solution is that in the next code, instead of adding new features I'll put my efforts on show a lot of debug messages so we can see what is doing every moment and see if we can find out what is the problem.

In the other hand, when trying to load a very large folder, it loads all files at once (in gloobus) so it will slow down a lot the computer, its pending to be done that in memory only holds about 10 or 12 images.

I'll say it here and in launchpad when the debug version is ready!!

Thank you!

---

### Post by badchoice on 2008-06-13
Well, these days I've been developing the plugin architecture!!!!

I'm very satisfied how it worked out, now with this its a very scalable infrastructure.

Now with the plugins I'll do that each one can implement his own render and loadTexture function (or use mine) so we'all can test in a very easy way why te blanc shapes bug appears!! and develop new plugins for .odt xml psd etc... etc... etc...

Then there could be two developing ways, one for plugins and other for the gloobus itself, better infrastructure, less memory, faster and all this.

I spoke with a guy from nautilus and he told me that bind a key is still not possible but it is to add a toolbar button with naultiluslib-extension.

I've a lot of things to do!!! I'm very happy with this projecte and I hope it will be a great one!

Thanks!

---

### Post by zekopeko on 2008-06-13
this already is a great project.
is it possible to open gloobus INSIDE the nautilus (like on mac) and not in it's own window?

btw did you update the binaries with the newest code?

EDIT: look like you did update the bins. thanx.

---

### Post by pt123 on 2008-06-13
wow some how managed to find this thread by accident you should create a shoutout thread for this with the title Gloobus in the Community cafe, a lot of Linux enthusists hang out there
[http://ubuntuforums.org/forumdisplay.php?f=11](http://ubuntuforums.org/forumdisplay.php?f=11)

---

### Post by pt123 on 2008-06-13
oops double post

---

### Post by badchoice on 2008-06-15
**[COLOR="Red"]Version 0.02 is out!![/COLOR]**

It has the preview wit plugin architecture, this way we can find and solve problems in a very easy way and now, everyone can develop his own plugin. When everything is more stable I'll post a quick guide on how to implement your own plugin. I hope we can preview almost all the files!!

**Download:** [https://launchpad.net/gloobus/gloobus-0.02/0.02](https://launchpad.net/gloobus/gloobus-0.02/0.02)

And remember, you can donate me some money ;)

**DONATE: [http://widget.chipin.com/widget/id/0b88c464e8dfbcce](http://widget.chipin.com/widget/id/0b88c464e8dfbcce)**

---

### Post by aantn on 2008-06-15
> **davim said:**
> just found a QT version of coverflow -> [http://code.google.com/p/pictureflow/](http://code.google.com/p/pictureflow/)

[http://ariya.blogspot.com/search/label/pictureflow](http://ariya.blogspot.com/search/label/pictureflow)

the cool thing about it is that it is a QT widget, meaning it could be embed into QT windows (and it doesn't use OpenGL) it would be cool to make gloobus as a GTK+ widget....

I'd like to second that idea. I think the ideal way of organizing things would be to break it into several components:

1. A library for loading preview images using your plugin system.
2. A GtkWidget for showing a loaded image.
3. A generic GtkWidget that provides a coverflow animation on *any* other set of widgets.

Organizing it in this way would let it be used in other applications like [this.](http://forum.compiz-fusion.org/showthread.php?t=8767)

Also, can you please update the INSTALL and README files with a bit more information? (E.g. Ubuntu package names.) It would make installation a lot easier.

---

### Post by spg76 on 2008-06-15
badchoice, I just installed the new version and I'm still having the same trouble as before (white rectangle with most files, and no preview with some other files).
I can send you some feedback if you tell me what you need.
Thanks.

---

### Post by damis648 on 2008-06-15
Hello, thank you very much for this, I see lots of potential in it. However, I cannot get it to run smoothly. I can start it and flip for a few seconds, and then it crashes with a segmentation fault after a few seconds. This even happens if I am not flipping. Any suggestions?

---

### Post by badchoice on 2008-06-15
Yes.. there are still some bugs, now I'm trying to solve them.
Just now I'm centered on the preview function and see if it can solve the withe shapes bug. Now i have uploaded new version of the plugin iText and iPdf that don't use SDL_image anymore and are improved a lot!!

When I have it preview Ok, I'll make gloobus(coverflow) work with this plugin architecture and solve this segmentation faults problems!!

Thank you all for you support!

---

### Post by morbidous on 2008-06-18
> **aantn said:**
> 
1. A library for loading preview images using your plugin system.
2. A GtkWidget for showing a loaded image.
3. A generic GtkWidget that provides a coverflow animation on *any* other set of widgets.


I would like to add another point in this list: the coverflow animation should be coded as a plugin, as well. This way we can have other animations for doing the transitioning, being able to create new ways to make transtitions based on user preferences or file type.

Just imagine an animation that resembles a page turn for pdf files or other cool effect for navigating between movie files. This would be awesome!

---

### Post by Islington on 2008-06-23
[http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux](http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux)

help digg it up!

---

### Post by KhaaL on 2008-06-23
> **Islington said:**
> [http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux](http://digg.com/linux_unix/Gloobus_a_QuickLook_for_Linux)

help digg it up!

Done :P

Cool project, keep up the awesome work!

---

### Post by aantn on 2008-06-24
I get the following when running the installation script:
```
natan@natan-desktop:~/Code/gloobus-0.02$ sudo ./install.sh 

Installing Gloobus

Directory exists
 Copying plugins
cp: cannot stat `./plugins/*': No such file or directory
 Copying Data
 Copying Binaries
cp: cannot stat `preview': No such file or directory
cp: cannot stat `gloobus': No such file or directory

Installation OK

```

---

### Post by badchoice on 2008-06-24
Do you have the folder plugins and the files gloobus and preview in the same folder where you have install.sh ???

Anyway, you can do it manually, just create the folders

1. /usr/share/gloobus
2. /usr/share/gloobus/plugins

copy the files inside DATA in 1. and copy the files inside plugins in 2.

Then just copy the binaries gloobus and preview on /usr/bin

I hope it helps you!

---

### Post by davim on 2008-06-25
is there a PPA repository for gloobus??

---

### Post by fazillatheef on 2008-06-26
When folder is displayed .. filenames of the files inside the folder can be displayed.

You could use some kind of filter for folders.When a folder appears in gloobus the user can enter text that can filter and display filenames in the folder.

---

### Post by belovedmonster on 2008-06-26
How hard would it be to port this over to work with Thunar?

---

### Post by zekopeko on 2008-06-26
AFAIK gloobus isn't GNOME/KDE dependant. if thunar has something like nautilus scripts or keybinding you could use it with it.

---

### Post by badchoice on 2008-06-27
Hes right, by now isn't plataform dependent so you can use it anywhere that supports openGL (KDE, GNOME, XFCE...) you just need to create a launcher for the gloobus and the path and/or for preview and the path/file as parameter.

I hope it helps  you!

---

### Post by gsiliceo on 2008-07-14
The window outside nautilus, it feels hacked, if you could integrate it to nautilus that would pretty much own the world.

---

### Post by badchoice on 2008-07-15
I'm searching on how to do this.. but I have not a place where start, there are people that suggested me things but I can't do it alone, I would like someone whit nautilus experience that guides me...

---

### Post by yelo3 on 2008-07-15
You can join the nautilus mailing list!

---

### Post by gsiliceo on 2008-07-15
I wish i could help you, but good luck on that.

---

### Post by ryanhaigh on 2008-07-22
This is simply fantastic. My Partner saw the Mac Preview feature for the first time today and thought it was pretty cool so I thought I would see if it is available for linux/ubuntu and here it is. I use gutsy on my primary desktop but this even worked in my VirtualBox hardy install (albeit a little slowly). I am going to see if it will work on gutsy tomorrow but the libraries are obviously a little behind those in Hardy.

As a small suggestion do you think it would be possible to pull in the native folder icon from the theme currently being used? Not sure if there is a desktop environment agnostic way of doing this?

Simply amazing work! Happy to offer my small paypal contribution to see it continue.

---

### Post by badchoice on 2008-07-23
Hey! thank you a lot for your comment! I really apreciate the donation, these things makes me keep working on the project! I've subscribed to nautilus-list to see if anyone can help me in integrating it, anyway now I'm developing the iMovie plugin, but its the hardest plugin since now.. when I'l finish it i'll upload the new version very improved!!

Thank you again!

---

### Post by ryanhaigh on 2008-07-23
Im VERY happy to report that gloobus 0.024 works perfectly on Gutsy with only a very minor modification to the installation process. For gutsy the libMagick++10 package is not available with the closest available version being libmagick++9c2a so you need to change the dependancy installation from this

```
sudo apt-get install libsdl-mixer1.2 libsdl1.2debian libsdl-ttf2.0-0 libsdl-image1.2 libmagick++10 libmagic1 libtag1c2a libavcodec1d libavformat1d libswscale1d libsdl-gfx1.2-4
```

To this 
```

sudo apt-get install libsdl-mixer1.2 libsdl1.2debian libsdl-ttf2.0-0 libsdl-image1.2 **libmagick++9c2a** libmagic1 libtag1c2a libavcodec1d libavformat1d libswscale1d libsdl-gfx1.2-4
```

Once those packages are finished installing create a symbolic link to the .9 library from the .10 file that gloobus/preview look for 

```
sudo ln -s /usr/lib/libMagick++.so.9 /usr/lib/libMagick++.so.10
```

Proceed with the rest of the installation as normal and you have working (much better than in a VM) gloobus and preview.

Badchoice I will post this in the other thread I found (we should really see about getting them merged) and maybe on launchpad too.

---

