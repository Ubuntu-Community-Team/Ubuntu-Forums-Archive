---
title: "Hello.... tv issue"
date: 2011-10-30
forum: Multimedia Software
---

### Post by saltsprung on 2011-10-30
Hi, I just installed ubuntu 10.04 on the new desktop and the tv won't work with it

I had the tv hooked up to the last computer no problem

trying to figure out why the tv won't work with this computer though

:confused:

---

### Post by saltsprung on 2011-10-31
last computer I had (yesterday) had just put ubuntu 10.04 on it. 

it was a hp pavilion dual core amd 64 x2

I had it hooked up to my dell monitor and my emerson 32 inch tv using the s-video cord
it worked no problem 

when I first put the ubuntu disc in it showed up on both screens

new computer (yesterday)  now has ubuntu 10.04 as well

it is a hp pavilion quad core amd 

I hooked it up to both screens but the disc only showed up on the dell monitor

when I go to "monitors" and click "detect monitors" only the dell shows up

please tell me if you know what the problem might be or how I can find out how to get the computer working on the tv?

thank you in advance :)

---

### Post by saltsprung on 2011-10-31
Hello?

---

### Post by JKyleOKC on 2011-10-31
I saw your post over on the thread about "mv" and "locate" commands, and asked for a staffer to give you a hand. However I did find this thread under "New Posts" so it did finally appear.

There are an unbelievable quantity of posts here in a very few minutes, so it might take quite a while for a new post to appear in the "new posts" search.

Unfortunately I have no idea what could be causing your problem. In the past couple of years there have been many significant changes to the video drivers used in Ubuntu, and that might be part of it. This is the right place to ask; let's hope that someone who knows more than I do about it will show up and give you a hand!

---

### Post by saltsprung on 2011-10-31
Okay, thank you :)

---

### Post by lisati on 2011-10-31
Hi there. Like JKyleOKC, I'm wondering if there could be a driver issue. I'm also wondering at what point the TV needs to be switched on relative to booting your computer for the TV to be properly detected. Beyond that, I'm not sure: my experience of hooking up external displays to laptops is extremely limited.

---

### Post by saltsprung on 2011-11-01
Hi, thank you. Actually it's a desktop, but I wonder if maybe it has something to do with the last computer not having hdmi and this one does have it. Like I said, the last one and this one are hooked up with s-video. Maybe there's something in the setup or whatever that needs to be switched to s-video? I did have the tv on when I first put the ubuntu install disc in and like I said, with the last computer it came up on both screens, but this one it only came up on the monitor. Nothing at all showed on the tv. I wish there was more I could tell you now.

---

### Post by saltsprung on 2011-11-01
I went to system > administration > nvidia xserver settings > xserver display configuration

tv was disabled

so I changed that. :grin:

now the tv is working with the computer, only problem is the tv screen looks like it's zoomed in too much

that is, only part of the screen that I see on the monitor (that is working fine) is showing

to make it even weirder, it moves around when I move the mouse

while the screen on the monitor stays still :confused:

anyway, good thing I didn't go waste $35 on a hdmi cable :)

---

### Post by saltsprung on 2011-11-01
When I go to system > preferences > monitors, I get

 "It appears that your graphics driver does not support the necessary extensions to use this tool. 
 Do you want to use your graphics driver vendor's tool instead?"


Maybe I'll have to change the video card so I can get a driver that works with this?

---

### Post by wolfen69 on 2011-11-01
> **saltsprung said:**
> 
Maybe I'll have to change the video card so I can get a driver that works with this?

What is the model #?

---

### Post by saltsprung on 2011-11-01
> **wolfen69 said:**
> What is the model #?

The driver is:

173.14.22

The video card is:

NVIDIA GeForce 8500 GT

The computer is:

HP a6352f

[http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-12133158-12133158-12133158-81139564-81575402.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12132708-12133156-12133158-12133158-12133158-81139564-81575402.html)

---

### Post by BicyclerBoy on 2011-11-01
You can not use the gnome display prefs tools with nVidia driver..

Use the nvidia display config tool from the menus or:
nvidia-settings


You are getting display panning because the display (over S-video) is small compared to primary display.

If you use cloning or mirroring or twinview there will be panning if the 2 displays are different resolutions.

You are recommended to use the HDMI, via DVI-HDMI adapter cable if you have to..
A proper display link supporting EDID (HDMI,DVI VGA) is going to result in a better setup..

---

### Post by saltsprung on 2011-11-02
Okay, thank you.  Can you please tell me how I can get the tv to show  the screen just like the monitor does? With the ubuntu monitor  preferences it did it automatically on the old computer. Can I get them  to look the same now even though they have different resolution? I can get the hdmi cable if I have to, but is it possible to do it without it?

---

### Post by BicyclerBoy on 2011-11-02
I repeat: you can not use the gnome monitor prefs tool with the nVidia graphics driver.

You have to use nvidia-settings from terminal or find the nvidia config tool in the menus

If you are using Unity ..tick on the top left cnr & type nvidia...

If you want desktop cloning
you enable the 2nd monitor & enable twinview, then under the twinview tab is hidden the clone setting..

If the 2 displays have different resolutions, then there are panning options.

s-video is completely sub-optimal for your display device..
A cheap HDMI cable is $5.

---

### Post by saltsprung on 2011-11-03
Yes, I understand, thank you. I am using the nvidia config tool. I only mentioned the gnome monitor prefs tool because it worked no prob before with getting both the 22" monitor and the 32" tv to look exactly the same on each screen.

I now have the twinview enabled with the clone setting, thank you again. :) The monitor was showing the entire page, while the tv was only showing the upper left quadrant of the page. 

The monitor resolution was at 1680 x 1050 and the tv resolution was at 1024 x 768 (the highest it will go).

So I set both for 1024 x 768. 

Now it works good except the outside 1/2 inch or so, top, bottom, right and left are missing on the tv. It's okay because I can still use the monitor if I need to. 

Can that be fixed?

Btw, the cheapest hdmi cord I found here on the island was $27.99 plus tax B.C. (hst) ;)

---

### Post by BicyclerBoy on 2011-11-03
I wouldn't have recommended HDMI cable unless it was of benefit to you..
An HDMI cable from a normal shop (retail consumer) here would be $30.
But from any internet shop/computer shop it is $5-10.

There are different ways to make the panning behave...you might not need to use same resolution on both..

There is an HDMI (& TV out) overscan adjustment tool in nvidia-settings under the specific monitor section..should be somewhere in the bottom couple of sections/tabs.

Note you do not have to use twinview..I prefer separate X screens for full screens programs on the TV (MythTV, XBMC mplayer etc).
There is a slight learn curve to get the best for separate X screens tho..

---

### Post by saltsprung on 2011-11-07
Thank you again BicyclerBoy, I will get the hdmi cord. I haven't quite figured out the overscan adjustment tool yet if there actually is one here. I mean if it is I don't understand it, but the tv is serving it's purpose as it is now. :)

---

### Post by saltsprung on 2011-11-15
> **BicyclerBoy said:**
> I wouldn't have recommended HDMI cable unless it was of benefit to you..

WOW! What a difference. The picture is perfect compared to... blurry with the s-video cord. Wow. The overscan is gone too. Thank you :D

---

