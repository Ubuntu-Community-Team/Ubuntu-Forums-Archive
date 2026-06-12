---
title: "Asus F8SA Webcam Issue"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by otetiani on 2008-01-27
Though I've been using Ubuntu for 2 years now this is my first post.

I got an Asus F8SA-X2 notebook recently and there are only 2 things that I can't get to work are the video driver (mobility radeon HD2600 driver not out yet so no 3d) and the webcam.

I have read through many many posts, but none seem close enough for me to follow to use the Syntek driver from Sourceforge.net

my usb id is  174f:5a31 which is Syntek, but I do not know which model?

Is there a way to cross-reference the usb id to a mfr/model number?

Any help is appreciated.

---

### Post by apoll0 on 2008-01-29
Hi.  I know this is going to make me sound like a complete n00b but how on earth did you get Ubuntu installed on your F8SA?  I've tried everything and for the life of me can't get it to work.

For some reason whenever I try to boot it will only display a black screen or the x server will crash.  I'm fairly certain is has to do with the hd2600.  I've tried the VESA driver on all standard resolutions and depths and it simply will not fly.

Also I have tried different distributions of Linux including Fedora 8, Backtrack, and Sabayon and none of these seem to play nicely with my new lappy.

If you could please point me in the right direction I would be greatly appreciative.

Thanks so much.

---

### Post by aciddburnn on 2008-01-30
I have been having the same problem. When I boot from the CD the install spits out a memory allocation error. After that, if I attempt to select a standard install, it crashes. If I try a text based install, it installs - but I can't get xserver started. I've installed linux many times (for the past 10 years) on old and new/unsupported hardware (included graphics cards). I've never had a problem with a graphical install. Is it a problem with the system memory or the ATI Radeon HD2600? Any help would be greatly appreciated... and I'm also using an Asus F8SA. And dare I say, should I try a linux distro other than kubuntu 7.10/ubuntu? I've tried openSuse 10.3 but that just gives me a blank screen and does nothing.

BTW, I'm going to post this in its own thread as well, so if you have a solution, please find that thread so we don't hijack the webcam issue :) I'll title it "Asus F8SA Install Issues"

---

### Post by otetiani on 2008-02-04
I do have 2GB memory vs the original 1GB, but other than that it is stock.  I dual boot Vista and Ubuntu (Vista is horrible, but I need .doc for work)
When I installed 7.10 I performed the default install and had no issues.  

I fixed the screen resolution issues (wasn't 1280x800), but I can't remember what I did.  Give me a day to figure it out.

Still no 3d since ATI hasn't released actual driver yet for the 2600, but no issues in last 2 months.

---

### Post by otetiani on 2008-02-04
Ok ,so I found the post I used to correct my screen resolution.  It was posted by Clancy_s under Hardware and Laptops  **How to Ati Mobility HD 2xxx +7.11 +Compiz** on December 8th, 2007:

> 
1. all fglrx driver. sudo apt-get install
fglrx-driver
fglrx-driver-dev
fglrx-control
xorg-driver-fglrx
xorg-driver-fglrx-dev

2. xserver-xgl install. sudo apt-get install xserver-xgl.
3. envy download - [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
4. needed to install packages for envy
dpatch
linux-headers-generic [7]
build-essential
debconf
dh-make
fakeroot
gcc-3.3
libstdc++5
module-assistant
5. envy install and 7.11. sudo dpkg -i envy*.deb
6. xorg Config adapt. sudo gedit /etc/X11/xorg.conf
In "Extensions" composite "Disable" set
7. Rebooting
8. in the xorg.conf "extension" to add the following option AIGLX "" 1 "
9. Rebooting
10. shell open and glxgears should now try to work
11. compiz install
12. xserver-xgl remove aptitude remove xserver-xgl
13. xorg.conf adapt. Under "extension" option "composite" "Enable".
14. Rebooting
15. xserver-xgl again. sudo apt-get install xserver-xgl


---

