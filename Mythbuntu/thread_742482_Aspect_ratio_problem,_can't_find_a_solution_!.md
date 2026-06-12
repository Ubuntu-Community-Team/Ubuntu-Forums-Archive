---
title: "Aspect ratio problem, can't find a solution !"
date: 2008-04-01
forum: Mythbuntu
---

### Post by sierramike on 2008-04-01
Hi !

I definitly searched around and didn't find the solution.

I've managed to get Mythbuntu working, installing envy to get the latest NVidia drivers, and now output in 1920x1080i works great on my 42" Full HD LCD Panel.

But, there's a problem. When watching a 4/3 video (let's say DivX), I can do what I want using the "W" key on the keyboard. But when watching a 16/9 video (res of 624x352 which is real 16/9), the system adds black lines on top and bottom as if it believes this is a 4/3 display, and "W" and "E" keys acts on a zoom, but can't toggle displays ...

Why the hell do MythTV believe 1920x1080 is 4/3 display and act like this ???

Please help I'm lost ! Thanks so much by advance !

---

### Post by foxbuntu on 2008-04-01
Did you make sure to set the frontend aspect ratio? (Util/Settings > Setup > Apperence) Should be the 2nd or third page if I recall.

---

### Post by sierramike on 2008-04-02
Yes, it was, now I tryed going back to 4/3, same effect, returning to 16/9, same effect ... I tried also putting Xinerama from "0" to "All", I tried using a "Wide" theme for MythTV, always getting the same behaviour ...

Would there be a bug ???

Note : I'm using MythBuntu 7.10 installed on hard drive.

---

### Post by sierramike on 2008-04-02
aïe aïe aïe finally got it working, but what a workaround !

Got to get to the settings/video/player and add to the mplayer command line the switch "-monitoraspect 16:9" and now it works !

But cannot test the playing of DVD nor watching live TV as my test PC doesn't have any DVD player nor video capture card ...

BUT, I can't think MythTV developpers left such a bug, so I still wonder if there wouldn't be any other setting to do that automatically ...

Note : I have added a "DisplaySize" in my xorg.conf ...

---

### Post by sierramike on 2008-04-03
Ok I'm a bit forward now ...

In fact, I saw the internal player used for playing DVD and VOB files works ok, using the "W" key to switch between zoom modes, and also is outputting audio on the SPDif output (would it be LPCM, DD 2.0 or DD5.1 stream).

But, mplayer has a lot of problems. I've put -monitoraspect 16:9 in the command line for the 16/9 movies to display correctly. But now 4/3 movies are played with black bars left and right, and zoom (using W and E keys) does nothing. So, when playing a 4/3 movie that includes bars on top and bottom, mplayer adds bars on left and right and I have a little picture in center of my TV set, which is really sad.

Also, if I put "-ao alsa:device=spdif" in the command line, it streams digital audio to the SPDif output, but it is downsized to PCM 2ch even if the source is DD 5.1. I have to put "-ac hwac3" in the command line to have AC3 (DD 5.1) being output on the SPDif. BUT, then, if there is no AC3 in the original sound, I have no output at all ...

I don't think I will be changing command line in the MythTV setup each time I want to watch a movie, depending of the sound format and the picture aspect ratio ...

MPlayer seems to be really bugged ... Do someone have another solution more reliable than mplayer for use with MythTV (in fact, MythVideo !)

Thanks a lot !

---

### Post by laga on 2008-04-04
> **sierramike said:**
> 
Also, if I put "-ao alsa:device=spdif" in the command line, it streams digital audio to the SPDif output, but it is downsized to PCM 2ch even if the source is DD 5.1. I have to put "-ac hwac3" in the command line to have AC3 (DD 5.1) being output on the SPDif. BUT, then, if there is no AC3 in the original sound, I have no output at all ...

MPlayer seems to be really bugged 


You need to configure it correctly! Here's what 'man mplayer' says:

> 
DECODING/FILTERING OPTIONS
       -ac <[-|+]codec1,[-|+]codec2,...[,]>
              Specify a priority list of audio codecs to be used, according to their codec name in codecs.conf.  Use a
              ’-’  before  the  codec  name to omit it.  Use a ’+’ before the codec name to force it, this will likely
              crash! ** If the list has a trailing ’,’ MPlayer will fall back on codecs not contained in the list.**
              NOTE: See -ac help for a full list of available codecs.

              EXAMPLE:
                 -ac mp3acm
                      Force the l3codeca.acm MP3 codec.
                 -ac mad,
                      Try libmad first, then fall back on others.
                 -ac hwac3,a52,
                      Try hardware AC-3 passthrough, software AC-3, then others.
                 -ac hwdts,
                      Try hardware DTS passthrough, then fall back on others.
                 -ac -ffmp3,
                      Skip FFmpeg’s MP3 decoder.



Emphasis added by me.

I'm also sure there's a solution for your aspect ratio "problem", you just need to dig a little bit. It's not easy to get get a full-screen picture while retaining the correct aspect ratio without loosing too much picture quality.

---

### Post by sierramike on 2008-04-06
Thanks so much for your help !

Now I have my audio part working good, using "-ac hwdts,hwac3," argument, that's great !

But, I've read lots of manpages lines, lots of webpages, about the 16/9 monitoraspect, but I've not found the good solution.

In fact, I've put the "-monitoraspect 16:9" argument to the command line. So Wide videos are playing fullscreen on the widescreen TV, and 4/3 movies have black borders let and right, which is good.

But when I have a video encoded in 4/3, having black lines on top and bottom of the screen, mplayer adds black borders on left and right. I would like to use the zoom range (using W and E keys) to zoom in, and get the 4/3 picture going to 16/9 fullscreen (cropping top and bottom), as the internal myth player can do with DVD's, but I can't get it work.

When I press W and E keys, I see the range progress bar changing on the picture, but nothing happens !!!

Do you guys know something about this and a workaround to get it working ?

Thanks !

---

### Post by msebast on 2008-04-07
I agree that the mplayer command line interface leaves a lot to be desired. (Actually the problem is that it does everything you could possibly want but won't help you figure out how to do it.) And the man page is HUGE. 

Once you figure out useful command line options that you want to enable all the time (such as -vo, -fs, -zoom or -monitoraspect) make the setting permanent in /etc/mplayer/mplayer.conf

mplayer DOES have a graphical interface. Just run gmplayer instead of mplayer. If you change the command lines in mythtv to run gmplayer then you will be able to right click on the running video and get a nice popup menu. The downside (if I remember correctly?) is that gmplayer keeps running after the video is stopped, and it makes it look like mythtv is locked up. You need a keyboard to hit alt-tab to get to gmplayer and then alt-f4 to close it and get back to mythtv. So I went back to plain mplayer when I got a remote.

---

