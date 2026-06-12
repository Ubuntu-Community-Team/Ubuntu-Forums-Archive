---
title: "A Real Pro-Level FOSS Video Editor at Last?"
date: 2010-04-12
forum: Multimedia Software
---

### Post by Ubuntiac on 2010-04-12
OK, I admit that not too much is known on this yet, but Lightworks Academy and Emmy by EditShare are apparently going open source. See:

[http://www.editshare.com/index.php?option=com_wrapper&Itemid=208](http://www.editshare.com/index.php?option=com_wrapper&Itemid=208)

No word on the license or the exact date yet, but the product description from their website is as follows:

> Academy® and Emmy® award-winning Lightworks was introduced in 1989 as the first and most advanced non-linear editing system on the market. Used by editors such as Chris Gill and multi Oscar-winning Thelma Schoonmaker, Lightworks offers intuitive controls, advanced real time effects, 2K native support with DPX or RED, and multi-camera editing features that remain unmatched. With wide support for codecs, including EditShare’s Universal Media Files, Lightworks achieves a level of unsurpassed interoperability by offering seamless media sharing with Avid and Final Cut Pro. This new workflow enables Lightworks artists to collaboratively edit projects with a much wider group of editors.

Feature Highlights:

FORMATS AND CODECS
AVI, QuickTime, MXF, DPX and RED R3D, DV, DVCPRO 50, DVCPRO HD, XDCAM HD, XDCAM EX, P2, AVC Intra, DNxHD, ProRes. Real-time up and down-scaling, from SD to 2K.

MULTI-CAM
Advanced multi-cam editing with unlimited sources and dual-SDI outputs, so you can simultaneously view your source angles in sync with your edit.

THIRD PARTY SUPPORT
Support for Adobe After Effects, Boris, Combustion, Sapphire and many more.

EFFECTS
Real time video and audio effects, including primary and selective colour correction, are all guaranteed in resolutions up to 2K, thanks to Lightworks powerful GPU based effects engine.

AUDIO
Sub-frame audio editing, direct-to-timeline voice over tool, Mackie protocol support, real time playback of mixed sample and bit rates, and guaranteed real time multi-track audio.

PROJECT SHARING
The most advanced Project Sharing capabilities available, allowing editors to access each others’ work with the click of a button. Instant Save technology ensures you’ll never lose your work again.

OUTPUT
Full-screen video output through a DVI-attached LCD display, with support up to 2K Full Frame, offering an inexpensive monitoring option, with no need for SDI hardware.

MULTI-CHANNEL INGEST
Lightworks is the only NLE available to offer multi-channel ingest, with support for synchronised capture, making it ideal for advanced 3D Stereoscopic projects.

---

### Post by CinemaScope on 2010-04-13
Hey, this could be big news. A pro NLE serious about open source...wow. Feels like I've been waiting years for Lumiera and now this (supposedly by quarter 3 this year).

---

### Post by benmoran on 2010-04-13
There are a few really good FOSS video editors already, such as Openshot and Kdenlive. Kdenlive is amazing recently. They aren't good enough for everyones needs though, so I welcome any new open source programs.

---

### Post by BobLand on 2010-04-13
Something to consider is this products support for After Effects.  I'd venture to guess this will be a Windows only product.

Then again, what exactly is a "pro-level nle"?

I'm having very good luck with Blender, which is about as close to pro-level as I'll ever get.  Especially at its price point.

---

### Post by Ubuntiac on 2010-04-13
@benmoran - Kdenlive has a really nice interface, but I've been waiting years for it to *finally* become stable and have all it's features actually work reliably. I even helped out with it for quite a while, but it seems that there is something in the project that seems to make stability an elusive goal. This is the one I would love to get better and take over, but even their latest release 7.7 had to be shortly followed up with 7.7.1 because of missed major bugs. :( Openshot (also based on the same underlying MLT library) is coming along nicely and seems more open to community assistance, but being fairly new, their stability is still about the same. I have more hope for them becoming stable, although both really are aiming at a very basic level of functionality (fine for average youtube clips though).

@bobland - I remember hearing someone say that it was cross platform, though I can't confirm off hand. As to what's pro level, take a look at the feature list posted. Most of those features aren't even on a wishlist for our current Linux editors yet. RED demuxing, ability to realistically handle 2k with gpu based accurate colour correction, support for interoperating with commonly used commercial packages. Where to begin...?

Blender is awesome, and I love it, but the editor is currently very, very basic. 2.49 still has audio syncing issues with many file formats and 2.5 alpha 2 currently doesn't even import a sequence of frames and play them back correctly on my machine correctly. I do file bugs on Blender regularly, but honestly VSE bugs shouldn't even be Durian team's focus until Durian gets into the post production phase. They're busy enough making awesome 3d at the moment. :) Blender does do awesome 3d and has nice compositing, but the editing is still very primitive. I do love me my Blender though. :)

---

### Post by Junkieman on 2010-04-15
Awesome, awesome! This will definitely up the quality of NLE's. Sounds like it has some mean collaborative editing functionality!

---

### Post by rylleman on 2010-04-15
Wow, this is really good news!
But I can't find anything about a linux release. I can't even find current system requirements. 
Or more screenshots that the small one on the site.
If they are going open source I do hope the will open up and give more info about their product.

---

### Post by BobLand on 2010-04-16
Found this from Linux Magazine.  I'm hoping that since they printed this it means it will be released for Linux.

[http://www.linux-magazine.com/Online/News/Lightworks-Video-Editor-Goes-Open-Source](http://www.linux-magazine.com/Online/News/Lightworks-Video-Editor-Goes-Open-Source)

This article explicitly states that this editor is for Linux!

[http://www.phoronix.com/scan.php?page=news_item&px=ODE1MQ](http://www.phoronix.com/scan.php?page=news_item&px=ODE1MQ)

Now, here's a bombshell from the BlenderArtists forum.

[http://blenderartists.org/forum/showthread.php?p=1609389#post1609389](http://blenderartists.org/forum/showthread.php?p=1609389#post1609389)
see msg #7
***One thing is nearly certain: this will cause interested Windows users to go to a dual boot configuration because, at present, LightWorks runs under Linux.***

---

### Post by Ubuntiac on 2010-04-17
Check out the Wikipedia entry:
[http://en.wikipedia.org/wiki/Lightworks](http://en.wikipedia.org/wiki/Lightworks)

Yes, kids, according to that it most definitely runs on Linux! :popcorn:

Also worth reading is:
[http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source](http://ostatic.com/blog/powerful-video-editor-lightworks-released-as-open-source)


Sounds like their business model is "We sell hardware. Lets ship free software that gets people using more of it. Let's also provide a marketplace for commercial add-ons and make a buck, there too while the community makes the core product better." If I'm right... It sounds promising! The actual editor is open source. There's freedom to develop it and extensions for it, and people have motivation to write commercial apps, too.

Now I just await the third quarter and to find out the license. Please let it be some variation of the GPL!

---

### Post by shaunthesheep on 2011-04-07
See [this post]("http://ubuntuforums.org/showpost.php?p=10628721&postcount=2") which provides an update on where Lightworks is at.

---

