---
title: "[64 bit] ESPN 3, Flash 10, Full Screen Problems"
date: 2010-05-11
forum: Multimedia Software
---

### Post by lespedeza on 2010-05-11
I'm having problems viewing ESPN3 in full screen mode.  I'm using

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.3) Gecko/20100407 Ubuntu/9.10 (karmic) Firefox/3.6.3
Ubuntu Karmic 64-bit
Adobe Flash 10,0,45,2
Video card is a MSI Geforce 9400 using the HDMI output to an LCD.

Flash full screen works fine for Hulu Desktop, YouTube, etc.  I just have problems when switching to full screen in ESPN3.  The other viewing modes in ESPN3 work fine, compact and mosaic.

When I switch to full-screen, the controls show up across the middle of the screen and I only see a small strip of the video, also in the middle of the screen.

Anyone else experiencing anything similar?  Any suggestions on what might be the problem?  

Thanks.

---

### Post by WinterRain on 2010-05-11
Are you using 64bit flash?

---

### Post by lespedeza on 2010-05-11
> **WinterRain said:**
> Are you using 64bit flash?

Yes, I'm using 64 bit flash downloaded from the following link

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

---

### Post by WinterRain on 2010-05-11
I've noticed that some websites do full screen perfect, and others don't. As far as I know, there's nothing that can be done about it. If someone can tell me different, that would be great, but for now I live with it.

---

### Post by badnaam on 2010-05-23
I am having the same problem. Did you ever finda  solution?

---

### Post by lespedeza on 2010-05-23
Hey badnaam, I hadn't found a solution, until I saw your response.  This is what I did to get things working.

I could never get it to work with version 10.0.45.2, so I realized that there is a version 10.1 out.  I installed that and it seems to be working right now.

There is no 64-bit 10.1 version, so I had to follow the directions [_here_]("http://blog.turabdin.nl/2010/05/install-flash-10-1-beta-on-ubuntu-64-bits/") to get it to work.  

Don't use the link for the beta on the web page.  Here's the correct [_link_]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc5_linux_052010.tar.gz") for the newest version of the plugin.

Let me know if you have any problems.  I'm no expert, but I was able to get this to work.

BTW, I submitted a comment w/ ESPN and there response was that they didn't support Linux, so they're not much help.

Cheers.

---

### Post by nelwin on 2010-06-02
Fixed! Fullscreen working beautifully on 64-bit Ubuntu 10.04. I followed Lespedeza's instructions and had it working in no time. 
The only thing worth mentioning is that you need to copy the libflashplayer.so file (after extracting) to a couple places. For me it was...
   /usr/lib/firefox/plugins
   /usr/lib/mozilla/plugins
   /home/yourusername/.mozilla/plugins
   /home/yourusername/.mozilla/firefox/plugins
I opened a terminal and used "gksu nautilus" to open the file browser as root and copy the libflashplayer.so to these locations (replacing the older one). Hope this helps and thanks to Lespedeza! :)

---

### Post by lovinglinux on 2010-06-02
> **nelwin said:**
> Fixed! Fullscreen working beautifully on 64-bit Ubuntu 10.04. I followed Lespedeza's instructions and had it working in no time. 
The only thing worth mentioning is that you need to copy the libflashplayer.so file (after extracting) to a couple places. For me it was...
   /usr/lib/firefox/plugins
   /usr/lib/mozilla/plugins
   /home/yourusername/.mozilla/plugins
   /home/yourusername/.mozilla/firefox/plugins
I opened a terminal and used "gksu nautilus" to open the file browser as root and copy the libflashplayer.so to these locations (replacing the older one). Hope this helps and thanks to Lespedeza! :)

Is better to create symlinks instead of copying the files and there is no need to put them on the home folder if you have symlinks under /usr/lib/mozilla/plugins and  /usr/lib/firefox-addons/plugins.

See the 64bit code at [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) and replace the paths to the adobe plugins with the version you want. That code is for the 10.0.45 version.

---

