---
title: "SSH+VNC=8bit woes"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by gr0undzer0 on 2012-03-05
Setup:
I've got an Ubuntu 11.10 vm guest running on xen cloud platform. I've configured ssh and installed x11vnc. I use ssh forwarding to connect tight vnc to the guest. I currently use the command -safer -localhost -nopw -once - display :0 to prepare the guest and then connect with tight vnc. 
 
 
Problem:
When I connect with tight vnc (tried ultravnc as well) The client connects to my linux box but I get a "preparing initial screen" message with a gray screen. During this time I can tell that the inputs work though because I can watch them on my xen manager locally. So I can move the mouse around and click and such but I can't see the output. AFter playing with the options alot I figured that if i put the color to 8bit the linux desktop is visible but ofcourse looks horrible. This behaviour is the same on both tight vnc and ultra vnc clients. I've tride every setting and and encoding I can think of on the client side but can't get either client to run above 8 bit color. 
 
This is rather frustrating because the xen viewer does not work remotely even if you port forward and I need a remote solution. 
 
I'm going crazy with this problem. Anyone got any ideas?

---

