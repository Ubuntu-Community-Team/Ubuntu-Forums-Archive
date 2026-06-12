---
title: "DVD Playback Quality"
date: 2007-07-06
forum: Multimedia &amp; Video
---

### Post by rscott5 on 2007-07-06
Hi all,

I have a fresh install of Ubuntu 7.04 with a nice new 20 inch widescreen monitor. When I play a DVD, whether it be in VLC, the default movie player, etc. and I go to fullscreen, the video quality is pretty grainy. I installed all of the necessary codecs and everything for DVD playback (I think, I mean it wouldn't play at all otherwise right?) so I was wondering if anyone else has had a problem like this and might know a fix. I'm running at 1680x1050 resolution if that helps at all.

Also, I noticed that when I go to fullscreen when I'm watching a widescreen DVD, it still shows the black bars at the top and bottom, even if I change the aspect ratio to 16:9. Does anyone know how I can fix that?

Thanks in advance for your help.

---

### Post by david_2001 on 2007-07-06
> **rscott5 said:**
> Also, I noticed that when I go to fullscreen when I'm watching a widescreen DVD, it still shows the black bars at the top and bottom, even if I change the aspect ratio to 16:9. Does anyone know how I can fix that?
The second question I can answer.  An anamorphic widescreen movie will likely have an aspect ratio of 2.35:1 (the ratio will be printed on the back of the dvd case) but the dvd format only allows 16:9, or approximately 1.8:1, so the movie has to be letterboxed to fit properly in the reduced width.  Wikipedia can explain this better than me: [http://en.wikipedia.org/wiki/Anamorphic_widescreen](http://en.wikipedia.org/wiki/Anamorphic_widescreen).

---

### Post by rscott5 on 2007-07-07
Okay so from what you said and what I managed to understand from the Wiki article, even though my DVD's might be true widescreen, the DVD format only supports 16:9 so some letterboxing may still need to be added which is what I am seeing. Does that sound right?

The only part I don't get is that I can watch the movies on my widescreen TV and set the aspect so that there is no letterboxing. The article said that DVD's whose boxes say something like "enhanced for widescreen television" should show the full anamorphic widescreen. Well I tried one of my movies that says that and it still didn't work on the computer. Could you explain this for me?

Also, anyone know what my be going on with my playback quality? Thanks.

---

### Post by mrphantastic on 2007-07-07
First of all, that's really dang high resolution, so you might just have to be set with somewhat icky resolution aka "grainyness" with your dvd's, i mean, i have a 19 inch samsung and a blasted, Nvidia 8800 gts on my setup and MY dvds look unclear at times.  But, the important question is, what codecs exactly did you put on, and how?....

---

### Post by SeattleUser on 2007-07-07
Is your screen resolution set to 1680x1050?  I had to install the 915resolution package to get that resolution on my system.  I have a 22inch wide screen lcd monitor.  DVDs look fine on my system.  I can't say the same for fonts on web pages, though.  I have to increase the font size when I load a page to make it look decent.

---

### Post by david_2001 on 2007-07-07
> **rscott5 said:**
> Okay so from what you said and what I managed to understand from the Wiki article, even though my DVD's might be true widescreen, the DVD format only supports 16:9 so some letterboxing may still need to be added which is what I am seeing. Does that sound right?

The only part I don't get is that I can watch the movies on my widescreen TV and set the aspect so that there is no letterboxing. The article said that DVD's whose boxes say something like "enhanced for widescreen television" should show the full anamorphic widescreen. Well I tried one of my movies that says that and it still didn't work on the computer. Could you explain this for me?

Also, anyone know what my be going on with my playback quality? Thanks.
Chances are that your TV is set to a mode that expands the picture vertically to hide the letterboxing.  The last TV I owned, which was widescreen, had this option.  Some of the left and right hand ends of the picture will be lost in the process in order to maintain the correct aspect ratio.

---

### Post by rscott5 on 2007-07-07
I installed libdvdcss2 and w32codecs for DVD playback becuase that's what the Enabling Multimedia in Feisty sticky said to do here: [http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626) . Are those the codecs I should be using? I started wondering about what you mentioned, that I'm running at such a high resolution that the video output gets stretched too much. Is there some way to fix that maybe? (Aside from turning down my resolution before watching a movie.) I'm planning to run Windows XP Pro virtually, I think through VirtualBox. Would the graphics quality be good enough for me to just watch the movie in the virtual OS?

SeattleUser - Yes I'm running at 1680x1050 because that is the max resolution that my monitor supports. By installing the nVidia drivers for my 6600GT I was immediately able to change Ubuntu's resolution to match that.

---

### Post by SeattleUser on 2007-07-07
My monitor is also a hdtv.  Last nite I tried another test.  FIrst I played a dvd using Ubuntu and then I played the same dvd on a player hooked to the component input to my monitor.  The player did have a little better quality, plus it was full screen with small black bars on the sides.  The dvd box says the aspect ratio is "various" and on the front it says "Full Screen" so I have no idea what ratios it produces.  I would think that various means amorphous.  My standalone dvd player is set to output in 16:9 mode.  I installed the recommended codecs, but I don't recall what they are.  Totem movie player was used in Ubuntu.  The odd thing was that when I played it with Totem it skipped the menu and FBI warning and went straight to the movie.  That was a plus.  When I selected full screen with Totem the bars on the side were a wider than the display from the player.

You don't have any quality issues with fonts in web pages?   Perhaps that is a problem with the linux driver for my intel graphics.

---

### Post by david_2001 on 2007-07-07
> **rscott5 said:**
> I'm planning to run Windows XP Pro virtually, I think through VirtualBox. Would the graphics quality be good enough for me to just watch the movie in the virtual OS?
Maybe or maybe not.  I have XP Pro running in VirtualBox and while it's fine for what I need it for (mostly running Cuttermaran) DVD playback is ruined by an annoying video artifact - difficult to describe but it's like a small tear that runs right the way across the player window.  This is with a nvidia 7100GS card, nvidia-glx-new driver and a 19" 1280x1024 LCD monitor.

---

### Post by david_2001 on 2007-07-07
> **SeattleUser said:**
> Totem movie player was used in Ubuntu.  The odd thing was that when I played it with Totem it skipped the menu and FBI warning and went straight to the movie.  That was a plus.  When I selected full screen with Totem the bars on the side were a wider than the display from the player.
Totem doesn't support DVD menus, which both a good and a bad thing.  Menu support works in kaffeine, xine and gxine and mostly works in vlc, all of which are better DVD players than totem.

---

### Post by Boztech on 2007-07-07
First and foremost a standard def. DVD will be somewhat grainy when played fullscreen at 1680x1050 because standard def. DVD has a resolution much lower than that.

Second, 1680x1050 is 16:10, not 16:9, which is still not exactly what a typical widescreen movie is formatted as, so there will usually be bars.

However the video interlacing quality of DVD playback can be affected by your video hardware and the driver being used.  Make sure you are using the latest stable driver for your video card, and I would suggest giving mplayer or VLC a try to see if the quality is improved over Totem for you.

---

### Post by SeattleUser on 2007-07-07
Kaffeine said:

The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd)

gzine said:
The xine engine failed to start.  No input plugin was found.

vlc did nothing when I selected dvd from from the menu and pushed play.

Totem starts right up and plays.

---

### Post by david_2001 on 2007-07-08
> **SeattleUser said:**
> Kaffeine said:

The source can't be read.
Maybe you don't have enough rights for this, or source doesn't contain data (e.g: no disc in drive). (/dev/dvd)

gzine said:
The xine engine failed to start.  No input plugin was found.

vlc did nothing when I selected dvd from from the menu and pushed play.

Totem starts right up and plays.
In order to read DVDs with kaffeine, xine and gxine install libxine1-ffmpeg (the package formerly known as libxine-extracodecs).  Vlc ought to just work provided that the correct dvd device is selected in the Open Disc dialog.

---

### Post by SeattleUser on 2007-07-08
I check and libxine1-ffmpeg was already installed.  I did notice that libxine1-plugins wasn't installed so I had that one installed along with some dependencies.  Now Kaffeine and xine both work and give me a picture just as good as the one from my standalone player.  There is one slight oddity.  My PC has both DVDRW and DVDrom drives.  Totem can play dvds from either while xine and Kaffeine only work from the DVDrom drive.

Thanks David for the tip.

---

### Post by david_2001 on 2007-07-08
> **SeattleUser said:**
> There is one slight oddity.  My PC has both DVDRW and DVDrom drives.  Totem can play dvds from either while xine and Kaffeine only work from the DVDrom drive.
The xine engine, as used by kaffeine, xine and gxine, only supports one dvd source drive (see attached screenshot).

---

### Post by rscott5 on 2007-07-09
So I installed Windows XP Pro in VirtualBox and the quality is exactly the same (maybe because I'm running it fullscreen at the same resolution, duh?) but I've decided I can just live with the graininess and the letterboxing until I get some money and buy a DVD player to hook up to my monitor as well.

Thanks for all the responses.

---

