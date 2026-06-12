---
title: "VNC issue - X11vnc vnc4server libxtst-dev"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by dustinr on 2012-07-18
Hello Forum,

I have had a couple issues with VNC servers. Firstly this is what I am using:

OS - Ubuntu 10.10
kernel - 2.6.35.14-custom
CPU - intel G620 @ 2.6gz
GPU - intel sandy bridge
RAM - 4 gbs

SUMMARY:
after time I cant connect to vnc /
after time I cant control mouse clicks, i can only move cursor

History:

I used to use tightvnc-java, tightvncserver, vino, libgtk-vnc-1.0-0, and vinagre. I would use these VNC services to help me connect remotely. It works for me, but on one machine I have a hard time connecting to it. ( I have to wait up to an hour for the password prompt to come. )

Because of this huge wait and the unreliable nature I have noticed ( plus everyone says vino is buggy ) I decided to explore alternatives.

I uninstalled the above programs. ( tightvnc-java, tightvncserver, vino, libgtk-vnc-1.0-0, and vinagre ).

Then I INSTALLED, X11vnc, vnc4server, gnome-core, xtightvncviewer, tsclient, autocutsel.

ISSUE:

The latest change with X11vnc worked well for me for 12 days, then today I ran across not being able to control  the display.

SYMPTOMS: 

I could connect to the VNC just fine and quickly. Once I am connected I could not send any mouse events or keyboard events. With the exception of changing window size by hovering over the border and clicking and dragging to change size. I repeat, I could only send an event in this way. If i clicked the 'X' to close a window it would not click, it would only change the icon when i hovered over it. Notice I could also see the mouse cursor.

For the sake of troubleshooting I did not reboot and turn off any services when i was experiencing this. I DID however go to the physical machine that I couldnt control, and tried to use the touchscreen to navigate. Same story, i could not click buttons but i could see the mouse cursor moving. 

Out of curiosity i pressed ctrl+alt+F8 ( black screen )then ctrl+alt+F7 ( normal screen ). after I did this i could control the computer as I would expect, both physically and remotely. I have yet to recreate this problem. I am currently letting it sit for another 12 days to see what happens.


HELP?:

I did see this at this site, 

[http://www.karlrunge.com/x11vnc/faq.html#faq-missing-xtest](http://www.karlrunge.com/x11vnc/faq.html#faq-missing-xtest)

under the "Q3" they suggested installing libxtst-dev because other wise it is view only mode. This does not explain why i could control it for 12 days, or that i could change window size. 

I followed this guide to set up my x11vnc

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

Has anyone encountered this before? Any suggestions? I dont HAVe to use X11vnc, if someone has a suggestion for a different vnc server / viewer please offer me a guide or link to set it up. Im sure it will be straight forward.

I am really curious why this happened. Even if I go with a different VNC program I would still like to know the reasons behind all of this weirdness.

Thanks in advance!!!

---

### Post by dustinr on 2012-07-18
bump :)

---

### Post by dustinr on 2012-07-19
bump

---

