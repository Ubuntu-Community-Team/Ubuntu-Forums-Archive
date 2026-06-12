---
title: "take pictures of a video"
date: 2012-04-29
forum: Multimedia Software
---

### Post by vivek40 on 2012-04-29
Hi,
I have a few videos of my 3 month old baby... When i went through the videos I felt there were quite a few moments which just might turn out to be very cute pics ... Is there any way I can take those particular shots from the video... 
<Am using 11.10 ubuntu..if that matters>
Thanks
Vivek

---

### Post by newbie-user on 2012-04-29
Congrats on the new baby! They're so much fun.

Anyway, back to your question. You could pause the video, then take a screenshot using the print screen button. You could also use the Screenshot program in Ubuntu to do the same thing and crop out extra stuff at the same time. Some video editors allow you to take a picture of a particular frame, but I'm not sure which editors allow this.

---

### Post by andrew.46 on 2012-04-29
Have a look at Tip no. 5 in this long-neglected guide:

Top 10 Tricks and Tips for the svn MPlayer
[http://ubuntuforums.org/showthread.php?t=1154431](http://ubuntuforums.org/showthread.php?t=1154431)

And congrats on the new baby :).

---

### Post by SeijiSensei on 2012-04-29
I use a couple of different methods to capture frames from a video depending on my needs.

1) Install smplayer.  To capture a single frame, hit  S; to capture a sequence use Shift-D to start and another Shift-D to stop.  The frames will be written as numbered PNG files to $HOME/.config/smplayer/screenshots.  

If you have a recent NVIDIA card (8xxx or later) and the proprietary driver, smplayer may default to using "vdpau" for output.  You can't grab frames with this driver, so go to Options > Preferences > General > Video and select the "xv" driver from the drop-down box at the top.

2) Use mplayer from the command line with the JPEG output filter and -ss and -endpos options to select a segment of the video by timestamp like this:

```
mplayer /path/to/videofile -ss hh:mm:ss -endpos N -ao null -vo jpeg
```

This will begin grabbing frames starting around hh:mm:ss and continuing for N seconds thereafter.  The files will be written as numbered JPEG images into the current directory. (It may not start exactly at ss seconds because of video compression.  Files encoded with MPEG2 or MPEG4 algorithms capture full frames periodically and then include only the frame-to-frame differences until the next anchor frame is captured.  mplayer will select the nearest anchor and start displaying the frames from that point.)

Welcome to the world of parenthood!  Enjoy the ride!  Oh, and try and get some sleep.

---

### Post by shantiq on 2012-04-29
Vivek best tool i know for this is VLC

[ATTACH]216813[/ATTACH]


set your folder    then a hotkey

and you can do this from afar if you have a wireless keyboard;   watch your video /pause or do it on the fly/   and click hotkey


Then all your pix will stack in your folder

---

### Post by evilsoup on 2012-04-29
Assuming you are using the default Totem movie player, just press 'ctrl+s'.

---

### Post by vivek40 on 2012-05-02
Thanks everyone...  SeijiSensei's reply worked perfectly for me....
<used mplayer>

__

---

### Post by The Rnegade on 2012-05-02
> **vivek40 said:**
> Hi,
I have a few videos of my 3 month old baby... When i went through the videos I felt there were quite a few moments which just might turn out to be very cute pics ... Is there any way I can take those particular shots from the video... 
<Am using 11.10 ubuntu..if that matters>
Thanks
Vivek

the easiest solution is to pause the video at the parts you want to take pictures of and then press the screenshot button, which will take a picture of that frame

the f12 button should take screenshots

---

