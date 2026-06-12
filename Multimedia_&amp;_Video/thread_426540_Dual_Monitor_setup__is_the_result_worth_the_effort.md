---
title: "Dual Monitor setup:  is the result worth the effort?"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by mijj on 2007-04-28
I'm a novice Ubuntu user (just a few days of experience).

I have a dual monitor setup for WinXP that is *very* practical .. not a gimmick.
In fact, i wouldn't be  surprised if a significant proportion of people have dual monitor setups now that LCD monitors are common and use so little deskspace.

I was prepared for a long haul effort to find out how to get a dual monitor setup working for ubuntu.

However ... I came across this site which has some  useful observations ...
[**[COLOR="SeaGreen"][SIZE="3"]_http://www.redinnovation.com/blog/topics/ati_[/SIZE][/COLOR]**]("http://www.redinnovation.com/blog/topics/ati")

It looks like the best that can be done is to demo that Ubuntu can have a dual monitor setup, but it'll never be more than a rough implementation so it wont be much practical use.

... does this look like it's true? 

... if so, it's saved me a lot of effort in going down a dead end.  
.. and, for me,it's reduced the utility of Ubuntu.  (e.g. On a piece of work no longer being able to use several windows simultaneously - breaking from a mindset to hunt around for relevant windows is going to be annoying now that i've gotten used to having ref material and working material conveniently arranged across 2 monitors.)  No amount of wobbly Beryl windows is gonna make up for that shortfall.

This isn't a question of *how* to implement dual monitor for Ubuntu .. it's a question of *how rough* the successful implementation is and if it's worth the effort.

---

### Post by mijj on 2007-04-28
*(shudders at the thought that Windows can never be abandoned)*

---

### Post by TheMono on 2007-04-28
Yes, you are right, it is not easy.

However, it does work perfectly when done. It really depends on your graphics card how hard it will be though.

If you have one from Intel or Nvidia, won't be too bad. If it is ATI, no promises....

Just going over this persons comments on Nvidia twinview:


    * You cannot configure screen resolution and layout with end user applications - this one is true

    * Started application windows are opened on the wrong monitor - untrue

    * Applications don't necessary know on what monitor they are and are opening dialogs to wrong monitors - the vast majority do, I don't use any that don't in my day to day usage.

    * If screen resolutions don't match, which they rarely do, there is some mysterious empty space around the smaller resolution monitor and you can move mouse cursor off screen. This is very annoying since it makes hitting the scrollbar at the right edge of the screen with mouse cursor very difficult. - Basically the same happens in Windows... It is kinda logical when you think about it. 

    * Size estimations fail in applications because of fake total screen resolution - Untrue

    * Monitor specific taskbar and other panels don't necessary work - Untrue in GNOME, KDE, and XFCE.


Plus, for example you can't have a taskbar on your second screen in XP without 3rd party hacks. In linux, it is as easy as just making another - plus Kubuntu and Xubuntu support different wallpapers for each monitor, which XP does not (I don't know about vista).

So, in conclusion, don't let one guy's cluelessness put you off.

---

### Post by TheMono on 2007-04-28
Just as an addendum: to answer the question posed in the subject line, yes, it is worth the effort. And to mitigate calling the guy who wrote that page clueless, he is right about the pain of setting it up. Command line acrobatics really should not be called for.

---

### Post by Mike'sHardLinux on 2007-04-28
It seems hard when you haven't done it before, but I find it to be pretty easy now. When I re-format and re-install, I don't even have any kind of step by step to get it going. I just get the base install, do some basic xorg.config tweaking, and restart X. If I run into a snag, or forget something, I get on the Ubuntu forums and always find the answer I need quickly.

Honestly, I don't think it ever takes more than 20 or 30 minutes to get it going from a base install, if even that long. I just installed Feisty on my laptop earlier this week, and from what I am seeing, it may be even easier.

With this community, I am pretty sure you can get it going, unless there is some weird quirk with your hardware. Even then, someone may already have a workaround.

At any rate, I almost can't live without dual monitors.

---

### Post by mijj on 2007-04-28
I have no objection to going through long drawn out pain to get a dual monitor desktop set up .. as long as i'm sure it works as i would expect when it's been set up.

The question is about the quality of detail of use of the dual monitor desktop and how useful it really is in Ubuntu.

stress: I want to be sure it works as i expect it to work before i start the long painful journey of installation.

The link referenced in the first post implies that the end result is scruffy.  Has anyone who's succsssfully implemented a dual screen desktop found that his criticisms are false? (detail please)

---

### Post by mijj on 2007-04-28
I guess TheMono answered the point about the quality of the result ...

... i guess i shall make the effort, though i'll put a hold on assumign thta the result will work like i expect.


... and another point .. How come the developers of the various Linux flavours have thought this problem to be so insignificant?

