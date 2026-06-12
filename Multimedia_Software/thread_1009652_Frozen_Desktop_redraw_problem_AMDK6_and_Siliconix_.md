---
title: "Frozen Desktop redraw problem AMDK6 and Siliconix Chipset Suggestions?"
date: 2008-12-12
forum: Multimedia Software
---

### Post by bluemax7 on 2008-12-12
I have a WinMax motherboard that is running an on the board siliconix
VGA driver chip.. 

every now and then (and launching an Xterm especially sometimes upsets it)

The windows show up, but don't redraw properly..
especially if you move them around..
and/or if you try to scroll in a window that has text...
The text only at the bottom updates...

If you move the mouse around.. sections of the window 
that the mouse goes over tend to redraw..

I looked in the system log, and the Siliconix driver alerts me to 
a possible problem with a shared frame buffer.. and that perhaps
video play back (as in video media) may have a problem.

But there is no logging of say a frame buffer overflow.. or 
any indication that there has been a trap on a hardware error..

So far this is my problem..

has anybody seen this? 

I have adjusted all sorts of settings in my Bios..
shared AGP.. ect ect..
I reduced the resolution .. 
and the refresh rate is as low as it can get..

Anyone ever seen this?

I don't really want to get a video card, which will proabably solve the problem.. I want to fix it so it just works..

anybody? :confused:

---

