---
title: "Cant play .WMV"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by metafour on 2007-03-04
This seems to be a recurring problem among user, and I cant seem to fix it.  I've read several threads on this topic and followed the advice: installed the packages from the Restricted Formats page, installed Automatix and installed the codecs+w32codecs that they provide, and its STILL not working.  The only other video format I've tried are MPG's and they work fine with VLC.  With VLC I'm able to load the WMV file but after that it just does nothing (I get to see a still image of the opening frame).  MPlayer doesn't seem to be able to play any of my video files (not even MPGs) as it keeps spitting out the "Error Opening/Initializing the selected video_out (-vo) device" message whenever I try to load ANY video file.  With gxine I can play my MPG files but once again cant play WMV files (this time I just get a black screen, I can see the time on the bottom progressing but nothing is playing).  Totem allows me to load up the WMV files but once again doesn't play, I can scroll to parts of the video and get a still image of the screen, but theres absolutely no motion to the video.

Hopefully I've provided enough because this is really starting to irritate me, I cant see what else to do.  It doesn't seem like a video-player problem because none of the players I've tried have been able to play the WMV files, but at the same time I'm pretty sure I've installed all the codecs I'm supposed to install.

---

### Post by freeflyer57 on 2007-03-04
Do your multimedia players point to the codec's proper place? I have my win32 codecs in 
/usr/lib/win32.

---

### Post by metafour on 2007-03-04
My win32 codecs are in the same location.  How can I check where my multemedia players are looking for codecs?  I dont see anything in VLC that lets me do anything like that...

---

### Post by freeflyer57 on 2007-03-04
for WMV, VLC should look for /usr/lib/Win32/wmv9dmod.dll

You can find this at settings->preferences->video codecs->fake->image file

---

### Post by freeflyer57 on 2007-03-04
preferences->input/codecs->video codecs->fake->image file

sorry for that!

---

### Post by freeflyer57 on 2007-03-04
Xine:control->decoder->path to Win32 codecs

under gui tabset configuration experiece level to master of the known universe

gXine:same as Xine

---

### Post by metafour on 2007-03-04
It wasn't pointed to anything but I pointed it to the file that you specified, still not working though.

---

### Post by metafour on 2007-03-04
With gXine do I need to point it to the PATH (folder) or the actual file (like with VLC)?

---

### Post by freeflyer57 on 2007-03-04
gXine only the path /usr/lib/Win32

---

### Post by freeflyer57 on 2007-03-04
are you sure you have the latest WMV9 codecs?

---

### Post by metafour on 2007-03-04
Pointed VLC to the file ---> still not working.
Pointed gXine to the folder the codecs were located in ---> not working but wondering if I'm supposed to point it to the specific file like with VLC.

---

### Post by metafour on 2007-03-04
> **freeflyer57 said:**
> are you sure you have the latest WMV9 codecs?

Havn't checked, but I JUST installed Automatix today so I'm assuming the Win32Codecs I installed were of the latest version.

---

### Post by freeflyer57 on 2007-03-04
try this [http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs)

---

### Post by freeflyer57 on 2007-03-04
look in /usr/lib/Win32 and tell whether or not there is wmv9dmod.dll.

If you find this file then they are up to date.

---

### Post by freeflyer57 on 2007-03-04
Tell me exactly what it is that you are trying to watch. Maybe we can attack the source that way.

---

