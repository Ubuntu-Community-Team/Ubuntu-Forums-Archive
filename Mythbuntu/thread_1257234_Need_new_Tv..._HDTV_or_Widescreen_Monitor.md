---
title: "Need new Tv... HDTV or Widescreen Monitor?"
date: 2009-09-03
forum: Mythbuntu
---

### Post by elklabone on 2009-09-03
We have a Mythbuntu box I built over a year ago... we have CATV and could receive a few HDTV stations IF we had a HDTV tuner card in our MythTV box...

Here's my question.

Our old 26" TV gave out, so I'm thinking about adding a HD tuner card to our MythTV and either buying a HDTV or just buying a widescreen computer monitor instead.

Sine we're going to be using our MythTV box for TV would it save us some money to get a widescreen monitor instead of buying a HDTV? 

We're on a tight budget, so what would be a good size to replace a 26" TV? This is probably a dumb question, but since the widescreen is a different aspect ratio than the TV, do you compare 26" to 26" or do you need to get something larger to get the same size picture?

:confused:

---

### Post by SiHa on 2009-09-03
I can't comment on whether a monitor would be as good as a TV, but there's a reason they're cheaper...;)
It depends on the quality of the monitor, of course, but I've heard that the colour control isn't as tight, and the contrast ratio nowhere as good on a monitor. To be honest, I'd be surprised if you could get a monitor big enough though.

Anyway. The screen size is measured on the diagonal, so to answer your second point, to get the same height picture on a widescreen as on your 4:3 26" telly, you would need a diagonal measurement of 31.8", so 32" would seem to fit the bill.

However, CRT screen sizes are measured across the maximum dimensions of the tube, which is 1-2" bigger than the viewable area, so the 26" tube probably has about 24.5" viewable. LCD screens are measured across the viewable screen, so 32" is 32".

Best bet is to measure the height of your screen and go down to the local TV shop with a tape measure.
If it helps, we replaced our dead 28" 4:3 CRT last year with a 32" LCD, and first impressions were that it was huge!

---

### Post by Caysho on 2009-09-03
I did the same about six months ago, from a 32" CRT (widescreen PAL) to a 37" LCD HDTV.

Be sure to get one that does [1:1 pixel mapping]("http://en.wikipedia.org/wiki/Pixel_mapping"), otherwise the picture will be distorted.  There is a pixel mapping wiki worth checking out.

I know both LG and Samsung handle it - both brands have a Just Scan picture size option.  I have mythbuntu using 1080p out of the box on my Samsung.

---

### Post by joshoekstra on 2009-09-04
Also be sure it has HDMI 1.3b or later, Samsung has left a lot out of it's TV's and with HDCP obliged by a lot of players you want to avoid the trouble it causes.
I'm really happy with my 40W5500 and as far as I can tell the 32 version does 1080p as well and are pretty cheap.

---

### Post by mitchell2345 on 2009-09-05
I wouldn't go monitor.  Live TV in Myth is sub par and sometimes its just faster to use the tv tuner for the occasions when time shifting isn't required (ie sports)

Mitchell

---

### Post by itlarson on 2009-09-05
Although I agree you should get a TV, not a monitor, I've always thought I  made a mistake by buying a TV which isn't made to accept input from a computer.  My thinking at the time was that since dvi converts directly to hdmi, any TV with hdmi input would be fine, but I have run into some issues.  

   The first effect of this is that I have to live with over-scan.  There is a workaround for this though.  In xfce settings,I set the number of panels to zero.  I set up borders so that maximized apps aren't off the edge of the viewable screen.  I use alt+tab to switch apps, and ctrl+alt+d to access the desktop, where I have created launchers for my favorite apps. This setup actually works quite well for a media computer, where you are viewing it from across the room.  I also had to setup the mythtv GUI size separately so that it wasn't off the edge of the screen.  During tv playback I let it over-scan.  It's my understanding that television is made to be played with this way, and I have never noticed the missing edges.     

   The second issue is that although the TV is a 1366x768 panel,it can't take input at this resolution, only 720p, 1080i, and 1080p. I suspect, (but can't prove) that I am not getting as good a picture, because I am not sending the screen a signal at it's native resolution.  Mythtv playback seems to have a softer picture, and more motion artifacts than when I watch the TV directly. 

   The thing I did right was not cheeping out on the size of the TV.  My living-room is small, but the only way to set it up is with the TV and sofa at opposite ends of the room, about 15' apart.  I struggled long and hard to find a way to make a smaller TV work, but finally decided I needed 50" at a minimum.  I haven't regretted it.  My advice is buy the biggest TV you can without going into debt.  At the very minimum get one that has a viewing area as tall as that of your current television,  so that 4:3 content won't be any smaller.   

   Also I recommend the pchdtv tuner cards. [http://www.pchdtv.com/]("http://www.pchdtv.com/")  The price is down to $99, so you might as well get two.  Choose DVB card in mythtv setup and they will work without any trouble.

---

### Post by SiHa on 2009-09-05
Also, a follow-up to itlarson on the HDMI front. If you intend using a DVI/HDMI converter, make sure the TV will accept a separate audio input on the HDMI inputs.

We made the mistake of getting a Philips 19" for the bedroom that will only accept audio over HDMI for all three HDMI inputs - even the auxilliary one on the side. So we've ended up using the VGA, but the picture isn't as sharp as I through HDMI.

---

### Post by itlarson on 2009-09-05
Good point about the audio in/outputs.  If you are using a home theater amp and speakers you will want a digital output so you can have surround when you are watching the TV's built-in tuner.  If you are using the TV's speakers you may want a digital input as SiHa mentions.  I think if your myth box has a hdmi out you can send sound over that these days, but I'm not 100% sure if this is working reliably.

---

### Post by joshoekstra on 2009-09-06
For me it is working reliably.

---

### Post by Caysho on 2009-09-08
> **itlarson said:**
> 
...
   My thinking at the time was that since dvi converts directly to hdmi, any TV with hdmi input would be fine, but I have run into some issues.
   The first effect of this is that I have to live with over-scan.
 ...


This is why I looked into the pixel mapping.  1:1 mapping avoids the overscan issues - the picture is presented as broadcast with no postprocessing done by the TV.  The TV can be treated as a monitor.

Overscanning is typical only because CRT TV's did it, so it hangs around for legacy reasons (user expectations ?).

---

### Post by newlinux on 2009-09-09
Just a point about not accepting native resolution over HDMI inputs:

One would hope that giving your TV 720p or 1080p/i over HDMI would not degrade the TV picture much (overscan is another issue easily addressed in myth, but not so much by other applications and your desktop). TV's should be optimized to convert those signals to its native resolution, since any cable box, satellite box, etc. will have be sending 720p or 1080i/p through the HDMI input as well, regardless of the TV's native resolution. So you probably aren't losing too much picture quality giving a 1366x768 native res TV a 720p or 1080i/p resolution signal. Depends on which scaler is better, your video card's or your TV's because the HD tv signal will be converted one way or another since it isn't 1366x768.

---

### Post by SiHa on 2009-09-10
That's a good point. I stumbled across [[COLOR="Navy"]**this**[/COLOR]](http://hd1080i.blogspot.com/2006/12/1080i-on-1366x768-resolution-problems.html) page when I was trying to get the best out of my new TV a while back.

---

### Post by the Goat on 2009-09-10
I use a 47 inch 16:9 1080p monitor instead of a TV and I couldn't be happier.  I saved money and the monitor has multiple DVI and HDMI inputs that work like a dream with computer video outputs.  I have never missed having a tuner built into the display.

---

