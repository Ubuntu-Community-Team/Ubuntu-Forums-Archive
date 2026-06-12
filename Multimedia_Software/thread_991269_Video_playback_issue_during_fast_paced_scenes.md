---
title: "Video playback issue during fast paced scenes"
date: 2008-11-23
forum: Multimedia Software
---

### Post by dn* on 2008-11-23
My video card is a nVidia 8600 GT with the 177 rev of the proprietary drivers enabled on an updated Intrepid Ibex. Compiz-fusion is turned on.

When I play video files (in any video player) they play fine but in action packed scenes with a lot going on, there is a noticeable 'slice' to be seen wherever the action if taking place.

Although not a deal breaker, it is one of the minor issues that has been bothering me for a number of releases now. My only guess is that it has something to do with monitor refresh rates.

---

### Post by ajgreeny on 2008-11-23
Try turning compiz off and see if that helps.  It can sometimes be the straw that breaks the camel's back, just one thing too much for the videocard to cope with.

---

### Post by cariboo on 2008-11-23
IT may also be a problem with your monitor, if you are using an LCD monitor, the response time may not be quick enough.

From wikipedia:
> LCD screens with a high response time value are often unsuitable to play fast paced computer games. The pixel response time is often confused with the LCD input lag which adds another form of latency to pictures displayed by LCD screens. An LCD screen with high response time and significant input lag will not give satisfactory results when playing fast paced computer games or performing fast high accuracy operations on the screen (e.g. CAD). Manufacturers only state the response time of their displays and do not inform customers of the input lag value.

Jim

---

### Post by mgmiller on 2008-11-23
I also have an nvidia 8600GT and I have no problem with "slicing".
This can be a problem in fast gaming sequences also.
Here is how I fixed it.....

Try going to System > Administration > NVIDIA X Server Settings

If it's not there try entering:
```
nvidia-settings
```
in a terminal.

If it's still not there, install it:
```
sudo apt-get install nvidia-settings
```

Once it's there and you manage to get the gui to run....

First, don't have a heart attack if the screen goes black, it will turn back on in a few seconds.

On the left side, click on the triangle next to "X Screen 0" to open up the choices under it.

Click on "X Server XVideo Settings".

On the right side, under "Video texture Adaptor", click to enable the check box in front of "Sync to VBlank".

Then click "Quit" to exit the gui.

See if the slice is gone

---

### Post by dn* on 2008-11-24
Thanks for your replies. 

I used nvidia-settings to have a look and Sync to Vblank was already turned no. I then turned off compiz and the slicing has gone away which is quite upsetting as I enjoy being able to flip between work spaces by scrolling on the desktop. And wobbly windows is nice :)

Is there a compromise here? Or is it a driver issue? I mean, although the card is not top of the range it is still relatively quite powerful.

---

### Post by mgmiller on 2008-11-24
I wonder if it isn't just some effect that you have turned on that causes the problem.  Try disabling some of the effects in compiz.  Wobbly windows comes to mind, that one seems to use an inordinate amount of gpu power.  There are probably others that can cause the problem, you'll just have to experiment with turning them off one at a time till you find the culprit.

If you haven't already installed it, put in "simple-ccsm"  This will install both the full blown compiz config settings manager as well as an easier to use "simple" gui control panel.  Once installed look in System > Preferences > CompizConfig Settings Manager for the full blown gui and System > Preferences > Simple CompizConfig Settings Manager  for the simpler gui.

```
sudo apt-get install simple-ccsm
```

You will now have very fine control over every aspect of compiz-fusion.  You can easily turn individual effects on and off and tweak their settings to a great degree.

As I mentioned earlier, I have the same video card as you, I am using the 177 driver and I use lots of effects in compiz, but I don't experience the slicing you have noticed.  Then again, I turned off wobbly windows a long time ago as I found it annoying after a few minutes of having it stick windows to various edges.  I do enjoy having "hot corners" where I can turn on the scale effect to quicly pick an open application and I even slowed down the spinning cube effect when I scroll on the desktop to better show off my animated background and 3D windows effects.

So you can have lots of effects , just not all of them.

---

### Post by aeiah on 2008-11-24
> **dn* said:**
> Thanks for your replies. 

I used nvidia-settings to have a look and Sync to Vblank was already turned no. I then turned off compiz and the slicing has gone away which is quite upsetting as I enjoy being able to flip between work spaces by scrolling on the desktop. And wobbly windows is nice :)

Is there a compromise here? Or is it a driver issue? I mean, although the card is not top of the range it is still relatively quite powerful.

is compiz's sync the same as your monitor sync? i think there's a setting along the lines of "automatically detect monitor refresh" or something to do with frames per second. try manually setting it to the same as your monitors. if that doesnt help and niether does turning off some of your plugins, then perhaps you'll have to run your videos without compiz running. it might not be as horrible as you think though. 

the best thing would probably be to use a script that'll replace the window manager like this one
```

metacity --replace 
mplayer $1
compiz --replace

```

this will replace compiz with metacity, launch your media player with your movie and when closed, replace metacity with compiz. not ideal, i know, but as a last resort could be useful.

when you right-click on a video and go to properties, you can select what program to launch your videos with. browse for the shell.sh file you created with the contents i mentioned (or something similar with totem, vlc, xine or whatever you use as your video player)

---

### Post by ajgreeny on 2008-11-24
You can also use Forlong's pre-written script application to turn compiz on, and then off with a single click.  Look [here]("http://forlong.blogage.de/article/pages/Compiz-Switch").  I find it very useful to be able to do this occasionally.

---

### Post by mgmiller on 2008-11-24
> the best thing would probably be to use a script that'll replace the window manager like this one
     Code:
     metacity --replace 
mplayer $1
compiz --replace
This function has been added to the standard menu system for Intrepid, but has not been turned on by default.

Right click Applications and select "Edit Menus"

On the left side navigate to "Other"
On the right side you will find entries for "Compiz" and "Metacity", but the check boxes are not checked.
Put in a check mark...(just being complete)
I have noticed that the compiz entry works just fine as is, but I had to edit the one for metacity.

So, right click the Metacity entry and select Properties and in the command area change it from:
```
metacity
```To:
```
metacity --replace
```Close out of everything and then you will have 2 entries in your menu system.  One for compiz and one for metacity.

I use these all the time before and after gaming and they work great.

---

### Post by dn* on 2008-12-01
Thanks for all the suggestions. 

The "fix" appeared to be in having nVidia Settings and compiz on the same page - Sync to VBlank in one of them didn't work but having it enabled in both does work. Changing to "Solved".

edit: seems I can't change it to solved!

---

### Post by mgmiller on 2008-12-01
Where in ccsm did you find the sync to v blank setting?

---

