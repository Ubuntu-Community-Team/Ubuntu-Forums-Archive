---
title: "TwinView worked, the died after 2 days."
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by PiGeek31415 on 2007-06-19
Alright, this is driving me crazy.

It all started about three days ago, when I decided to migrate from my dell's onboard video to my Nvidia GeForce FX5200 PCI card. The drivers worked fine, but I was only able to use a single screen. I then used [_this_]("http://ubuntuforums.org/showthread.php?t=221174") tutorial to set up TwinView (through the "obsolete" method of copy/pasting options into my xorg.conf file). The twinview setup worked quite well for a couple of days, then suddenly... didn't. One screen would turn off, and the other would have a big desktop (the entire 2560x1024 display) that scrolled to follow my mouse. 

I've gone through that tutorial again, not getting the same results (just one screen comes up). I've used "sudo nvidia-settings"; that gave me 1280x1204 on one screen and 640x480 on the other, with no option to go higher. 

So I manually messed with my xorg.conf file, and managed to get an almost-perfect setup.
The resolutions are correct, and everything looks nice, but the second monitor, the one that gets turned off when there's only a single screen, is displaying an "input not supported" message over the (obviously supported) desktop. I can't get a printscreen of the message, since it's being displayed by the monitor itself.

I'd love to be able to get rid of that stupid box, if at all possible.

Thanks in advance, 
-PiGeek31415

(attached is a copy of my current xorg.conf file, in .txt format)

Edit: Forgot to mention that (1) I'm using Kubuntu Feisty (2) Both monitors are connected to the Nvidia card (wasn't sure if I was clear about that).

---

### Post by Yoooder on 2007-06-19
My advice: restore the backup you should have made before manually editing the xorg.conf file and use nVidia's GUI tool to configure TwinView.  It works pretty well all in all.

The question I have to your current situation is: have you ran any updates?

---

### Post by PiGeek31415 on 2007-06-20
Yeah, I've tried using the GUI after reverting the xorg.conf file. It didn't detect my second screen.

As for updates, "sudo apt-get update" is all I've used.

I plan to just start over with a fresh install of Ubuntu Feisty (I'm getting fed up with the KDE, due to this and other problems).

Thanks for trying, 
-PiGeek31415

---

