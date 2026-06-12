---
title: "Limit display to smaller region of LCD?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by manducasexta on 2008-07-29
Hi, and thanks in advance for checking this out. I'm trying to limit the display in ubuntu to just a subsection of the LCD.

I'm working on a project with a Dell Inspiron 4150 and an old TDC Project-or-view (which looks like a microfiche reader). I'm setting up the TDC as a frame for the laptop and using it as a digital picture frame on steroids (or maybe more like a chumby: displaying weather, rss, email, calendar, etc as well as pictures).

Here are a few pictures to give you a general sense of what I'm up to. They're crummy pix, but hopefully they'll be sufficient.

The TDC before disassembly:
[IMG]http://farm4.static.flickr.com/3206/2712560361_f814f7e3c5_d.jpg[/IMG]

Guts of TDC with laptop guts propped inside
[IMG]http://farm4.static.flickr.com/3003/2713374402_996802665d_d.jpg[/IMG]

Front view of TDC with laptop inside 
[IMG]http://farm4.static.flickr.com/3239/2712561561_90c3decfe8_d.jpg[/IMG]

Anyway, I disassembled the laptop and set the display inside the TDC. Now the screen is physically in the portrait orientation. I used Ubuntu's System > Preferences > Screen Resolution to rotate the screen after reducing the resolution from 1200x1600 to 768x1024. Excellent.

However, the opening in the TDC is smaller than the laptop screen. I'd like to reduce the region on the screen that is addressed by the video card, so I can run things full screen and they won't be invisible under the bottom of the TDC frame. Also, I'd like to be able to maximize applications without losing them out of sight. I've fooled around with XRANDR and xorg.conf a little bit.

Successful reduction of screen used: 
I changed xorg.conf, adding 
       SubSection "Display"
               Virtual         600 800
       EndSubSection

to the "screen" section.

Once I restarted, this effectively limited the size to a subsection of the
screen. However, the display was no longer rotated. When I tried to rotate it, with xrandr, I wasn't able to.

I suspect I may need to fill in my xorg.conf (it's completely bare at this point) and then set all the xrandr arguments in there. I don't know how to fill that in though.


Specs:
Dell Inspiron 4150, 512 MB RAM, P4 - M CPU, 2.20GHz
Video card: ATI Mobility Radeon 7500C 32Mb 
Display: UXGA 14.1" (357.1mm x 214.3mm)

Thanks for any suggestions.

---

### Post by manducasexta on 2008-07-30
bump. anyone? suggestions about better places to ask this question?

---

### Post by aeiah on 2008-07-30
can you state that you want rotation from within xorg.conf?

i solved my overscanning hdtv by setting a 'resolution within a resolution' like you but i didnt need any rotation, obviously. anyway, i did it with modelines instead, perhaps if you set rotation in xorg.conf and this doesnt solve the problem, adding a modeline instead of a virtual res will help? its worth trying, although it may take longer time than its worth.

the lazy way is to use custom-sized gnome or xfce panels around all the edges, making them the thickness of the hidden parts of the screen. since you wont be using this for a great deal of stuff, you might find this way sufficient. programs will maximize normally and not overlap the panels, although fullscreen things will. if the only fullscreen things you use are something for displaying pictures and video then you may find an application that will compensate for you. i know things like mplayer and xine will do this with commandline options.

cool project by the way

---

