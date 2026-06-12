---
title: "can someone recommend a music playing prog with hotkeys"
date: 2006-06-07
forum: Multimedia &amp; Video
---

### Post by syxbit on 2006-06-07
i've just recently switched over from WinXP \\:D/ 
i loved Winamp on there.
i've been using RythymnBox here, and i like it, but the shortcut keys only work when it's focused.
I like having the programin the taskbar (or whatever it's called in linux) and out of the way.

any ideas ?
thanks

---

### Post by BitTorrentBuddha on 2006-06-07
If you don't mind doing some extra work, you can just configure your own using the media player's command's options with xbindkeys. To do that: ```
sudo aptitude install xbindkeys xbindkeys-conf
xbindkeys
xbindkeys-conf
```
There will be a gui, the commands for rhythmbox are:
rythmbox --play-pause
rythmbox --pause
rythmbox --play
rythmbox --previous
rythmbox --next

For more commands, try ```
rhythmbox -?
``` 
map them as you see fit, and Good Luck :)
After you're done, make sure to add xbindkeys to start-up programs (System -> Preferences -> Sessions -> Startup Programs)

---

### Post by syxbit on 2006-06-07
(System -> Preferences -> Sessions -> Startup Programs)
is that where all startup programs happen ?
that's cool, i'd been wondering about that.
even basic things like that (that i know in windows) i don't know in Ubuntu

---

### Post by asc on 2006-06-08
apt-get install xmms gxmms-xmms

Then add the Gnome applet to your panel and launch XMMS. If you use Winamp XMMS will be very familliar.

---

### Post by bskov on 2006-06-08
Xbindkeys is not a must to make shortcutkeys.... 

I set up some of my mediakeys, on my mx3100 desktop, with the build in keyboard shortcuts app. 
go to:  

system -> preferences -> Keybord shortcuts 
(not sure of the spelling (in danish it is: System -> Instillinger -> Tastaturgenveje))

and make the keys the way you like them.

I made a "play/pause" button, a "next" and "prev" button, a "stop" button. And a small button named "media" brings up the rythmbox   ;)

they all work when the app isn't in focus or when it is minimized to sys.tray.

it wasn't all the buttons on my keybord that was recognised but I got what I needed.

---

### Post by syxbit on 2006-06-08
thanks for the tips guys
i tried the player you recommended XMMS, but didn't seem too feature filled.
i like having it show my music library, like winamp, and be able to browse by artists etc..
i kinda like rythymnbox. It's not as flashy as winamp, and the GUI looks kinda basic, but it seems just as capable.
thanks for the tip on
system -> preferences -> Keybord shortcuts
it works like a dream. even better than i thought, as i use the media buttons on my laptops.
I have a question though. aren't the keyboard shortcuts i set up supposed to be universal ?
they work fine with Rythymnbox, but they didn't work with XMMS.
would they work in other programs
is this just a problem with XMMS, or does it have something to do with XMMS not being installed by default in Ubuntu.
just curious

---

### Post by dmalinovsky on 2006-06-14
You can use Amarok as well.  It supports hotkeys without any additional programs required and has very complete feature list.

---

### Post by MarcDM on 2006-06-27
I'm sure you probably already got it working, but have you looked at 

mpd and gmpc together? I've been using them since Warty and gmpc works with the  media keys on all my logitech keyboards.

Also, take a look at 
System -> Preferences -> Keyboard Shortcuts

In order to set the key-bindings for the keyb.

---

