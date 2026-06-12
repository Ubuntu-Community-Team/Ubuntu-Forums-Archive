---
title: "Make the startx terminal full screen?"
date: 2009-04-17
forum: Multimedia Software
---

### Post by abeisgreat on 2009-04-17
Howdy, I picked up a little machine with an Intel 82810 graphics card yesterday, I spent the night installing server edition 8.10 (no gui, so don't tell me to do anything from a gui, terminal only) and setting up the drivers and such, at the moment the machine is setup so it boots into the terminal, I log in, and then I can run startx if I so choose so I can run videos and such with mplayer. 

This is all fine and dandy, except when startx boots, the terminal only covers just over 1/4 the screen. This is only a minor annoyance, but the grey/black pixel background of the rest of the screen is kinda lame to look at. When I start a video with (gotta run it as root otherwise I don't get audio, but I can fix that) "sudo mplayer -fs filename" it loads the video fullscreen, and cover all of my monitor. 

So to get to my question, is there a setting somewhere for the default terminal inside of x, width and height?

(Sorry, I kinda posted this in the wrong area :P)

---

### Post by aurelieng on 2009-10-09
Same thing here... did you already get a reply ?

---

### Post by Seq on 2009-10-09
I'd try a barebones WM like fluxbox, openbox or one of the tiling WMs before trying to actually use TWM (which is what you're probably using just by running startx). They would let you set key bindings to change window sizes, etc.

---

### Post by urukrama on 2009-10-10
Xterm does not maximise because you need to tell it to maximise, either through a window manager, or by launching xterm with a different command.

Do you have a window manager installed? If so, configure that to maximise your terminal. 

If you don't, you just launch xterm without a window manager, so you'll have to tell xterm to maximise itself. You can do that by specifying this in you ~/.xinitrc (have a look at the manpage for xterm for the exact syntax). If you are entirely new to xinit and startx, have a look at [the Ubuntu wiki page about this]("https://wiki.ubuntu.com/CustomXSession").

Alternatively, you could use a special xinit command. This is what is given in the [xinit manpage]("http://www.xfree86.org/current/xinit.1.html"):

```
xinit -geometry =80x65+10+10 -fn 8x13 -j -fg white -bg navy 
This will start up a server named X, and will append the given arguments to the default xterm command. It will ignore .xinitrc.
```

If you don't like the default X background, you can easily change that by adding the following to your ~/.xinitrc: 

```
xsetroot -solid black &
```

---

