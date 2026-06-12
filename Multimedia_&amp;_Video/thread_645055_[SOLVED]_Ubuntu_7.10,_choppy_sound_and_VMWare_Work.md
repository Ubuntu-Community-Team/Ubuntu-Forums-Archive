---
title: "[SOLVED] Ubuntu 7.10, choppy sound and VMWare Workstation 6"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by vortex0007 on 2007-12-19
So I'm addicted to Apple ITunes and have quite a few songs purchased from ITunes, so as much as I want to dump Windows, I'm stuck until someone can figure out how to play Apple Encoded songs on Linux and dumb it down for people like me.  With that said, to get the most of out Ubuntu, and keep Apple ITunes, I decided the configuration that was right for me was to have the base OS be Ubuntu, then install VMWare Workstation 6 and put Windows XP Pro SP2 in a Virtual machine. 

So I started playing around with Ubuntu and have turned on the Extra Visual Effects to go with my 256MB ATI Radeon x1950 video card that is running with the Linux drivers direct from ATI.

What I'm struggling to now understand is why the audio coming from Itunes running inside of VMWare is almost unbearably choppy when I pretty much do ANYTHING outside of the VM.

Opening an application in Ubuntu causes the audio to chop, scrolling with the mouse's wheel also seems to emphasize the problem, opening a new tab in Firefox causes it, I mean basically every thing I need to do day to day on Ubuntu causes this to happen. 

What I'm confused about is changing the graphic options might have affected this sound output. 

I thought - well maybe it's hardware resources. The desktop is a Dell OptiPlex GX620 with an add-on ATI Radeon X1950 Pro 256MB card. With a Pentium D dual-core CPU with 3GIG of RAM and a 256MB video card with SATA hard drives I thought I wouldn't have this kind of problem. 

With my limited knowledge of Ubuntu, I found System Monitor and I'm observing  that scrolling through menus causes a spike in the first core processor that hits around 90% and then drops as soon as I stop scrolling. 

The more I dig into this, the choppy sounds seems to happen when I'm doing any of the following outside of the VM:

maximize/minimize a window
use an application scroll bar 
attempt to open a menu with the scroll bar

:confused: I'm a bit lost on where to go from here. Anyone have any ideas on how I can solve this?

---

### Post by vortex0007 on 2008-01-04
I've given up and am going to dump ITunes so this will no longer be a problem.

---

### Post by johnpinochet on 2008-01-05
This is sad.  I was hoping to see a solution to this problem.

---

### Post by linuxvacuum on 2008-01-05
Have you tried the excellent [[COLOR="Blue"]**VirtualBox**[/COLOR]]("http://www.virtualbox.org/") ?

---

