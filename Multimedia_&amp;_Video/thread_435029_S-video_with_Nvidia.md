---
title: "S-video with Nvidia"
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by El Lance-O on 2007-05-06
I want to watch movies and such on my tv (which has s-video, so I don't have to use composite) but not clone the desktop, instead have it set up as a duel monitor. Also, I'm running beryl so how would I be able to transfer windows from monitor to TV while still being able to move windows around the cube on the monitor?

I tried to install nvtv to see if I could at least see if my video card (Nvidia GeForce6600) would work.

> Fatal: No supported video card found.

I looked up the card and it lists it as a feature...what to do?

I'm on feisty by the way, thanks ahead of time!

---

### Post by Nythain on 2007-05-06
is it working with desktop cloning right now...
does the tv show up as a monitor when you run gksudo nvidia-settings...
if so, do you have it set up as seperate x screen with the xinerama box checked...
if what im reading is what your saying, that should so the trick, possibly with some slight alterations to the xorg.conf once you get it set up
as for the beryl issue... there are guides to help set that up, but i dont run beryl so i dotn know what they are, try searching "dual monitor beryl" on the forums

---

### Post by El Lance-O on 2007-05-06
Well at this point I don't have a S-video cord even, I just wanted to know if my system was capable of it before I went out and bought it.

---

### Post by Nythain on 2007-05-06
should be, but dont quote me, im not sure of all the intricacies of svideo/vga/dvi and all that jazz

---

### Post by puterboy on 2007-06-09
I seem to have a solution. I'm using a 6600gt on ubuntu 6.06 amd64

First off, i didn't use nvtv. i used envy, which configured all my settings for me. maybe it's cheating, but whatever.....after it installed the packages and stuff i needed, nvtv STILL wouldn't work, despite finally seeing the NVIDIA splash screen. so I went into 

Applications>System Tools>NVIDIA X Server Settings

I went to the X Server Display Configuration, clicked on my TV (which it had never detected before), and configured it (I put my screen to the right of screen 0, my PC monitor. I couldn't apply settings, so I saved it and restarted. It didn't work after restarting my X Server (Ctrl+Alt+Shift+Backspace). I found that the file didn't have the correct permissions, so i used

sudo chmod a+rwx /etc/X11/xorg.conf

to let me write it. I couldn't seem to keep any settings by overwriting the file, so I had to save the xorg.conf from the settings panel on my desktop, open both, and paste over the contents of the old file with the new one. worked like a charm. i'm so newbish, but it works now. any questions, feel free to PM me, i'll try to help as much as I can.

Also, after every reboot of the X server, you need to reconfigure your TV setting in the panel, because if it didn't work, it'll overwrite the settings to where your TV is disabled.

Hope it works!!!

---

