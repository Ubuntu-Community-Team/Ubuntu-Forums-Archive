---
title: "Samsung Widescreen TV with Intel 845GE"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by infinitejones on 2007-06-09
I have a 91cm Samsung Widescreen LCD TV which has a VGA input. I've recently picked up a cheap desktop with an Intel 82845GE integrated graphics chip, and I'm using it as a headless server to store all of my music, ripped DVDs, etc.

I've set up FreeNX Server to be able to access the server from my laptop for general maintenance etc, and this works perfectly. However, I'd like to be able to connect it to the TV via VGA (which in turn is hooked up to my amp and speakers) to play MP3s (with visualisations), watch videos and so on. 

With the PC as the source for the TV, everything's fine during boot-up, including the screen with the Ubuntu logo and the progress bar. However, when it gets as far as the log-in screen, and the desktop after log-in (I've set the server up to login automatically), the display flashes on and off for about 10 seconds and eventually the TV gives up and turns itself off because it thinks there's no source. In the brief intervals when the desktop is visible, I can tell that everything is being displayed properly - it's just that the display disappears after too short a time for me to be able to do anything like changing the display resolution. If I try to change the display resolution from the laptop, the only options it gives me are the ones relevant to my laptop display, and I assume this is because of the way FreeNX works.

How can I fix this? I kind of know what I'm doing with Ubuntu, but not to the extent of manually changing xorg.conf without guidance. Is it a problem with the graphics driver being unable to support the resolution of the widescreen TV? Are there any changes I can make to xorg.conf to fix this? Any other ideas?

Thanks!

---

