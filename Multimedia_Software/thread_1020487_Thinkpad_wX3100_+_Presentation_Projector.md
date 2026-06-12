---
title: "Thinkpad w/X3100 + Presentation Projector"
date: 2008-12-24
forum: Multimedia Software
---

### Post by defcon3 on 2008-12-24
Hello:

I am using my Thinkpad T61 (with Intel X3100 video adapter) extensively for presentations. Every time I need to make one, I reboot into Windows :(

This is because the first time I thought to give one using my lovely Ubuntu, I failed miserably in front of the coming audience - the resolution was cut in the middle, screen looked horible, mouse was on the wall (through projector) while menus were on the laptop screen... 

Now I decided to put an end to this disaster and brought home with me for the holidays one of the projectors I use most frequently - an EIKI with maximum resolution 1280x1024; 

I tried using displayconfig-gtk, I attempted the console xrandr, quite the same funny effect I got during my first attempt... 

I need some help getting something pretty simple done: 
My laptop has 1280x800 screen; I wish to have *the exact same output* to my projector; i.e. whatever I have on my laptop screen to appear on the wall... 

Please help me get it working, I am really tired of booting windows for each presentation :popcorn:

---

### Post by defcon3 on 2009-01-01
I would be pleased to even get ideas where/what to follow and try something... :KS

---

### Post by acreech on 2009-01-05
I just figured out how to get an "Infocus" projector to work with my Intrepid system. I added the following lines to my xorg.conf file at the bottom where it says "Section Device"

> 
#        Option  "TwinView"               "Yes"
#        Option  "TwinViewOrientation"    "Clone"
#        Option "MetaModes"    "1400X1050,1680X1050,1680X1050"

On the third option, make the first set of numbers what you want you projection resloution to be. When I want to use the projector I remove the "#" from each line, save & close (both gedit and terminal), then Ctl+Alt+Backspace and then log back in. 

This transfers my laptop monitor to the projector. One thing to note here is it turns your laptop monitor completely off. 

I also found this website, but have not got the method that is suggested to work....

[http://www.len.ro/2007/03/external-monitor-on-linux-laptop-nvidia-/](http://www.len.ro/2007/03/external-monitor-on-linux-laptop-nvidia-/)

---

