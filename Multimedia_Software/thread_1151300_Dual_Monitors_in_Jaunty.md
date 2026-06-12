---
title: "Dual Monitors in Jaunty"
date: 2009-05-06
forum: Multimedia Software
---

### Post by Mirge on 2009-05-06
I've searched both here & on Google, but was unable to find a working solution...

I have a Radeon HD 2400 XT video card, 2 monitors plugged into it...

basically what I'm trying to make happen is "Extend windows onto this desktop" functionality from Windows XP/Vista into Ubuntu 9.04.

I can't figure it out... I looked into Xinerama, but it's grayed out! Says I only have one desktop enabled. Please help!

---

### Post by Mirge on 2009-05-06
If I uncheck "Mirror" setting in Display (System -> Preferences -> Display)... it's almost what I want. What I would like is two actual SEPARATE desktops... so that each monitor has its own taskbar and so if I maximize a window.. it maximizes on that screen, not across BOTH screens.

Any help?

Ordered an nVidia 8800 GT... hopefully be here this week, but not sure. Anyway, prefer a solution that'll stay working once I swap out video cards, but if I need to re-do it after the swap, that's fine too.

---

### Post by Mirge on 2009-05-07
Anybody have any ideas?

---

### Post by Pantalaimon on 2009-05-07
I used NVIDIA X Server.

I have no idea if that will work for you. but it managed to for me.

The config I selected is twinview

---

### Post by Mirge on 2009-05-07
Will look into it... if nothing else, it'll probably work when my 8800 GT comes in. Thanks!

Any others?

---

### Post by Mirge on 2009-05-07
Well I had to re-install, got it the way I want it again..... using the default open source ATi driver that came with Ubuntu 9.04.

I went to System -> Preferences -> Display... UNCHECKED "Mirror". Now my primary (left) monitor is on, and is fine... and my right monitor is fine heh.

Not real sure wtf to make of that... but it works! My only complaint is that I don't have a taskbar (or panel I guess) on the secondary monitor. Any idea how to get one over there?

---

### Post by Kareeser on 2009-05-07
Correct, "TwinView" will work with all NVIDIA cards.

Have you tried loading ATi drivers from the ATi website? It might come with a utility to help you out.

---

### Post by Mirge on 2009-05-07
Yeah, I tried ATi drivers, but if I do that... I can't maximize a window and it appear maximized only on that monitor. Using the open source driver that came with Ubuntu, I can do that.

I'm just gonna cope with this for now until the nVidia 8800GT comes in... apparently just shipped today, not ordering from AacendTech.us again :P. I paid for the card Monday... took them too long to ship it! :P

---

### Post by Longinus00 on 2009-05-07
> **Mirge said:**
> Well I had to re-install, got it the way I want it again..... using the default open source ATi driver that came with Ubuntu 9.04.

I went to System -> Preferences -> Display... UNCHECKED "Mirror". Now my primary (left) monitor is on, and is fine... and my right monitor is fine heh.

Not real sure wtf to make of that... but it works! My only complaint is that I don't have a taskbar (or panel I guess) on the secondary monitor. Any idea how to get one over there?

If you want to add a new panel, just right click on an existing one and select "new panel". Then you can hold the ALT key and drag it where ever you want. I actually find the open source ATI drivers in jaunty to be the less buggy (multi monitor wise) than any of the other proprietary drivers so good luck with NVIDIA.

---

### Post by Mirge on 2009-05-08
> **Longinus00 said:**
> If you want to add a new panel, just right click on an existing one and select "new panel". Then you can hold the ALT key and drag it where ever you want. I actually find the open source ATI drivers in jaunty to be the less buggy (multi monitor wise) than any of the other proprietary drivers so good luck with NVIDIA.

REALLY not sure why I didn't think of that.......... that's definitely better, but not quite perfect. Ideally, I would like for (for example) FileZilla FTP client in taskbar (panel) to appear on the right monitor's taskbar since the window is over there. Any way to accomplish that?

And I agree 100% with the Jaunty ATI drivers comment... it's been the best by far of all I've tried heh.

---

### Post by Mirge on 2009-05-08
Actually, I added the panel like you said... then I right-clicked, chose "Add to Panel", and selected "Window List" (Switch between open windows using buttons).

Then Ubuntu just sort of figured it out on its own what should go where, PERFECTLY.

Saving the 8800 GT for the Vista box... my setup is now exactly how I want it, and I don't want to mess with that haha.

EDIT: In all of my excitement, I forgot to say thanks! Thank you Longinus... your help is much appreciated!

---

### Post by btnfrm on 2009-05-08
To configure 2 monitors with an Ati card and Ati repository driver in Jaunty, the best I've done so far is with xrandr.
In a terminal, type 
xrandr
to display the possible resolutions of your 2 monitors.
Then, the key is to change one by one each monitor. What worked for me for a dual head config (1 LCD, 1 external) with separate desktops :
1.) add the resolution of your 1st monitor : 
xrandr --addmode VGA-0 1280x1024
2.) Change the resolution of you 1st monitor :
xrandr --output VGA-0 --mode 1280x1024
3.) do the same for your second monitor :
xrandr --addmode LVDS 1024x768
xrandr --output LVDS --mode 1280x800
4.) indicate the placement
xrandr --output VGA-0 --left-of LVDS
If it doesn't work, change first the virtual desktop size as it is displayed by "xrandr". 

