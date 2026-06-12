---
title: "Dual monitor questions"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by searayman on 2011-04-06
I am running Natty and actually liking it so far. Just a a few questions about running dual monitor on it. 

First is there anyway to have just one screen with the clock at the top. The whole one bar thing is just mirrored onto both screens at the top, and looks kind of tacky...

Also with wallpapers is there anyway to have them stretch across both screens instead of being a copy on both screens?

---

### Post by Scenemaker on 2011-04-06
> **searayman said:**
> I am running Natty and actually liking it so far. Just a a few questions about running dual monitor on it. 

First is there anyway to have just one screen with the clock at the top. The whole one bar thing is just mirrored onto both screens at the top, and looks kind of tacky...

I find this tacky as well.  

> **searayman said:**
> 
Also with wallpapers is there anyway to have them stretch across both screens instead of being a copy on both screens?

Yes, it is in the options on the background screen under style.  Choose "Span".    If you use a regular size Wallpaper like 1680x1050, it centers it between the two monitors and looks goofy.  Basically, the dimensions would be twice the length if your monitors are the same size.  So something like 3360x1050  If you are like me with 2 different sized monitors, that would be tough to pull off and have look decent.

---

### Post by osarusan on 2011-04-06
I agree.

Dual monitors has always given me issues in gnome. It always seems to be stapled on as an afterthought with very little consideration.

Now, with Unity, it seems like they have actually taken a huge step backwards by forcing you to accept it this one specific way. It's very frustrating.

I want the ability to display the panel across only one screen -- and particularly to display the Launcher on whichever screen I like, not always the leftmost screen.

---

### Post by Tich666 on 2011-04-11
> **osarusan said:**
> I agree.
I want the ability to display the panel across only one screen -- and particularly to display the Launcher on whichever screen I like, not always the leftmost screen.

I second that one, I only want the panel and unity launcher on my main display, which happens to be the leftmost screen, yet unity decides the launcher should be placed on the right screen, just in the middle of my desktop. It quite frankly can not get any more stupid than that!

---

### Post by Blasphemist on 2011-04-11
I seem to have nearly the opposite preferences but I will offer a bit of help. I too have natty unity and two monitors, my laptop display and an external. The external sits to the right of the laptop display. The displays support different resolutions and I have them both on maximum resolution. I have my wallpaper on each screen, not stretched.

I have the launcher on the laptop monitor and the panel on both. I prefer this as I use the external mostly for my browser with many tabs open usually. I use the laptop monitor for the terminal, admin screens, mail and screens that I only use periodically.

You can install and use the multiple screens app to tell the system which display is on the left or right and which is the monitor for the launcher. You'll see the outputs on the basic tab and you can set their resolutions there. On the layout tab, I drag my external display to the right position but it sounds like you need to dray the display that currently has the launcher to the left but you may have to experiment with this.

I installed multiple screens app from the software center. Note that each time I run this multiple display front end to grandr it appears I've never set the position of the monitors. Here is a screenshot of my desktop showing all of this.

---

### Post by ben s on 2011-04-11
Jim, I'm glad you were able to get your monitors working correctly.  I'm having an issue and I'm wondering if you see it too, since it appears one of your screens is taller than the other.  On your short screen, can you send your pointer out of bounds (i.e., above or below the screen)?  If I alt-drag a window in, say, the upper 1/3, I can drag it down below the bottom of the shorter screen.  Normally, the pointer should stop when it reaches the bottom of the screen, but because one screen is taller, it seems as though Unity is taking that as the total screen length on both screens.

This is an issue because system windows are constantly opening up with 1/2 of their contents submerged and I need to alt-drag them up.  Very annoying.

I'm wondering if it's just my set up or if it's common with all heterogeneous dual-monitor configs.

---

### Post by Blasphemist on 2011-04-11
That is happening to me too. For a while the issue was at the top of laptop display and that was really hard to deal with. I found a resolution, not the max and not my preference, on the external that minimized the problem but didn't solve it. Then I switched to the gnome classic desktop and ended up installing the multiple display app to get to where the resolutions could be as I wanted and the issue you mentioned went to the bottom of the screen.

I had a post in here about this and quite a few viewed it but no one responded. For anyone else reading this, we can drag the mouse off the bottom of one of our monitors and windows don't respect the actual dimensions of the physical display as well. I don't know how to describe it fully without being very wordy.

I've attached a screenshot. If you can see the workspace representation in the bottom panel you can windows sticking down off the bottom of each monitor.

---

### Post by Tich666 on 2011-04-12
I don't have any problems setting up my displays with xrandr or the monitors tool which is just a graphical frontend to that.

What does not work for me is having the unity panel at 0,0 as in your picture, it always stays on the right monitor, my laptop, unless I deactivate it and only use the external monitor. (see screenshot)

I realized after a day of using unity that having the panel on top of both screens is actually neccessary for window management, etc. but I would appreciate it, if the clock, indicators, etc. would stay on my main display and not be needlessly duplicated on the secondary one.

About the windows going below the actualy screen, that does not seem to be a problem for me!

---

### Post by Blasphemist on 2011-04-12
So let me guess, is this just a question of a system being created assuming everyone is right handed? My external is on the right because that is where it works best for the mouse to be. The wireless keyboard rests in front of the laptop and the mouse in front of the external monitor.

I can't find any configuration settings to move the BFB and the launcher, the activities center to be pc I believe. So how does classic mode look for you?

---

### Post by Tich666 on 2011-04-12
Lol.. I am right handed. :P

Classic look (in both Maverick and Natty) looks exactly like I want it, with the gnome panel on my primary (external) display.

I've always had the bigger monitor to the left of the smaller one, which in this case just means my laptop is right of the external display and my current desk would not allow me to switch that around either. :S

---

### Post by Blasphemist on 2011-04-12
Here's a wild idea then. If your classic desktop looks right, and you can just log out and in to test that, try enabling the unity plugin in classic. I did it and you get classic with the unity launcher, kind of a hybrid.

See what you think. You can always just disable the plugin again as I did.

---

### Post by Tich666 on 2011-04-13
Not a bad idea, but unfortunately it did not work! Got the same result when I enabled unity plugin in the classic gnome desktop as when I started the unity session.
edit:
I fixed it with this very simple, yet somehow hard to come by xrandr trick!

This is my config:
```
xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
LVDS1 connected 1280x800+1680+0 (normal left inverted right x axis y axis) 287mm x 180mm
   1280x800 59.8*+
   1024x768 60.0
   800x600 60.3 56.2
   640x480 59.9
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 296mm
   1680x1050 60.3*+
   1280x1024 75.0 60.0
   1440x900 75.0 59.9
   1280x960 60.0
   1152x864 75.0
   1280x720 60.0
   1024x768 75.1 60.0
   800x600 75.0 60.3
   640x480 75.0 60.0
   720x400 70.1
```

And this is the solution:
```
xrandr --output HDMI1 --primary
```

---

### Post by alessandramorgan on 2011-04-16
Thank you, that worked beautifully.

"xrandr --output VGA-0 --primary"

Why is there not a checkbox for this under each display in the "Monitors" preference pane?

---

### Post by teachop on 2011-04-16
> **alessandramorgan said:**
> Why is there not a checkbox for this under each display in the "Monitors" preference pane?
I agree a checkbox would have helped me, I didn't think or know to look in xrandr for an option of that sort.

---

