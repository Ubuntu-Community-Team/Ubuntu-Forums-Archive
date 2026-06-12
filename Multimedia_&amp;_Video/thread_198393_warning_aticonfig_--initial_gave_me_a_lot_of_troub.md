---
title: "warning aticonfig --initial gave me a lot of trouble whith wide desktop/tv-out ati"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by TLE on 2006-06-17
It may be that I'm just a total idiot for not figuring this out right away :---) , but it actually gave me a lot of troble so I thought I would share my discovery.

This is a rather long post so I'll give a short description of the contents first. [INDENT]Trying to configure tv-out with the fglrx drivers (on X800XL card) using the --initial switch in aticonfig gave me *nothing* but trouble and was *not* needed for the solution. So if this catches your attention please read on.[/INDENT]

I was trying to configure a wide desktop to expand onto my tv so that I could just drag totem onto the TV when I wanted to watch a movie. So I installed the fglrx drivers* and decided that I would like to try and use whatever tools were installed with those drivers for this task. To sort of give those ATI folks another chance to prove themselves;)  After installing the drivers I ran ```
dpkg-reconfigure xserver-xorg
``` to activate the drivers and it worked**.
Now came the time to try and make the wide desktop tv-out configuration. I fumbled a little around on the web and found references to aticonfig. I ran that and got a rather extensive help text explaning all the options. Then at the button there were som examples, among these is this text
```
Examples:
  1. Setting up fglrx for the first time.
       Single head :    aticonfig --initial --input=/etc/X11/xorg.conf
       Dual head   :    aticonfig --initial=dual-head --screen-layout=above
                        This command will generate a dual head configuration
                        file with the second screen located above the first
                        screen.

```
So I figured, well I'm setting up fglrx for the first time so I probably have to use the --initial switch, so I read about this a little further up where it says
```
ATI Initial Configuration:
  --initial
        Generate a default ATI device section in the configuration file which
        is capable of loading the fglrx driver.
  --initial=dual-head
        Same as '--initial' but generate a basic dual head configuration file.

```
SO I FIGURED that, using the --initial switch, the aticonfig application would somehow read my xorg.conf and create a new xorg.conf that would be optimized for the fglrx drivers and all it's options, but that it would be *based on how I had set it up*....! This however did not seem to be the case for me. I did this and tried all sorts of different configurations including my TV and got all sorts of wierd results, like setting up clone only to find out that the TV would only show 600x480 pixels of my screen no matter what(ususally it is not possible to clone above 1024x768 but this was ridiculous), or setting it up to a wide desktop only to find that output on my TV was streched or that black bars was added at the top and buttom:confused: At this time I was about ready to give up on Dapper and fglrx alltogether. What got me going a little further was that I noticed that there was also some changes in what resolutions were available. (I may be remembering this wrong, since aticonfig claims that it only modifies the graphics card section and not the screen, but this is how I remember it) so I figured that maybe this --initial went a little to far in creating a *default* xorg.conf. So I decided to try and do it without this option. So I did a new ```
dpkg-reconfigure xserver-xorg
``` to get a fresh xorg.conf, and then I ran the aticonfig *but only with the configuring options* --desktop-setup=clone or --desktop-setup=horizontal depending on what I was trying to set up, *and it worked !!! right away*. So I suppose my conclusion will have to be DON'T use the --initial switch for a first try, instead just ```
dpkg-reconfigure xserver-xorg
aticonfig --desktop-setup=horizontal
``` THAT is what worked for me.

Regard TLE

*which are actually needed to get any resolutions working with a frequency above 60 Hz (on CRT so definitely needed, ahhh my eyes) with that damned Ati X800XL I have
**Please notice that I off course backed up my xorg.conf like a million times during all of this

---