I can now move windows or applications between the two desktops. I can watch VLC full screen on the two monitors or move the window between desktops.
If you add a panel and a task bar applet on you 2nd monitor, the applications minimized on your 2nd monitor would be tasked in the 2nd monitor taskbar.
There are a few problems : for example, I can't add / move icons on one of the desktop and on the other desktop, but it's very easy to change the settings on the fly with xrandr or to add it in scripts.

---

### Post by Mirge on 2009-05-08
> **btnfrm said:**
> To configure 2 monitors with an Ati card and Ati repository driver in Jaunty, the best I've done so far is with xrandr.
In a terminal, type 
xrandr
to display the possible resolutions of your 2 monitors.
Then, the key is to change one by one each monitor. What worked for me for a dual head config (1 LCD, 1 external) with separate desktops :
1.) add the resolution of your 1st monitor : 
xrandr --addmode VGA-0 1280x1024
2.) Change the resolution of you 1st monitor :
xrandr --output VGA-0 --mode 1280x1024
3.) do the same for your second monitor :
xrandr --addmode LVDS 1024x768
xrandr --output LVDS --mode 1280x800
4.) indicate the placement
xrandr --output VGA-0 --left-of LVDS
If it doesn't work, change first the virtual desktop size as it is displayed by "xrandr". 

I can now move windows or applications between the two desktops. I can watch VLC full screen on the two monitors or move the window between desktops.
If you add a panel and a task bar applet on you 2nd monitor, the applications minimized on your 2nd monitor would be tasked in the 2nd monitor taskbar.
There are a few problems : for example, I can't add / move icons on one of the desktop and on the other desktop, but it's very easy to change the settings on the fly with xrandr or to add it in scripts.

I can do all of the above with default Ubuntu ATi open source driver that came with the installation, simply by adding a 2nd taskbar for the secondary monitor. I tried different ATi drivers (proprietary & open source)... the one that ships with Ubuntu 9.04 turned out to be the absolute best for me.

When I used the driver from ATi's website... latest for my card, sometimes I'd see black 'patches' I guess you could say... in various applications. MOST common in firefox, but it could happen in any window. And I'd see black 'borders' sometimes when minimizing for about half a second.... I guess it was just laggy in general. I'm extremely satisfied right now. MIGHT go ahead & try putting the 8800 GT in here and running a dual monitor setup with that using the same technique or similar as what I did for this setup.

---

### Post by Mirge on 2009-05-10
2 more days & the 8800 GT comes in woohoo :P. Having a couple issues with the ATI setup, so I'm definitely going to try the 8800GT.

---

### Post by Longinus00 on 2009-05-12
> **Mirge said:**
> 2 more days & the 8800 GT comes in woohoo :P. Having a couple issues with the ATI setup, so I'm definitely going to try the 8800GT.

What's currently wrong with the ATI setup?

---

### Post by Mirge on 2009-05-12
Logging out (or rebooting) causes the screens to Mirror again. When I un-mirror, I can't move a window ALL the way over to the right screen... I'd say the far-right 200-250 pixels are blocked off, like the window just stops moving that direction.

I can get around that by mirroring them again, then saying "Restore previous configuration" when it asks if I want to keep it again. That fixes that issue, until the next logout/reboot.

---

### Post by Mirge on 2009-05-13
Well I'm still waiting for the video card to come in... UPS tracking status says "Out for delivery" since 6:20am........ it's now past midnight..

---

### Post by Longinus00 on 2009-05-13
> **Mirge said:**
> Logging out (or rebooting) causes the screens to Mirror again. When I un-mirror, I can't move a window ALL the way over to the right screen... I'd say the far-right 200-250 pixels are blocked off, like the window just stops moving that direction.

I can get around that by mirroring them again, then saying "Restore previous configuration" when it asks if I want to keep it again. That fixes that issue, until the next logout/reboot.

I don't know why that might be happening. Maybe you still have some cruft left over from when you tried installing ATI's drivers? Try using an ubuntu live cd and enable dual desktops there. Log out and log back in (it will auto log in if you log back out) and check to see if you're still getting the same issue there.

---

### Post by Mirge on 2009-05-13
> **Longinus00 said:**
> I don't know why that might be happening. Maybe you still have some cruft left over from when you tried installing ATI's drivers? Try using an ubuntu live cd and enable dual desktops there. Log out and log back in (it will auto log in if you log back out) and check to see if you're still getting the same issue there.

If I read that post before I installed my 8800GT I would have, but the new card is in already... TwinView, log out, reboot, etc... keeps settings (though I HAD to save config file to my home folder, then in terminal sudo cp the file over to /etc/X11 after backing up my existing xorg.conf)........ works friggin perfectly. Used proprietary driver 180 as opposed to 173... that Ubuntu listed under Hardware Drivers. TwinView is working awesome, everything stays the same when I log out or reboot (tested extensively). I have compiz running smoother than a baby's bottom with dual monitors. I couldn't be happier. LONG LIVE UBUNTU (and nVidia).

---

### Post by Mirge on 2009-05-14
Ok, I had the DREADED freeze... less than an hour after getting it all set up. Switched to driver 173... been a few hours now, great performance still & no freezing. Just a heads up for those switching to a similar card.. use 173.

---

### Post by humphreybc on 2009-09-23
Hi could anyone help with my problem here?

[http://ubuntuforums.org/showthread.php?t=1273242](http://ubuntuforums.org/showthread.php?t=1273242)

---

