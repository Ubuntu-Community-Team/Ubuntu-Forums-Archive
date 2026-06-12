---
title: "[SOLVED] Running GMPC on Minimal Ubuntu"
date: 2018-12-03
forum: Multimedia Software
---

### Post by qwin2 on 2018-12-03
Hi all,
I'm new to Linux, Ubuntu and command line entry.

I have an Odroid C2 (SBC) which I am trying to turn into a networked music streamer.

To this end, I have loaded the C2 with minimal Ubuntu OS, that has no GUI or desk top utilities and installed MPD which launches successfully at boot up.

I will eventually be controlling MPD from a networked tablet, but for the time being want to run GMPC on the same device as MPD, this device also has a small amount of music stored on it for test purposes.

Is this combination compatible ?

I have been led to believe that GMPC will install part of the gnome desktop, enough to run GMPC on minimal Ubuntu, without the need for a full GUI desktop/utilities.

I have installed GMPC on the C2, but when I try and launch it get this error message:

** (gmpc:718):[COLOR=#ff0000] ERROR[/COLOR] **: [COLOR=#008080]15:58:46:271[/COLOR]: Failed to parse commandline options: Cannot open display: Trace/breakpoint trap

1). Is what I'm trying to do even possible ? - Run GMPC on minimal Ubuntu ?

2). If it is possible, any tips on how to configure things to work ?

---

### Post by Holger_Gehrke on 2018-12-06
I think it's not only possible, but quite probable that you've already done it. Your mistake lies in assuming that gmpc will start the GUI. You have to start it and then start gmpc. Check whether /usr/bin/startx exist and execute that if it does. That should start the GUI (and hopefully at least a window manager ...)

Holger

PS. there also is a non-graphical mpd client if you just want to test the server. You can find it in the package 'mpc'.

---

### Post by qwin2 on 2018-12-07
> **Holger_Gehrke said:**
> I think it's not only possible, but quite probable that you've already done it. Your mistake lies in assuming that gmpc will start the GUI. You have to start it and then start gmpc. Check whether /usr/bin/startx exist and execute that if it does. That should start the GUI (and hopefully at least a window manager ...)

Holger

PS. there also is a non-graphical mpd client if you just want to test the server. You can find it in the package 'mpc'.

Thanks for the response, /usr/bin/startx does not exist.

I considered using MPC, but I'm now taking the easy route and loading a graphical client on my networked Windows10 laptop to control MPD for testing purposes.

---

### Post by qwin2 on 2018-12-11
I got Cantata (MPD Graphical Client) loaded on to my Windows 10 Laptop.
Configured it and it sees the 10 track library I set up on my SBC across the network.
When I play a track from Cantata/Laptop sound comes from the HDMI monitor plugged into the SBC, so that is a great start.

---

