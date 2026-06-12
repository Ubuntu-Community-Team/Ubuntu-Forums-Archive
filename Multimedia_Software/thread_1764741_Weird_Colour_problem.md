---
title: "Weird Colour problem"
date: 2011-05-22
forum: Multimedia Software
---

### Post by ajaybhat999 on 2011-05-22
Hi I have a rather strange problem...
I recently installed VLC media Player and have been using it as the default application to view my video files...
The audio files get opened in the Movie Player(the default one)..
But When I open the Video files in Movie Player ,The Colour gets distorted and all videos appear bluish in colour...
Also the same thing happens when I open a video file in VLC after opening on the audio files in movie player (The colour gets distorted and appears bluish)...


Please Help:confused:

---

### Post by Kschikan on 2011-05-22
It sounds like a problem with your red channel (when you have no red, the blue comes through more strongly). Are you only having this problem with VLC, not with YouTube or in games, etc? If it's a system-wide problem, it could be the connection from your graphics card to your monitor.

If it's only a problem with vlc, do you notice any errors in the logs that might be relevant?

---

### Post by Jimlas53 on 2011-05-22
I'm having the same problem.  Playing video via "Fox-TV" add-on for Foxfire.  I can't get the stream going unless I play it in VLC, and the color is way off (think "SMURFS").

-Doug

---

### Post by dnguyen1963 on 2011-05-23
> **ajaybhat999 said:**
> Hi I have a rather strange problem...
I recently installed VLC media Player and have been using it as the default application to view my video files...
The audio files get opened in the Movie Player(the default one)..
But When I open the Video files in Movie Player ,The Colour gets distorted and all videos appear bluish in colour...
Also the same thing happens when I open a video file in VLC after opening on the audio files in movie player (The colour gets distorted and appears bluish)...


Please Help:confused:

Mine is even worse...most of the time the video looks like a negative 35 mm slide.  The only way that I have found to get around this problem is to open the video file with smplayer (which plays the video fines) then re-open with VLC.  I do not know why that fixes the problem.  There appears to be some temporary setting file that VLC uses, which I have no way of tracking down.  BTW, the reason that I do not use smplayer is that sometimes I get no sound.

---

### Post by no2498 on 2011-05-23
this problem use to be fixed in totem by setting the saturation slider to 0
after you see a good picture reset it to default 
hope it still works for you

---

### Post by dnguyen1963 on 2011-05-23
> **no2498 said:**
> this problem use to be fixed in totem by setting the saturation slider to 0
after you see a good picture reset it to default 
hope it still works for you

Nope, tried this approach already.  Thanks anyway.

---

### Post by no2498 on 2011-05-24
look in your package manager for gstreamer
you need the good,bad,ugly and 10 for the ubuntu/linux you use

---

### Post by ajaybhat999 on 2011-05-25
I opened the package manager and searched for gstreamer and saw that it was already installed...
I didn't get the good,bad and ugly part...:confused:

---

### Post by no2498 on 2011-05-25
they call them from the good set,bad set

GStreamer plugins from the "bad" set (Multiverse Variant)

GStreamer plugins from the "good" set

GStreamer plugins from the "ugly" set (Multiverse Variant)


thats just a few of what i have installed

---

### Post by Beauxesprits13 on 2011-06-10
This seems to happen to me every-time i install. opening movie player and going to edit>preferences>display and sliding all the colour balances back to 50:50 or just pressing return to defaults always works for me.

---

