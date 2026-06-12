---
title: "Want to upgrade an intel video driver"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by Dannyblueyes on 2007-11-30
I currently have the following video card 
Mobile Intel® 945GM Express Chipset Family

How to I obtain and install the latest driver for this in Ubuntu gutsy gibbon? I would really like to be able to play second life and lbreakout 2 without having the computer freeze after a few minutes like it's been doing. 

A bit of background, I'm a linux and a ubuntu newbie. Just installed it about a week ago switching from Vista. I'm unfamiliar with command lines and have installed all of my other apps using the applications menu or WINE (installing the driver through WINE didn't work, although I didn't document why :(   ). I am currently on vacation and have plenty of time to learn new things if necessary, but I'd prefer an easy answer if possible. 

Thank you very much in advance.

---

### Post by foolsh on 2007-11-30
I take it running this in a terminal
```
glxinfo | grep render
```

gives you 
```
direct rendering: No
```

try running 

```
cat /etc/X11/xorg.conf | grep intel
```
if you get 
```
Driver          "intel"
```
try running 
```
sudo gedit /etc/X11/xorg.conf
```
find the line that says Driver  "intel" and change it to Driver  "i810"
save the file then press Ctrl + Alt + Backspace or just reboot

according to [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) we should already have the latest driver for the 945 chipset

---

### Post by Dannyblueyes on 2007-12-05
I entered the first line of code suggested. The computer said "Direct Rendering Yes".

I then entered the last line of code (sudo gedit  etc) and changed driver From "Intel" to i810. saved it, rebooted, and tried second life again. 

I got the same result as before. did I do this correctly? Is there another answer?

---

