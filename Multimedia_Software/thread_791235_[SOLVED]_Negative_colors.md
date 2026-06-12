---
title: "[SOLVED] Negative colors"
date: 2008-05-12
forum: Multimedia Software
---

### Post by DeMus on 2008-05-12
Hi,
I noticed while playing a .rm file, later also with .avi, that the colors are negative: red becomes green, etc.
How can I change this? Do I need another codec, or another nVidia driver for my 8500GT card? If it is the driver could somebody please explain in simple terms how to install the driver since the explanation in the README file on the nVidia driver is way too complicated. I have no idea what to do and how to do it. I am relatively new to Linux and this is way out of my league.

Thanks for your help,
DeMus

---

### Post by peitschie on 2008-05-12
Check this thread out: [http://www.nvnews.net/vbulletin/showthread.php?t=107009&highlight=totem](http://www.nvnews.net/vbulletin/showthread.php?t=107009&highlight=totem)

The crux of it is you can test for this bug using the following:
```
xvinfo | grep -A2 XV_HUE
```

The XV_HUE should be 0... but for some reason it gets set to 178 when opening a movie in Totem using the GStreamer backend.

You can fix it using the following (temporary!) fix.  This will need to be run after every boot, so you might want to set it to run automatically when you login possibly...
```
xvattr -a XV_HUE -v 0
```
NOTE: you'll need to install xvattr for this to work:
```
sudo apt-get install xvattr
```

---

### Post by DeMus on 2008-05-12
> **peitschie said:**
> Check this thread out: [http://www.nvnews.net/vbulletin/showthread.php?t=107009&highlight=totem](http://www.nvnews.net/vbulletin/showthread.php?t=107009&highlight=totem)

The crux of it is you can test for this bug using the following:
```
xvinfo | grep -A2 XV_HUE
```

The XV_HUE should be 0... but for some reason it gets set to 178 when opening a movie in Totem using the GStreamer backend.

You can fix it using the following (temporary!) fix.  This will need to be run after every boot, so you might want to set it to run automatically when you login possibly...
```
xvattr -a XV_HUE -v 0
```
NOTE: you'll need to install xvattr for this to work:
```
sudo apt-get install xvattr
```

Thanks, it works great. Now the colors are normal again. Just one more question: how to set the code so it will start every time I boot?
Thanks so much for your help. Realy appreciate it.

---

### Post by peitschie on 2008-05-12
Hrmm.

I've been playing with this myself (I have an identical issue to you) and it seems that you need to run it before you play any video or change brightness settings etc. so it is quite annoying.  I'm still trying 2 figure out a good way of automating it or making it more permanent.

Sorry I still don't have a total solution yet, so for now I would recommend you put a launcher on your gnome panel that you can click if the colour goes funny ;)  It's what I have and it isn't too annoying juuuust yet.

---

### Post by DeMus on 2008-05-12
> **peitschie said:**
> Hrmm.

I've been playing with this myself (I have an identical issue to you) and it seems that you need to run it before you play any video or change brightness settings etc. so it is quite annoying.  I'm still trying 2 figure out a good way of automating it or making it more permanent.

Sorry I still don't have a total solution yet, so for now I would recommend you put a launcher on your gnome panel that you can click if the colour goes funny ;)  It's what I have and it isn't too annoying juuuust yet.

Thanks again for your answer. I placed it on my desktop and can start it when I need to. At least the colors in the videos are perfect now.

DeMus

---

### Post by peitschie on 2008-06-09
Hey!

Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video :)

To implement the workaround, do the following:

[LIST=1]
[*]Open gstreamer-properties (alt+f2, enter gstreamer-properties)
[*]Change to the video tab
[*]Change the default output plugin to "custom"
[*]Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
[*]Close the box and enjoy your now correct colour :D
[/LIST]

---

### Post by zorba_the_greek on 2008-10-24
> **peitschie said:**
> Hey!

Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video :)

To implement the workaround, do the following:

[LIST=1]
[*]Open gstreamer-properties (alt+f2, enter gstreamer-properties)
[*]Change to the video tab
[*]Change the default output plugin to "custom"
[*]Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
[*]Close the box and enjoy your now correct colour :D
[/LIST]

You saved my butt!!
Unfortunatelly, I have the same problem for Kaffeine and VLC, too..
Any solution..? :(:(

---

### Post by ecekarthic on 2009-11-12
In VLC player, go to Tools -> preferences and select VIDEO. In the Video settings, look for "Output". Change it to something like "OpenGL video output" and click on save. Restart VLC player. It works like a charm. If it doesn't work, try changing the Output to other options available in the drop down.

I'm using 9.10 and it worked perfectly for me.

Thanks,
Karthic

---

### Post by sparker1 on 2010-01-30
The above two posters are wonderful, wonderful people.

---

### Post by SoFl W on 2010-01-30
Thanks, this problem would come and go on my machine and didn't know what caused it.

---

### Post by JNik on 2010-04-10
> **peitschie said:**
> Hey!

Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video :)

To implement the workaround, do the following:

[LIST=1]
[*]Open gstreamer-properties (alt+f2, enter gstreamer-properties)
[*]Change to the video tab
[*]Change the default output plugin to "custom"
[*]Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
[*]Close the box and enjoy your now correct colour :D
[/LIST]

Thanks :D

That worked like a charm

---

### Post by gemmakaru on 2010-04-10
I had this exact same problem but found a hue slider in one of the video players.  Setting this set the colours correct in all the video players and the setting must have saved it's self.

---

### Post by papermonkey11 on 2010-06-05
I recently installed 10.04 and came across the same problem. I really didn't look too much into what caused it...

Just wanted to let everyone know

> Originally Posted by peitschie  
Hey!

Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video 

To implement the workaround, do the following:
Open gstreamer-properties (alt+f2, enter gstreamer-properties)
Change to the video tab
Change the default output plugin to "custom"
Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
Close the box and enjoy your now correct colour 

and

> Originally Posted by ecekarthic

In VLC player, go to Tools -> preferences and select VIDEO. In the Video settings, look for "Output". Change it to something like "OpenGL video output" and click on save. Restart VLC player. It works like a charm. If it doesn't work, try changing the Output to other options available in the drop down.


both worked great. Ubuntu forums saved me... Again... :-D

---

### Post by kianPopcorn on 2010-10-21
> **peitschie said:**
> Hey!

Just letting you know I have discovered another work-around that doesn't require you to manually set the hue every time you open a video :)

To implement the workaround, do the following:

[LIST=1]
[*]Open gstreamer-properties (alt+f2, enter gstreamer-properties)
[*]Change to the video tab
[*]Change the default output plugin to "custom"
[*]Place the following command in the bottom box: videobalance hue=-1 ! autovideosink
[*]Close the box and enjoy your now correct colour :D
[/LIST]



> **ecekarthic said:**
> In VLC player, go to Tools -> preferences and select VIDEO. In the Video settings, look for "Output". Change it to something like "OpenGL video output" and click on save. Restart VLC player. It works like a charm. If it doesn't work, try changing the Output to other options available in the drop down.

I'm using 9.10 and it worked perfectly for me.

Thanks,
Karthic

awesome, it stopped my annoying problem...thanks  !

---

