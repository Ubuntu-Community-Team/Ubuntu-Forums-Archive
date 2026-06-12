---
title: "Less colors visible on the screen after upgrading?"
date: 2010-11-14
forum: Multimedia Software
---

### Post by Starlight on 2010-11-14
Hi!

I've just upgraded to Kubuntu 10.10 recently, and everything's working well, except that the screen seems to display less colors than it used to. It's very noticeable when looking at smooth gradients, since there are no smooth gradients anymore.

I'm using a laptop with a Radeon HD 5650 video card. The drivers seem to be working well, since I can run a 3D game like Nexuiz without any problems. The lack of colors isn't even very noticeable when playing games, but I can see it clearly in KDE... for example, the window background gradient isn't really a gradient now, just a few different shades of gray next to each other... I've looked around in KDE display settings and ATI settings, but there's absolutely nothing about the number of displayed colors there... o_O Does anyone have any idea what's wrong?

---

### Post by Starlight on 2010-11-15
*pokes this thread with a poking stick*

I always seem to have weird problems with my computer that no one knows how to fix :shock:

---

### Post by Starlight on 2010-11-16
*bumps this thread*

Here's a portrait of me contemplating the fact that no one has any idea what's wrong with my color settings on my computer:

[IMG]http://i593.photobucket.com/albums/tt18/Indiemann/fffuuu.png[/IMG]

---

### Post by Starlight on 2010-11-18
Meep meep!

This road runner is also very curious why my computer screen doesn't seem to display the full color depth after the upgrade. Will anyone make the road runner happy by solving this mystery? I've checked and the actual color depth settings appear to be right. But the screen just doesn't display the colors properly.

[IMG]http://persianrap.ucoz.com/road-runner.jpg[/IMG]

---

### Post by Starlight on 2010-11-19
Moooo.

(that means "bump" in cow language)

---

### Post by Starlight on 2010-11-27
Apparently,the problem is fixed when I use the open source Radeon driver instead of the official one. That makes it the second strange and unexplained problem I have with my video card and the official drivers (the first one is here [http://ubuntuforums.org/showthread.php?t=1567324](http://ubuntuforums.org/showthread.php?t=1567324) )

I think the question that accurately sums up both problems and the fact that no one knows how to fix them is: what the hell?

---

### Post by Starlight on 2010-11-27
Braaaaaaaaaaaaaaains..... (That's what a zombie would probably say after reading this thread. Because zombies aren't really interested in unsolvable video card problems, they prefer to eat brains.)

---

### Post by Starlight on 2010-12-01
[SIZE="1"](LOL I CAN WRITE ANYTHING HERE AND NO ONE WILL EVEN READ IT!!111)[/SIZE]

When switching between the open source and official Radeon drivers, I've also noticed that the boot screen looks a lot better with the open source drivers (with the official ones, it looks like a text-only boot screen with white text on light blue background. It looks cool, though... kind of old school). I've always thought that the drivers are used only in X which doesn't control the boot screen... I guess I was wrong :P

---

### Post by Starlight on 2010-12-04
You, there.

Yes, you, the person reading this at the moment.

Hi! *smiles and waves at you*

---

### Post by Starlight on 2011-01-15
What a weird thread. I think I'll bump it.


I had to go back to using the official ATI drivers, since Spring doesn't work on the open source ones, and I have this strange color problem again.

---

### Post by Starlight on 2011-01-16
*bump*

Yay, second page! My computer must be very unique, if there's no one who ever had such a problem...

---

### Post by Starlight on 2011-01-17
Somewhere in the world there's a person who knows exactly why the colors on my screen aren't displayed correctly when using the official ATI driver, and how to fix it. That person will probably never see this thread.

---

### Post by Starlight on 2011-01-18
When you gaze long into this thread, the thread also gazes into you.

---

### Post by Starlight on 2011-01-19
I've noticed that the colors sometimes appear correct just after the system boots, but after a few minutes of using it they become wrong.

---

### Post by Starlight on 2011-01-22
*pokes the thread*


if anyone's reading this, say hi! :) Even if you have no idea how to fix this problem

---

### Post by Starlight on 2011-01-23
No one will probably read this, but I've noticed that the weird thing with colors happens after the screen turns off after inactivity. When the screen turns back on, the colors are bad.

---

### Post by Zorael on 2011-01-23
I'm mostly replying for the sake of it now. :3

This sounds like your driver isn't [**dithering**](http://en.wikipedia.org/wiki/Dithering) the way it should. I got this at one point when trying out bleeding-edge builds of the intel driver, and it was promptly fixed after notifying the developers about it. Have you reported it to ATI or the open source radeon crew?

---

### Post by xc3RnbFO8P on 2011-01-23
Did you try to change the resolution of your monitor?

---

### Post by Starlight on 2011-01-23
Yay! Welcome to my thread :D

I can't really change the resolution, because it's a laptop screen with only one native resolution, and I'm using it now. 

As for the drivers, I haven't reported it to ATI, if it's a common problem then someone must have already reported it, I think... But it's strange that it happens only after the screen gets blank after inactivity....

Maybe I'm wrong, but I don't think it's about dithering. When an image is dithered, it appears sort of grainy. When the colors are displayed correctly on my laptop, they are perfectly smooth. But when they aren't displayed correctly, it looks sort of like this: [http://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Dithering_example_undithered_web_palette.png/225px-Dithering_example_undithered_web_palette.png](http://upload.wikimedia.org/wikipedia/commons/thumb/b/be/Dithering_example_undithered_web_palette.png/225px-Dithering_example_undithered_web_palette.png)

And when I take a screenshot of these bad colors, it can't be seen on the screenshot when I open it later when the colors on the screen are right o_O

---

### Post by arpoodle on 2011-01-24
I have a similarly strange issue.

I've got an Nvidia card in my laptop, and am using both the laptop screen and an external LG monitor, connected via HDMI.

Both were working fine until a recent apt-get upgrade, I suspect on Friday. I noticed today that the external monitor is operating at a lower colour depth than the laptop screen, and yet within the monitor settings control panel, both are showing as using the same colour depths.  The monitor has no buttons other than power so I can't play with the colour depth that way.

Any ideas?

---

