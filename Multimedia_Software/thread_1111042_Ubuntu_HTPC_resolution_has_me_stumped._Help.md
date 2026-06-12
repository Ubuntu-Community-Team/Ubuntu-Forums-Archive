---
title: "Ubuntu HTPC resolution has me stumped. Help??"
date: 2009-03-30
forum: Multimedia Software
---

### Post by Linoobius on 2009-03-30
Group,

This may be a simple problem so I'll try to keep the back story to a minimum and will gladly provide additional information or configuration details if you need them.

I had been working with Kubuntu and was having issues so I though that going with Ubuntu and getting rid of the KDE 4.1 might help so this is a fresh load of Ubuntu 8.1 with all current updates from the standard repositories. I am using a Pegatron (ATI) 3450 video card with the HDMI connected to a 42" Vizio TV. After the initial OS load on a standard monitor I activiated the ATI catalyst drivers and connected the TV and disconnected the monitor and all was fine. 1920x1080 filled the TV screen to the edges, I installed XBMC and set it's video to 1920x1080(Fullscreen) which worked flawlessly. I was elated, the only glitch seemed to be that I had to killall pulseaudio or XBMC would crash and kill the mouse so no big deal right? Then I reboot and when the system comes back up, the desktop overflows the TV LCD panel at the bottom and right edges. I have to reduce the resolution to 1776x1000 for the desktop to fit on the TV.

I am really not sure even where the problem lies, I don't think it's in the TV as before the reboot everything was hunky-dory and the only settings I can find in the TV are Zoom/Wide which doesn't help and the Horiz and Vert size and position which only moves and changes the existing image i.e. if I shrink the image I don't see more desktop I just start to see black bars at the edges.

Has anyone else experienced a similar problem or know what I might be missing, I've see a lot of discussion on overscan which seems like it might be at the root of my problem but I don't see anything in the TV setup or in the Catalyst Control Center that specifically addresses this. I may just be missing something simple. It works fine at the 1776x1000 resolution and I'll live with that if that's the solution but somehow that doesn't strike me as the right solution, the TV is a 1080p set so I'd think that 1920x1080 would be the right setting on the PC and that there is just something I am missing.

If you have any suggestions or need additional information, just let me know.

Thank you,
Linoobius

---

### Post by Linoobius on 2009-04-01
Never mind, I started fooling around with aticonfig --set-dispattrib=tmds2i,positionX:0 and similar commands and the problem just went away. Go figure. Thanks anyway.

---

