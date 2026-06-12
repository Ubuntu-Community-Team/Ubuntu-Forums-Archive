---
title: "Adobe Flash Plug-In"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by CHFFriday on 2006-11-28
When I install Flash Plug-in For Fire Fox I can not view Videos from CNN.but I have sound. If I un-install the Flash Plug-in I can see the Video and hear it. The Video is played by Mplayer. I have tried to fix this buy upgrading to Flash 9.0 that I downloaded from Adobe. [http://labs.adobe.com/downloads/flashplayer9.html](http://labs.adobe.com/downloads/flashplayer9.html)

Can I get some help with is?

Maybe I installed the Flash upgrade incorrectly? When I right click on the "Video Box" of the player I get setup for Flash 9.0 but all it has is something to do with allowing Flash to use the computer Mic etc. None of the settings change anything.

I can not find a way to setup what Plug-In is to be used for these playbacks.](*,) 

CHFFriday

---

### Post by bswilson on 2006-11-28
> **CHFFriday said:**
> Maybe I installed the Flash upgrade incorrectly?

Can you share some details?  There's really not much to the 'installation' of Flash 9 in Linux.  All you have to do is place one file in a specific directory and you're done.  So...

[LIST=1]
[*]Where do you have Firefox installed?
[*]What is the path of your Firefox plugins directory?
[*]Where is the file libflashplayer.so on your system, who is the file owner, and what permissions does the file have?
[/LIST]

---

### Post by CHFFriday on 2006-11-28
bswilson,
I'm not at the PC that 6.06 dapper is installed on. I think the directory is some thing like this "firefox_nofree plugins" Sorry about this. I had to run Natulis from Terminal using sudo so I copy copy libflashplayer.so as I did not have rights otherwise.

If you can tell me were you think everything should be for 6.06 dapper and I will check it out when I get home.

CHFFriday

---

### Post by CHFFriday on 2006-11-28
bswilson,
I wiould like to make a correction.
1st: The WEB site to test is [www.foxnews.com](www.foxnews.com). Not CNN.com

2nd:the directories are usr/lib/flashplugin-nofree
and CHFFriday/.mozilla/plugins. CHFFriday is the logon user.
libflashplayer.so is installed in both.

CHFFriday

---

### Post by CHFFriday on 2006-11-29
bswilson,
After some more testing of other WEB sites it seams that the [www.foxnews.com](www.foxnews.com) is the only one I seam to have a problem with. This makesme think that the Flash Plugin is installed OK and that maybe something is wrong with the Web site.

What do you think?

CHFFriday

---

