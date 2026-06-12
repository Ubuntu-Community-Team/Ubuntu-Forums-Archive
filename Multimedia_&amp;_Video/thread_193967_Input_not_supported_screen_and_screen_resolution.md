---
title: "Input not supported screen and screen resolution"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by Huggy on 2006-06-10
Hey, when I got the OpenGl support on my Geforce 5200 going, the input not supported screen came back, but I noticed that it was not running on it's LCD native resolution. It's running at 86hz and has no other option I can change it to. So I was wandering how do I manually edit my refresh rate? I think it might solve the bouncing screen problem, because when I change it back to vesa, I loose OpenGl and 3d Accelleration support. It's a long shot, but it just might work. If you can help please do, because this bouncing input not supported screen is really annoying to work around.

---

### Post by zugu on 2006-06-10
For the screen refresh thing, try```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```
Now press Page Down until you see this:```
Section "Monitor"
```Insert this line below:```
       VertRefresh         50-160
```(note that there is a tab before VertRefresh and one before the numerical values) Save and close the text editor. Close all open programs and restart your display manager by pressing CTRL+ALT+BACKSPACE. You should now be able to choose different values for your screen refresh rate in Preferences >> Screen Resolution. If something is wrong after performing these commands (i.e. GNOME does not start), try:```
sudo mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```and restart GNOME.

---

### Post by Huggy on 2006-06-11
Okay, I did that, and my screen refresh rate is now 85hz and still has no other options, and that annoying input not supported screen is still there. For some reason I just can't change that refresh rate, and I'm not totally sure that will solve the bouncing screen either. I know I can put in vesa for my driver, but then I lose OpenGl and 3d Accell. What do I do?

---

