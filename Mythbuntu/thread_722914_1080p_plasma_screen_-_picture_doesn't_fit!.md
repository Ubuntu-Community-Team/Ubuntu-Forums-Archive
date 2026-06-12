---
title: "1080p plasma screen - picture doesn't fit!"
date: 2008-03-13
forum: Mythbuntu
---

### Post by cdt24 on 2008-03-13
I've been trying to get my myth box to display properly on my 50" 1080p plasma screen for a couple of weeks now, but with no luck. I have a mobo with a builtin nVidia 7100 video card that can output 1920x1080 just fine, the problem is that the picture that comes up on the screen is too big for the screen. That is, anything on the screen borders is slightly off the screen such as the menu bar or the "taskbar." I've messed with various modeline setup instructions and even tried installing windows to see if maybe there was something it could do - no luck in any of those cases. The picture is always too big for the screen!

So I'm wondering if anybody out there has had to deal with this and what they did to make it work. Please help!

Thanks!

---

### Post by tubasoldier on 2008-03-13
I have connected my computer to my Vizio television. I had trouble at first with getting the picture to fit within the screen. But after delving into it a bit I realized that it was not a problem caused by Linux. It was my television. After searching through my television menu I found and option to adjust the screen with my television. Thankfully it was an auto adjust.

perhaps your television has a similar option?

---

### Post by jaakan on 2008-03-13
have you tried a smaller display size output? there are a lot of TVs out there that can take a 1920x1080 source but that can't fully display it. they resize or crop to make the picture fit.

---

### Post by matteaton on 2008-03-13
What you're describing there is "Overscanning". TV signal is always cropped at the edges, don't know why but it is. All tv's do this. Some tv's (and if youre lucky, your tv will too) have a "Just Scan" feature for exactly this type of use. Try reading through your tv's manual, or spend a few minutes looking through the menu system to see if there is a way of adjusting for this. 

If you want to PM me with your TV make and model number, I'll gladly try and look up to see if the TV has a "Just Scan" mode or not.

Hope thats helpful!

---

### Post by uopjohnson on 2008-03-13
I used to fight with this on the pvr-350s output all the time.  I was never able to get a satisfactory view of the desktop, however there are lots of overscan/underscan options in the mythtv setup so if you are just using it for myth then try tweaking those to get a better picture on the screen.

---

### Post by cdt24 on 2008-03-13
Talk about barking up the wrong tree.  I tried for hours with modeline angle - to no avail.  However, thanks to the many great suggestions from folks on this site, I found that my TV has 2 "HD Size" settings.  The default was the one I had problems with, but the other is exactly what I needed!  Thanks again to everybody that suggested this!

---

### Post by nothing0011 on 2008-04-27
I am having the same overscan problem but enabling "Just Scan" on my Samsung DLP is not working. I am connected via a DVI - HDMI cable and there is no custom resize option for HDMI/DVI connections on my television. It's there for VGA but even then it overscans. It really looks like as if it is an issue with X. I need to resize the desktop resolution of x windows for it to fit properly.

Of course this would all be much easier if there was another tool like HDTV Resize found in the windows version of the NVIDIA display drivers. But windows plays back video with horrible quality when resized to 1080p.

Also, how can I get XvMC to work in Hardy? Seems that will fix my jitter problems when watching HD content.

---

### Post by Notselfcreated on 2008-05-12
I have a similar issue, and I'm not sure whether the problem is the TV or X.

TV is a Westinghouse LVM-37w3se (no EDID problem).
Computer is an Eee PC 701 running Ubuntu 8.04.

I successfully achieved 1920x1080 output by editing xorg.conf according [these instructions]("http://ubuntuforums.org/archive/index.php/t-425527.html").

However, there is big time overscanning in all directions, and the automatic thing doesn't work well.

Interestingly, when I change the picture to "standard" (which squeezes the picture into a 4:3 ratio for watching regular television), the picture looks better--the vertical resolution is displayed perfectly; only the horizontal (1920 pixels) dimension is distorted. Circles are ovals.

I experimented with adding a 1440x1080 mode (a 4:3 ratio) and using it with the "standard" setting on my TV. It's almost perfect. Nice temporary solution. But none of this TV's configurations will correctly display 1920x1280. Garbage.

The reason I suspect that this is an X problem is that my XBox360 can do 1920x1280 through a VGA cable with no issues.

---

### Post by Notselfcreated on 2008-05-13
Now here's an interesting development. No doubt about it, my tv is 1080p. But I finally succeeded in getting my display to use the full screen real estate. How? I set it to 1920x1200 (the 16x10 ratio). Thus it is a bit higher than the native resolution, and some lines of pixels are a little blurry. But it's the best solution I've come up with.

Theory: Computer monitors typically only use the 16x10 ratio. This is a TV, but the signal is going through a 19-pin SVGA cable. The TV is not expecting a 16x9 ratio signal from the VGA port, so it doesn't know what to do with it when it gets it. When the TV gets a 16x10 signal from the VGA port, it's comfortable again, even if some of the detail is lost in the pixel stretching.

EDIT: Something's not quite right. To test my theory, I tried a 16x10 resolution of 1728x1080. Unfortunately, I got the overscanning problems again. So using a 16x10 resolution isn't the trick.

It seems like my particular 1080p monitor has overscanning problems with any wide-screen 1080p resolution (1440x1080 works fine in a certain mode). This is weird especially because it has no problems with resolutions of high or lower vertical size.

---

