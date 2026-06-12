---
title: "Setting up xorg.conf"
date: 2009-06-14
forum: Multimedia Software
---

### Post by M'Hael on 2009-06-14
ATI Radeon X300
Ubuntu 8.10 (Intrepid Ibex)
CRT 17" VGA monitor
CRT TV with composite in

I have it working in xrandr already. Keep reading...

I'm new to linux and ubuntu. I'm planning on (hopefully) putting together a cheap htpc and running a lightweight linux distro on it with XBMC, and it's the perfect opportunity for me to start 'learning linux' as I've wanted to for a while. I don't need HD. This is so I can play movies and music directly to the stereo and use the slightly better TV, rather than having to listen to music through headphones, or continuously burn to disc.
At the moment I'm just doing a trial run, but the final setup will be essentially the same: video out to TV using an S-video -> composite cable as I am with the TV attached to this PC or just composite out.

After much reading and mucking around I've managed to stumble my way to getting an acceptable output on my TV, with which I can use XBMC using a clone mode of my Monitor, like so:

xrandr --verbose straight after logging in:[COLOR=Blue] **[http://pastebin.com/m71b9d8f8](http://pastebin.com/m71b9d8f8)**[/COLOR]
Method to setup screens: **[COLOR=Blue][http://pastebin.com/f113a800f](http://pastebin.com/f113a800f)[/COLOR]**
xrandr --verbose afterwards: **[COLOR=Blue][http://pastebin.com/m341b3bd5](http://pastebin.com/m341b3bd5)[/COLOR]**

Once it's set up, if I change the resolution in xbmc just using test resolution but don't keep the change permanently, when I quit xbmc then run it again without resetting xrandr settings to the way I had it, xbmc will (sometimes?) crash on opening or once running after scrolling down the main menu too fast or maybe just too fast past the 'scripts' menu item (I haven't narrowed it down and don't plan on continually resetting to do so), and ubuntu does not respond to ctrl+alt+f3 to bring up a terminal, or the power button on the front and so I have to reset.


[LIST]
[*]It is necessary for me to use refresh rates of either 60Hz or 72.2 Hz on the monitor or the output is off centre, or flattened or shrunk etc. The refresh rate makes no difference to the TV so far as I can tell.
[*]I believe only 800x600 resolution is currently supported to TV out by the opensource drivers.
[*]If I try and use 1024x768 on the monitor and clone to the TV I just get an 800x600 cropped image on the TV of the output on my monitor. Also It's simplest to have XBMC output fullscreen correctly on clone so that is why I've gone with clone as opposed to making a large desktop.
[*]I attempted to use Powerstrip on XP to use my resolution settings from there as one guide suggested but was thrown an error. (Yes I made sure res was 800x600)
[*]This TV can handle NTSC and Pal, but I'm not sure about the other older (but better) TV I'll be using with the HTPC, and all the TV stations here are Pal, so better safe than sorry.
[/LIST]
Also, I've installed all updates as I was told to by the update manager.

I'd like to setup my configuration to be permanent with xorg.conf, but am not sure how and at the moment would prefer to just be guided than muscle my way through manuals. Any more info you need just ask.

Thanks.

---

### Post by M'Hael on 2009-06-15
24 Hours? Time for bump.

---