---

### Post by tgalati4 on 2007-04-28
I have been playing with Freespire 1.0.13.  I installed it on a spare machine.  I noticed that it had "2nd Monitor" greyed out in the display resolution dialog.  Perhaps an easier way to get dual monitor is to boot with the Freespire Live CD, set up two monitors using the System Settings-->peripheral-->Display and setting up both monitors.  Then print out the resulting /etc/X11/xorg.conf file for use in Ubuntu.

This has the advantage of using a Live CD to test your video cards for basic operation and creating a semi-proper xorg.conf that can be tested tweaked later in Ubuntu.

I have dual display (one on top of the other) set up on a Dapper box.  It works quite well.  I have two different resolutions specified because the monitors are slightly different sizes and I can overlay windows between the displays and keep them somewhat aligned.  The mouse scrolls smoothly between the displays.

Sometimes an application will start in a window where the mouse was last clicked, so if you are moving around, you may get an application pop up in an undesired position.

You can use the Gnome desktop pager to drag windows between virtual desktops and to move them from one display to another.

I will admit, dual display is a breeze to set up in Windows.  This is the one thing that MS got right in windows.

It's certainly worth the time to set up.  Remember, you only have to do it once.  Make a backup of your existing xorg.conf file.

The final point about development of the X Windows system.  I was using it at MIT in 1983.  It was developed under Project Athena in the late 70's.  Xclock, xcalc, xload, all of these utilities have not changed in 30 years!  So unfortunately the xserver is based on a pretty old client/server model, but it has been working for all of these years and it is the foundation of just about every desktop.

The fact that it works at all is a miracle.  When is ssh into a machine over the web and then run xload & I smile when I see that little window pop up.  I think the X system is here to stay.  Remember X got its name as being one step beyond the W window system.

---

### Post by Mike'sHardLinux on 2007-04-28
mijj, unless I have missed something, you haven't specifically stated exactly what features you require that you think might not work.

That blog has a lot of stuff that isn't right, at least not in Ubuntu. I don't know what the heck the blogger means when he/she says you can't use end-user apps to configure the screen resolution and layout. If he's referring to having/not having a gui front-end to configuring X, well, there's no surprise there. Actually, there is a gui screen res app. but it doesn't work properly with dual screens.

For me, started application windows generally open on the monitor which they were last opened. Some programs will open on a monitor with no open windows vs. a monitor with open windows. And some programs seem to want to open on the window where the mouse cursor is located.

The opening dialog on the wrong monitor sometimes happens, but again, when that happens, it seems to be following the mouse cursor, and there is a certain logic to doing this.

The thing about the screen resolutions not matching....Who in the heck has dual monitors set up with different resolutions?? I tried this before and it is very annoying. Once, I thought it might be good to have a monitor set at a specific res as a "preview" monitor for things like video editing or web design, but hated it. *But, I tried and hated this in windows, too.*

I haven't had any issues with size estimations failing that I can remember. If I maximize a window, it fills it's current screen, but I can also drag the window to fill both screens if I want.

I can drag windows to a monitor from the other monitor.

I think that blogger doesn't understand what he/she is doing. Maybe they followed a tutorial and missed some steps? It really helps to know a little about whats going, ie, what the specific settings do in the .conf file. I've noticed several how-tos that aren't very good for different reasons. The best how-tos are the ones that explain what each step and setting is for.

---

### Post by mijj on 2007-04-28
bloody hell .. i got it working ... (ati radeon 9550)

i simply blindly edited the xorg.conf according to this link 
[**[COLOR="Green"][SIZE="3"]http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf[/SIZE][/COLOR]**]("http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf")

the graphics on stuff like moving windows around seems to have slowed down .. but ... the stuff teh guy i originally linked to was misleading on how it messes up

maybe i can mess further iwth xorg.conf to improve the graphics.  (there's also a black vertica bar on the left side of the left monitor) - looks promising tho

:)

---

### Post by Mike'sHardLinux on 2007-04-28
Good for you!!! That wasn't so bad, huh? :-)  Linux sure does get a often undeserved bad rep! If only people knew the whole story.

As for the black bar, I believe your monitor is not syncing properly. Tell your monitor to "Auto Adjust". That should fix it.

---

### Post by mijj on 2007-04-28
on checking .. the frame rate is ok .. 60hz ... but the frequency of the display in Ubuntu is 65.4 kHz (in windows it's 64kHz) .. the width wont adjust sufficiently low on the monitor control.

 ... is there a way to adjust this within the config file ... the horizontal freq should be a little lower (ideally 63kHz for a 1050 line display @ 60Hz)
Is there a way to adjust the freq in the config file?

still .. it's not like it's bad .. just a detail.


(edit: ... i suspect the above is gibberish)

---