### Post by metafour on 2007-03-04
> **freeflyer57 said:**
> try this [http://www.mplayerhq.hu/design7/dload.html#binary_codecs](http://www.mplayerhq.hu/design7/dload.html#binary_codecs)

Where do I extract these codecs, and are they only for MPlayer?

---

### Post by freeflyer57 on 2007-03-04
Check to make sure you don't already have them.

If you don't extract them into /usr/lib/Win32

They are codecs. They will work with all media players.

---

### Post by metafour on 2007-03-04
> **freeflyer57 said:**
> look in /usr/lib/Win32 and tell whether or not there is wmv9dmod.dll.

If you find this file then they are up to date.

Yup, its there.

---

### Post by freeflyer57 on 2007-03-04
wow! okay, what is it that you are trying to watch?

---

### Post by freeflyer57 on 2007-03-05
go ahead and replace the codecs with what you just downloaded.

This could go a lot faster by using yahoo instant messenger.

---

### Post by Lonthong on 2007-03-05
I know for sure that Totem-xine cannot play wmv9 files (other wmv files are playable) so probably gxine can't play them as well.
I probably can help you with Mplayer as I also faced that same problem right after installing mplayer  ("Error Opening/Initializing the selected video_out (-vo) device" message). 
You should change yr video output device
Issue the following command to get a list of available video output drivers:
mplayer -vo help
select a video driver (for me was a trial and error) and add it to your configuration file:
vo = selected_vo to ~/.mplayer/config     and/or
vo_driver = selected_vo to ~/.mplayer/gui.conf.

Hope this solution will work for you.

---

### Post by freeflyer57 on 2007-03-05
I watch TV everynight on my computer. The stream requires WMV9 and WMA 2, which work flawlessly with gXine, when the codec path is set to /usr/lib/Win32. It's getting late. If you still have this problem tomorrow, I will get back on to check with you. sorry for not helping much, we should use yahoo instant messenger(it would be much quicker to communicate).

---

### Post by metafour on 2007-03-05
Cant replace the codecs - says I dont have permission.

---

### Post by Lonthong on 2007-03-05
> **freeflyer57 said:**
> I watch TV everynight on my computer. The stream requires WMV9 and WMA 2, which work flawlessly with gXine, when the codec path is set to /usr/lib/Win32. It's getting late. If you still have this problem tomorrow, I will get back on to check with you. sorry for not helping much, we should use yahoo instant messenger(it would be much quicker to communicate).

I am on Edgy 64bit if that makes any difference at all.

---

### Post by Erlander on 2007-03-05
I have the same problem.

I watch TV (DVB-T) on my Edgy pc but can't view the video on this BBC site or any similar WMV files using Firefox:

 [http://news.bbc.co.uk/2/hi/south_asia/6418459.stm](http://news.bbc.co.uk/2/hi/south_asia/6418459.stm)

I have the Totem-Mozilla Plug-in installed.

Rob

---

### Post by freeflyer57 on 2007-03-05
Use this to copy with permission

```
sudo cp "codecs file" /usr/lib/Win32
```

---

### Post by sdowney717 on 2007-03-05
[http://news.bbc.co.uk/2/hi/south_asia/6196716.stm](http://news.bbc.co.uk/2/hi/south_asia/6196716.stm)

I can play with mplayer this video.
I never bothered to try with totem plugin. Just uninstall it and go with mplayer. Put in the restricted win32 codecs.

---

### Post by sdowney717 on 2007-03-05
you also have to add this to play mms streaming video from cc.com

---

### Post by erwinquita on 2007-03-05
Here's a screencast on installing codecs for common *nix video players

[[COLOR="DarkRed"]http://www.ibatayo.com/rails/categories/5/posts/15[/COLOR]]("http://www.ibatayo.com/rails/categories/5/posts/15")

You can also try [[COLOR="DarkRed"]xine[/COLOR]]("http://www.ibatayo.com/rails/categories/5/posts/13") video player.

Hope this helps

---

### Post by Erlander on 2007-03-06
Thank you everyone.

I will give your suggestions a try and report back later.

In the meantime I'm struggling with xorg.conf having changed my graphics card today from a TNT2 to a GeForce 7600GS.

Thank you.

Rob

---

### Post by panch0 on 2007-03-07
One important thing is that the win32 directory name must be **lower case**, we are on Linux remember? :) File and directory names are case sensitive.

I second the suggestion to use MPlayer, it's the best for streaming media, especially with KPlayer as the frontend.

---

### Post by DishBreak on 2007-07-01
I'm sure this is stretching the bounds of credulity, but i've tried nearly all these solutions and i still have no results. I set the player (i won't get into how many i've tried) to point to the drivers, and it still doesn't work for me. The program up and quits, without any errors, so i don't know what happened. :evil:

Help please?

---

