---
title: "Problems with dual screen ati setup."
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by EnterDaMatrix on 2007-01-20
My setup goes like this:
Ubuntu Edgy 6.10
ATI Radeon 9500 Pro (agp)

Main monitor: CRT at 1280x1024
2nd monitor: LCD at 1024x768

Driver: fglrx configured with aticonfig for dual-head.

What works:
1. Two screens side to side with different resolutions.
2. I can drag the mouse between the two.
3. I can have different applications open in each.
4. OpenGL acceleration in both.

What doesn't work:
1. Dragging windows between the two.
2. Having Firefox (or any one app) open in both at the same time.
3. The tray on my second monitor. Wine creates a little tray icon that floats around, but Gaim/aMSN/etc don't create any.
4. Using gnome-main-menu on the 2nd display opens the menu on the 1st on only. For instance clicking computer on screen 2 brings up the menu as if I clicked on screen 1. Regular Ubuntu menu works fine.

Is there anyway that I can fix these problems while keeping what is working. If buying an Nvidia card will work, I'll do it, but I need confirmation that all of those things will work (AIGLX would be a bonus too). Anyway I had none of these problems with Windows or Mac OSX86.

I realize that these are probably mainly ATI's fault (except for the tray thing).

I could tolerate the tray problem if the tray showed up on the first monitor and I still had the windows open on the second one.

---

### Post by EnterDaMatrix on 2007-01-20
My problem didn't disappear on its own... :-(

---

### Post by EnterDaMatrix on 2007-01-21
Sigh.. Did I post this somewhere wrong or something? All the other threads get replies... Whatever I'll go switch to Suse and recommend every prospective linux user out there to stay far away from Ubuntu. Sad cause in every other way it's been better.

---

### Post by Dietmar on 2007-01-24
With dual head dragging windows between the screens doesn't work. I'm using bigdesktop an there it works. But with different resolution on both screens I've a offset of the cursor if moving from the bigger to the smaller screen.

How to solve the other problems I've no solution.

---

### Post by roongpatoong on 2007-01-26
> **EnterDaMatrix said:**
> My setup goes like this:
Ubuntu Edgy 6.10
ATI Radeon 9500 Pro (agp)

Main monitor: CRT at 1280x1024
2nd monitor: LCD at 1024x768

Driver: fglrx configured with aticonfig for dual-head.

What works:
1. Two screens side to side with different resolutions.
2. I can drag the mouse between the two.
3. I can have different applications open in each.
4. OpenGL acceleration in both.

Firstly, you just need to have a little bit of patience. It is not everyone that runs Ubuntu, it is even less of them that have an ATI card, not many of them have dual monitors, and only a tiny number of people give a sh!t about getting it setup :)

I am on of the few who is trying the same thing as you. I have some answers below but I am wondering (for #4 above) - how did you test that you had OpenGL acceleration in both?

If I try to run fgl_glxgears it dies on me. fglrxinfo also tells me that I don't have ati 3D acceleration.

If you are feeling generous - please post your working xorg.conf and the test results of your 3D accel. tests.

> What doesn't work:
1. Dragging windows between the two.
2. Having Firefox (or any one app) open in both at the same time.
3. The tray on my second monitor. Wine creates a little tray icon that floats around, but Gaim/aMSN/etc don't create any.
4. Using gnome-main-menu on the 2nd display opens the menu on the 1st on only. For instance clicking computer on screen 2 brings up the menu as if I clicked on screen 1. Regular Ubuntu menu works fine.

1. This is not supported with a 'dual-head' setup. You need to go for the 'Big Desktop' setup to get this functionality. See my xorg.conf attached for a working config.
2. The only way to get this working would be to somehow setup two instance of the binary 'firefox' and run them as two separate processes. Maybe create a hardlink called firefox2?
3. Check my xorg.conf for the line ...
Option      "DesktopSetup" "horizontal,reverse"
This allows you to switch with monitor is the primary one - should allow your popup to 'popup' on the secondary monitor.
4. No explanation for the gnome menu strangeness - maybe just reconfigure your ubuntu menu and add extra apps to it?

Good luck with playing around and if you need a mega quick way to backup and restore different linux distros on the same machine - boot with systemrescuecd and run partimage!!

pAntZ

---

### Post by EnterDaMatrix on 2007-02-04
Cool, um well here:

Dietmar:
I'd tried big desktop, but the problem was that maximizing anything would stretch between both monitors. Is there a way to set it so maximizing only does so on the current monitor, but you can still drag windows?

roongpatoong:

1. Same as dietmar I suppose.

2. I've been using opera on the 2nd monitor and that works alright I suppose.

3. Im not sure what you're referring to. The popup comes on the 2nd monitor, it's just meant to be a tray icon. If I open utorrent on the main monitor, it puts the icon up in the tray like it's supposed to. If I run utorrent on secondary monitor, then it makes a little window. Also the other apps don't even have tray icons on the 2nd monitor.

4. I've just been using the regular menu on the 2nd monitor. Not a huge issue.

---

