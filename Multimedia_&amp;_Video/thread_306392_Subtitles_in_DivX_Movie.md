---
title: "Subtitles in DivX Movie"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by MoonBlossom on 2006-11-24
Hello,

I'm new to Linux. I've been using it for about 2 months and even though it was a little hard to understand the commands in the beginning I'm actually loving it :D 

I have a movie made with divx, I can watch it using mplayer, kaffeine or vlc but none of these programs can play the subtitles that came with this movie. I don't know if I'm missing a library or something.

Help with this will be much appreciated.

---

### Post by PurplePenguin on 2006-12-11
It's been 2 weeks since your post... did you find an answer yet?

MPlayer and VLC should have no problem playing external subtitles.  Which format are the subtitles in?  

If you are interested in hard subs (ie. subs that are permanently written onto the movie), Avidemux is great.

---

### Post by MoonBlossom on 2006-12-12
> **PurplePenguin said:**
> It's been 2 weeks since your post... did you find an answer yet?

MPlayer and VLC should have no problem playing external subtitles.  Which format are the subtitles in?  

If you are interested in hard subs (ie. subs that are permanently written onto the movie), Avidemux is great.

Thank you for replying. Unfortunately I haven't find an answer yet. 

I googled Avidemux but it seems to be a video editing tool rather than a player.

---

### Post by dorcssa on 2006-12-12
But you didn't tell what format do you use for the sub. Also, the subtitle's name should be exactly the same as the movie's.

---

### Post by MoonBlossom on 2006-12-12
The sub is inside the file, I guess it is a hard sub like PurplePenguin said.

---

### Post by PurplePenguin on 2006-12-12
If it's a hard sub, any video player will work - you cannot watch the movie without seeing the subtitle if it's hard-subbed.  So Totem, VLC, MPlayer, Xine - you name it - will all play hard-subbed films and you'll see the subtitles.  If you don't see subs, it'll need an external subtitle file.

To load external subtitles in VLC, just click Open File, browse for the film you want, click the checkbox for Subtitles, then browse for the external subtitle file.

MPlayer is a bit different (going from memory)... you need to open up whichever film you want, then as it's beginning, right click the Mplayer window again to bring up the menu.  I think it's Open then Subtitle File (or something to that effect).  It will reload the film from the beginning with the subtitles.

---

### Post by MoonBlossom on 2006-12-12
None of those players are able to display the subtitles. VLC is the only one that recognizes the subtitles in this particular file. Although if I select to view the subtitles I still can't see them and the movie will play as if I didn't select to view subtitles.

Maybe it has to do with the DivX codec.

---

### Post by PurplePenguin on 2006-12-12
If the sub "is inside the file" with the movie as you say, it means that you cannot watch the movie without seeing the subtitles.  As far as I know, if you can see the movie but not the subtitles, it means that there are *no* subtitles in the file.  In other words, everything is working fine. :)

That's the only way it is with divx... you'll need to download separate subtitle files (.sub, .srt, etc) to see subtitles.  I may be wrong, but I've never seen a way to put subtitles inside a divx file and choose whether or not to see them - it's either burned right into the movie itself or not.

---

### Post by MoonBlossom on 2006-12-12
Maybe my problem has to do with the codec. In Windows I was able to choose if I wanted to see subtitles or not using the DivX player.  

I hope the guys that make DivX start to support Linux again, because for what I saw in their website they only support Mac and Windows :-|

---

### Post by tauko on 2006-12-12
In VLC, when playing the video: right click on the vlc screen -> subtitle track -> track 1. If there are more, just try.

Hope it helps!

---

### Post by MoonBlossom on 2006-12-13
In VLC I only have video track option. It shows that the file has subtitles but if choose them nothing happens. It could even be the file that is wrong, I don't know. 

Thank you anyways :D

---

### Post by barrack on 2007-01-22
i also have a divx movie with a .sub file named the same as the main .avi file. both are in the same folder. i tried adding the .sub file manually as described above, but it fails to load. this happens in both vlc and in mplayer.

is there another step that i'm missing? do i need other files? or better yet, is there another program that i can use that "hard sub" the movie so that i don't need to do this all the time?

thanks!

---

### Post by herpes on 2007-01-22
> **barrack said:**
> i also have a divx movie with a .sub file named the same as the main .avi file. both are in the same folder. i tried adding the .sub file manually as described above, but it fails to load. this happens in both vlc and in mplayer.
I might be wrong, but I'm sure that .sub (microdvd) files need the corresponding .idx (index) file to work, normally it's the .idx file that is loaded manually rather than the .sub. Try googling for the missing .idx file (if it is missing), or for a different set of subtitles.

---

### Post by gerrymoth on 2007-05-09
Just in case anyone is reading this thread I found a good source for subtitle files [http://www.opensubtitles.org/en](http://www.opensubtitles.org/en)

I've been using VLC and Open File with film and separate subtitle file successfully for most films.

---

### Post by DevilBee on 2007-07-01
If the subtitles are in any other language than English you will need to chose the right encoding for the fonts.
In VLC the Menu in under advanced settings on the same window where you open the subs. 

To load subs in totem you need to put both the video file and the subs file in the same folder and both files must have the same name (apart, of course, for the file extension). 
After doing that, play the video file (totem will not recognize the subs on the load screen only after the movie is playing will you be able to activate the subs through the view menu.
To change the encoding the totem, go to preferences under the edit menu.
Usually Unicode UTF-8 would work but occasionally it doesnt and you need to go through the languages and find the correct one.

---

### Post by robertlankford on 2007-12-24
I just switched to Ubuntu from Windows and ran into this same situation myself.  Divx has a 'container' that embeds multiple subtitle tracks, multiple audio tracks, menus, and other potential things maybe.  The extensions are "avi" or "divx".  This is *not* the standard avi container, but an adapted one developed by Divx so that allows you to mimic the functionality of a DVD in a single Divx file.  In order for all this to work on Windows, you must use the Divx video player.  If you use something else (windows media player, perhaps), then you have to tell the codec that is rendering the video directly which subtitle or what-not that you'd like to use.  You can usually right-click the Divx icon in the lower right of the screen to access this additional container functionality.

I don't guess that the Divx decoders for Ubuntu understand this level of sophistication yet.  Or at the very least, the video players don't support Sub-title selection in their GUIs.

I know that this post doesn't really help anyone get any closer, but maybe it'll get everyone on the same page, at least, when discussing the issue.  The sub-titles aren't 'hard coded' into the video stream itself. And they aren't located in a separate file either. They are included directly in the avi/divx container and are meant to be rendered in real-time as the video is played.

---

### Post by vlaklak on 2007-12-24
The best one is Smplayer!   It is for the subtitles.

---

