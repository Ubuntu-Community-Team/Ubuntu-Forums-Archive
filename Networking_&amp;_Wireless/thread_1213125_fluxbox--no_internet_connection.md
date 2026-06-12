---
title: "fluxbox--no internet connection"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by guitar_man on 2009-07-14
Im having a problem with fluxbox...I'vejust install it while ago then used...but when I open y browser FF there it says that it is offline...
but when I run Gnome the browser is oK.

---

### Post by mac9416 on 2009-07-16
Hey, guitar_man (nice nick), I installed Flux the other day and had the exact same problem.
The thing is in Gnome you have a panel applet called NetworkManager applet that takes care of getting you connected to the net. NetworkManager doesn't start by default with Flux, so you have to do it manually by hitting <alt><F2> and typing 
```
nm-applet
```
in the box or by doing the same in a terminal.

You can also set nm-applet to start when Flux does by editing the startup script at ~/.fluxbox/startup and adding the following lines after "# Lines starting with a '#' are ignored."
```
# NetworkManager
nm-applet &
```

See here for [_more on editing the Fluxbox startup script_]("http://fluxbox-wiki.org/index.php?title=Howto_edit_the_startup_file")

---

### Post by guitar_man on 2009-07-16
> **mac9416 said:**
> Hey, guitar_man (nice nick), I installed Flux the other day and had the exact same problem.
The thing is in Gnome you have a panel applet called NetworkManager applet that takes care of getting you connected to the net. NetworkManager doesn't start by default with Flux, so you have to do it manually by hitting <alt><F2> and typing 
```
nm-applet
```
in the box or by doing the same in a terminal.

You can also set nm-applet to start when Flux does by editing the startup script at ~/.fluxbox/startup and adding the following lines after "# Lines starting with a '#' are ignored."
```
# NetworkManager
nm-applet &
```

See here for [_more on editing the Fluxbox startup script_]("http://fluxbox-wiki.org/index.php?title=Howto_edit_the_startup_file")



Thanks for the help...I already connected and did the same process by running nm-applet on the terminal...

There is another problem I cant control the volume on flux

---

### Post by mac9416 on 2009-07-16
LOL, that's the other problem I had. Are we addicted to Gnome panel applets or what?
I couldn't find a good panel applet, but alsamixer is a good text-based program that does fine for me. Go to the channel you want to control, then use the arrow keys to turn it up/down. Click "m" to mute/unmute a channel.

---

### Post by guitar_man on 2009-07-16
I tried this on the startup and it didn't work..:lolflag: 

> 
# Volume
mixer_applet2 &

---

