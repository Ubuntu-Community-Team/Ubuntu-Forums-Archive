---
title: "KVM Switch - Switching Monitors in Ubuntu"
date: 2009-05-14
forum: Multimedia Software
---

### Post by duwanis on 2009-05-14
OK. I know this is probably a longer description than it should be, but I'd like to make sure my problem is understood :)

I have two computers; a Desktop that runs Windows Vista (used for Gaming), and a Laptop (HP Pavilion dv6500) running Jaunty Jackalope, that I use for work.

I work from home, and since one laptop is mostly for work, and the other mostly for play, I rarely use both computers at once.
Sadly, the best screen resolution I can get on my laptop natively is 1280x800... which is kind of a cramped bit of space to be trying to work in, especially when my desktops CRT monitor can handle 1600x1200.

A solution! (or so I thought) - I would go and get a KVM switch that I could treat like a docking station for the laptop - plug it in, switch my keyboard/monitor/mouse over from the desktop, and be able to work with a nice large resolution.

Sadly, it doesn't appear to be that easy.

I'm using the restricted nvidia drivers for the laptops graphics card.

*Ideally*, what I'd like to see happen, is that when I use the laptops video toggle switch (Fn-F4 in this case) to switch from the laptops built-in LCD screen to the VGA adapter on the side - the resolution of my desktop automatically adjusts to a CRT-friendly value (1600x1200, 1400x1050, 1280x1024, I'm really not picky at this point. Anything larger than 1280x800 would be dandy).
Then, if I wanted to take the laptop into the living room and away from my desktop, I could cycle back through video input modes until I arrived at the built-in LCD, which would (in a perfect world) automatically adjust everything back down to 1280x800.

The best I've been able to get with my setup is that the nvidia drivers will leave the X screen size at 1280x800, and treat my CRT as a 1024x768 monitor. I can go into nvidia-settings and manually fix it, but then if I try to switch back to the LCD screen, it has a similar effect - its screen size is 1280x800, but my desktop is sized to 1400x1050.

I've tried searching around, but everyone seems concerned with running 2 monitors at once. I don't want to run 2 monitors at once. I want to 'dock' my laptop and simply switch between monitors as I see fit.
I imagine this has to be possible, and I feel like I've been getting closer, but I'm honestly at my wits end :)

SO. All that to say. I'd be glad to provide the current state of my xorg.conf file, but it's been changed so many ways and written over by nvidia-settings so many times now that I'm certain it's nowhere near ideal. What I'm really hoping is that somebody out there has done what I'm trying to do, or can otherwise provide a bolt of insight that will keep me from staying up all night switching mode lines around.

---

### Post by duwanis on 2009-05-15
No love? :(

I'd like to think this is similar to the problem any nvidia user with a docking station would face, if that helps... I don't think the KVM is part of the issue at all, it just happens to be the mechanism by which I switch monitors.

---

