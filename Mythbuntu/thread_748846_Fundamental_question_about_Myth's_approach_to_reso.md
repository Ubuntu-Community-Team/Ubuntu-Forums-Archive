---
title: "Fundamental question about Myth's approach to resolution and scaling"
date: 2008-04-07
forum: Mythbuntu
---

### Post by QA_manager on 2008-04-07
What is the MythTV paradigm regarding displays, resolution, and scaling?

As I see it, there are two obvious ways to deal with this question:
 1) Assume that the display requires a fixed input resolution; scale everything to fit.  For example, if the display is 1920x1080, then a DVD input file at 720x480 would be automatically scaled to 1920x1080.  An OTA sports program at 720P would be automatically converted to 1920x1080.  This may be a good approach for fixed-pixel displays (plasma and LCD) and particularly for computer displays that don't understand HD modes.

 2) Assume that the display can handle any valid SD or HD mode; pass through all video unaltered.  This may be a good approach for CRT televisions that inherently understand and can display any valid SD or HD mode.  For example, I have a Sony CRT HDTV with DVI (HDMI connector) input; it can display any valid SD or HD format without scaling.

Paradigm #1 works with any display; Paradigm #2 works only with displays that understand any valid format, but it saves CPU cycles on the Myth frontend and may allow you to use a lower-powered (and therefore lower heat and noise) system.  Also, Paradigm #2 preserves progressive and interlaced inputs, so sports programs display in their preferred progressive format and travel documentaries in 1080i.

It appears to me that MythTV follows paradigm #1, but I can't find this documented anywhere.  It appears to be one of those things that everyone just assumes that everyone knows (but of course the newbies can't know it if it isn't explained anywhere).

So, does MythTV automatically scale everything, or is there a magic switch that says 'Pass all video through unmodified - no scaling, no conversion, no filtering'?

---

### Post by Caps18 on 2008-04-08
I thought that there was an option to choose 1920x1080 output, and I am wondering if it is really doing this now.  My LCD TV tells me that when I am using the menu it is 1280x720.  I don't mind that, but I will check the TV shows when I get home to make sure they are still playing in 1920x1080.  I do know that my current processor isn't fast enough to do 1080p content however.  However, both my LCD TV and projector can handle 1080i (or p with a cpu upgrade).  My video card shouldn't be a problem either.

---

### Post by QA_manager on 2008-04-09
Thank you, but my question is not whether Myth can output 1920x1080 (I know that it can), but whether it can pass through any HD format unmodified.  My television can display any HD format - there is no need for prescaling or interlacing - so the highest-quality approach for me is to have Myth simply decode the MPEG and let the resolutions fall where they may.  I want to know how whether Myth can be configured to do this.

So on your system - if you switch to a news program, does your TV show that the format is 1080i?  If you then switch to a sports program does your TV say that it is 720p?  If the format switches on different programs, then you have Myth configured for Paradigm #2 (the way I want it to work).

---

### Post by Trollslayer on 2008-04-11
> **QA_manager said:**
> What is the MythTV paradigm regarding displays, resolution, and scaling?

As I see it, there are two obvious ways to deal with this question:
 1) Assume that the display requires a fixed input resolution; scale everything to fit.  For example, if the display is 1920x1080, then a DVD input file at 720x480 would be automatically scaled to 1920x1080.  An OTA sports program at 720P would be automatically converted to 1920x1080.  This may be a good approach for fixed-pixel displays (plasma and LCD) and particularly for computer displays that don't understand HD modes.

 2) Assume that the display can handle any valid SD or HD mode; pass through all video unaltered.  This may be a good approach for CRT televisions that inherently understand and can display any valid SD or HD mode.  For example, I have a Sony CRT HDTV with DVI (HDMI connector) input; it can display any valid SD or HD format without scaling.

Paradigm #1 works with any display; Paradigm #2 works only with displays that understand any valid format, but it saves CPU cycles on the Myth frontend and may allow you to use a lower-powered (and therefore lower heat and noise) system.  Also, Paradigm #2 preserves progressive and interlaced inputs, so sports programs display in their preferred progressive format and travel documentaries in 1080i.

It appears to me that MythTV follows paradigm #1, but I can't find this documented anywhere.  It appears to be one of those things that everyone just assumes that everyone knows (but of course the newbies can't know it if it isn't explained anywhere).

So, does MythTV automatically scale everything, or is there a magic switch that says 'Pass all video through unmodified - no scaling, no conversion, no filtering'?


The best method is to set the MythTV resolution to that of the TV and let the graphics card to the scaling.
Remeber the TV has to scale any source to it's native resolution anyway.
If you really want to avoid scaling then it gets very complicated and your picture could be a lot smaller.

---

### Post by QA_manager on 2008-04-12
Quote:
*"the TV has to scale any source to it's native resolution anyway"*

That is true for fixed-pixel displays (LCD and Plasma) but not for CRT displays.  A CRT can natively display 1080i, 720p, and 480 w/o any problem.  With a high-quality CRT display (such as my high-end Sony) it is preferable to deliver the unmodified video to the television and let it handle everything - interlace, scaling (if needed), even 3:2 pulldown.  

The advantage of delivering the unmodified video is that 720p sports programs deliver smooth motion (displayed in 720p) and high-res landscapes display in their native 1080i.  Also I can use a lower-powered CPU, therefore generating less heat and less cooling fan noise.

So the original question is still unanswered - does MythTV automatically scale everything, or is there a magic switch that says 'Pass all video through unmodified - no scaling, no conversion, no filtering'?

---

### Post by laga on 2008-04-12
> **QA_manager said:**
> 
So the original question is still unanswered - does MythTV automatically scale everything, or is there a magic switch that says 'Pass all video through unmodified - no scaling, no conversion, no filtering'?

The thing that actually drives your TV is the X server (and your VGA card, of course). The X server sets a resolution and MythTV scales everything to full-screen (usually using Xvideo).

You can disable scaling in MythTV, but you probably have to edit the source (small patch). In some videout output modes, MythTV doesn't do scaling because it'd be too slow (NO_XV=1 might already do the trick. No guarantees though :)).

But the problem here is that X still drives your TV at the same resolution. If the video resolution is 720x480 and your display runs at 1024x768, you'll get black bars around the video if it's not scaled.

To achieve what you want, you'd need to change the resolution in X to match the resolution of your video. I'm not sure it's possible by default, but some simple Xrandr calls might just do the trick. However, I think for "odd" resolutions you'll have to supply modelines.. And if your have video files with lots of different resolutions, it's going to be tricky. Especially if your TV doesn't like some resolutions (hint: read the manual before frying your hardware, with regards to your second paradigm in your first posting).

There is some xrandr support in MythTV, but I don't know if it can change the resolution based on the video res.

I'm not sure if it's worth the hassle, but maybe you want to perform some experiments with different resolutions and let us know what looks better. Don't fry your TV ;)

---

### Post by QA_manager on 2008-04-12
Excellent; thank you!  That really answers the question - MythTV uses paradigm #1.  You also went well beyond answering the question by discussing how it might be possible to change to paradigm #2.

I'm not too concerned about the modelines since I am using DVI for the connection and the TV returns the allowed modes (all the standard HD and SD modes).  Also not too concerned about odd resolutions in the video since all of my source material will be either OTA HD or original DVDs.

So it sounds like I can do the experiment by setting my X resolution to match the video source of the moment and turning off filters in Myth.  If I change the Myth sourcecode then I would certainly have to include safety checks so that we don't try to switch X to some bizarre resolution if the video happens to have been scaled oddly.

Well, not this weekend... sigh... too many other projects to work on.  :-)

---

