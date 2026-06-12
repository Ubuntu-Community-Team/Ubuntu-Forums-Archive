---
title: "Media player that can display videos frame-by-frame?"
date: 2008-08-09
forum: Multimedia Software
---

### Post by MaxIBoy on 2008-08-09
For secret, one-frame-long hidden messages in various videos. At a minimum it should be able to cope with ogg theora, but as many file formats as possible are great.

---

### Post by easybake on 2008-08-09
mplayer could probably do what you're looking for. If you have it installed. You could just run this:

```
mplayer -fps 1 -nosound  /home/blahblah/Videos/MOV012345.MPG
```


If you don't have it installed:
```
sudo apt-get install mplayer
```

EDIT:You can always read the man pages for more options with it.
```
man mplayer
```

---

### Post by MaxIBoy on 2008-08-09
I didn't know mplayer could do that! Thanks, that's exactly what I needed.

---

### Post by buntu_hugenewbie11 on 2008-09-09
Is it possible to do this with quicktime formats with something else?
Or specifically *.mov

---

### Post by easybake on 2008-09-09
> **buntu_hugenewbie11 said:**
> Is it possible to do this with quicktime formats with something else?
Or specifically *.mov

Of course. just change the end of ```
mplayer -fps 1 -nosound  /home/blahblah/Videos/MOV012345.MPG
``` to ```
mplayer -fps 1 -nosound  /home/blahblah/Videos/MOV012345.MOV
```

---

### Post by buntu_hugenewbie11 on 2008-09-10
ok I see that works now.
But my next question is how do I get a gui for mplayer?
I even have it in my kde menu but nothing happens when I load it.
The thing is I only want to see frame by frame footage for a section 8 or 9 mins in a video.
Is there an easy way to do video editing in linux on a frame by frame basis.
I looked at the wiki for mplayer and well I really hope there is a gui.

---

### Post by eye208 on 2008-09-10
> **buntu_hugenewbie11 said:**
> The thing is I only want to see frame by frame footage for a section 8 or 9 mins in a video.
Skip to the part that you want to watch frame-by-frame, hit the space bar to pause playback, then hit the "." (dot) key to advance frame by frame.

By the way, you can find all of this in MPlayer's manual.

---

### Post by shirilover on 2008-09-10
> **buntu_hugenewbie11 said:**
> ok I see that works now.
But my next question is how do I get a gui for mplayer?


You need to download a skin from here -> [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Extract the contents to ~/.mplayer/skins and then rename the folder to default.

Then run it using gmplayer.

---

### Post by Ultra Cronic on 2011-11-28
> **buntu_hugenewbie11 said:**
> ok I see that works now.
But my next question is how do I get a gui for mplayer?
I even have it in my kde menu but nothing happens when I load it.
The thing is I only want to see frame by frame footage for a section 8 or 9 mins in a video.
Is there an easy way to do video editing in linux on a frame by frame basis.
I looked at the wiki for mplayer and well I really hope there is a gui.
:popcorn::shock:
As useful as mencoder/mplayer are the command line stuff can get on your nerves. I go over paranormal investigation files , but before I put them into a heavy duty program, I give them a quicker look using AVIDEMUX for ubuntu.
It's a cut and splice linear editor with built in codecs [no dependencies needed]. But once you click on the pause button you can advance the video one frame at a time with the space bar, or use the arrow keys to frame forward or fast forward [hold arrow key], or fast and single frame reverse
[hold the arrow key and it will fly through the frames] until you see a "Blip" in the picture now let go, hopefully your looking for an all white background with black text, that would be easy to catch with this program, plus it wont break any other video software on your system because it's pretty much a stand alone program. Then it will export that frame as a .bmp when you find it.
Google it or apt-get it you may have to add Mediabuntu to your repository trust list first.
AVIDemux for ubuntu.

---

