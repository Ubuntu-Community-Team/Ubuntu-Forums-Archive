---
title: "Unable to run computer in any high resolution."
date: 2013-01-20
forum: Multimedia Software
---

### Post by vapblack on 2013-01-20
Greetings all.
So the problem is this. I have an NVIDIA 9500gt graphics card and I have a 24 inch hdtv connected via HDMI cable. When I ever I try to run it in anything higher than 1360x768. I feel like my monitor is being wasted. I have updated the drivers via the hardware control panel. 

When I put the computer in it's highest resolution, or indeed anything higher than 1360x768 some of the screen gets cut off. I can only see that in the monitor though. If I take a screenshot, the whole screen is captured. 

I was thinking that maybe the computer does not know I have a 24inch monitor. I suspect it even more now that I see the control panel and it says "STD Computer INC 19in"

[IMG]http://i.imgur.com/DuN2fMbl.jpg[/IMG]

---

### Post by Cheesemill on 2013-01-21
What's the resolution of your TV?

A lot of HD televisions only have a resolution of 1360 x 768.

---

### Post by SeijiSensei on 2013-01-21
Are you using the proprietary NVIDIA driver?  If not, try running "sudo apt-get install nvidia-current", then use the NVIDIA control panel (under "Settings") to set the resolution.

---

### Post by gordintoronto on 2013-01-21
What version of Ubuntu? What brand and model of TV?

If your TV is 1080P, set that resolution in your computer, and see if the TV's menu system can reset the TV.

---

### Post by papibe on 2013-01-21
> **vapblack said:**
> ... some of the screen gets cut off. I can only see that in the monitor though. If I take a screenshot, the whole screen is captured.

That sounds like [Overscan]("http://en.wikipedia.org/wiki/Overscan"). In other words, a problem in the HDTV settings.

If so, you have 2 options to solve it:

First (recommended): Some TV's have the ability to set how the signal is reproduced. In case of my Sony Bravia you can fix it by setting 'Full Pixel' to Screen -> Display Area. In my brother's Samsung you would set the attribute P.size to 'Full Scan' ( in the Picture Options -> Screen Size menu if I remember correctly).

Play with the options available on your TV, may be the option is not easy to see. Check your manual or research about it on the Internet.

Second: the 'Nvidia X Server Settings' has an option to correct overscan manually. Check [this]("http://www.ypass.net/blog/2010/04/nvidia-overscan-correction-fixed-in-latest-drivers/") article, or [this]("http://smartsoftwarefactory.blogspot.com/2011/01/correct-tv-overscan-using-ubuntu-nvidia.html") other one.

Tell us how it goes,
Regards.

---

### Post by vapblack on 2013-01-27
Thanks for your great responses. Alas I'm still with the issue. As for your questions:

Here's my tv
[http://www.upstarusa.com/TV-LCD-25.html](http://www.upstarusa.com/TV-LCD-25.html)
> Dynamic Contrast Ratio
1,000,000 :1 (TYP)
Resolution
1920 x 1080
Response Time
5ms
Colors
16.7 million

**SeijiSensei**: I am using proprietary Nvidia drivers. Though I did try your sugguestion 

**gordintoronto**: I'm usuing Ubuntu 12.10. I just upgraded from 12.04 and both versions seem to be doing this. When you say "set 1080 in your computer" do you mean to set my resolution to 19..x1080? if that is what you mean, I've done that. and when I do, part of the screen is cut off. The image isn't bad, just the edges are cut off and I cant see my cairo doc, or my bars at the top of the screen. 

**papibe**: Great suggestion I thought my problem was finally fixed, but alas I don't have that option in my NVIDIA control panel. The TV it's self does not have that option either. I searched exaustively looking for  fix. 


I wonder if I can manually shape the screen in unbuntu. Is that at all possible?

Is it possible that an open source driver might help me? If so, how do I go about getting them?


**Also, when I don't use any driver the screen can be in the highest resolution. Of course no games or HD video...

---

### Post by papibe on 2013-01-27
There's a good chance you can solve your overscan problem using 'xrandr'. Unfortunately, I don't have much experience with it.

I found 3 ways people use it to fix overscan: [here]("http://forums.freebsd.org/archive/index.php/t-20987.html"), [here]("http://ubuntuforums.org/showthread.php?t=1849599&highlight=intel+overscan+xrandr&page=2"), and [here]("http://forums.overclockers.com.au/showthread.php?t=862388&page=10").

The second one looks promising. First, let's say that the amount of pixels being "eaten" by overscan is 16 pixels in all directions.

Then to calculate the viewable size of the screen would be:```

1280 - 16 = 1264
720  - 16 = 704
```
Then you would do:
```
xrandr --output HDMI1 --fb 1264x704
xrandr --output HDMI1 --pos 16x16
```
Since I haven't used xrandr enough, please take these tips with a grain of salt.

Let us know how it goes.
Regards.

---

### Post by tgalati4 on 2013-01-27
Some TV's are sensitive to the cable:  VGA vs DVI vs HDMI.  Try a different cable or connection method.  My thinkpad can't put out as high a resolution on VGA vs DVI (using the dock).

---

### Post by gordintoronto on 2013-01-27
I would still concentrate on the TV's menu system.

---

### Post by vapblack on 2013-01-28
> **gordintoronto said:**
> I would still concentrate on the TV's menu system.

I checked all through the TVs menu. No luck.
still trying to do papibe's suggestion.

---

