---
title: "X server randomly reboots / crashes instantly"
date: 2005-12-26
forum: Multimedia &amp; Video
---

### Post by Ninjagecko on 2005-12-26
Hello.

Might anyone please help?

My X server periodically, instantly reboots with no warning whatsoever. I can't find anything meaningful when looking through logs (if someone could please hint at what to look for exactly... no SIGTERM 11s or anything like some other threads).

By the way, I am using the X composite manager, which may be related -- yes, I know it's highly unstable and probably the cause of this, but my computer ought to give me feedback on what's the matter instead of randomly restarting X.

Also, I've had this problem on both Gnome and KDE.

Thanks for the input.

---

### Post by 23meg on 2005-12-26
Please post your Xorg.0.log file, information on your video hardware, and your composite settings.

---

### Post by Ninjagecko on 2005-12-26
Thanks for the assistance.

* Last 300 lines of Xorg log attached.

* This is my graphics card info from *lspci*:
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go 5200] (rev a1)

(Please tell me if there's another source of info you'd like me to provide.)

* Composite manager settings for default KDE composite manager:
> 
[X] Use translucency/shadows

-- Translucency --

[ ] Active windows:
[X] Inactive windows: 53%
[X] Moving windows: 75%
[X] Dock windows: 80%

[ ] Treat 'keep above' windows as active ones
[ ] Disable ARGB windows (ignores window alpha maps, fixes gtk1 apps.

-- Shadows --

Active window size: 12
Inactive window size: 6
Dock window size: 6
Vertical offset: 81%
Horizontal offset: 60%

Shadow color: [rgb value: black]

[ ] Remove shadows on move
[ ] Remove shadows on resize

-- Effects --

[X] Fade-in windows (including popups)
[X] Fade between opacity changes

Fade-in speed: 48
Fade-out speed: 17

(It's very odd, things started crashing more/less when I fiddled the composite manager settings to say, increase the spacing of shadows below windows by just a few pixels...)


Miscellaneous:

- X also crashes sometimes if I load OpenGL, e.g. the screensaver preview.
- Also, sometimes Xorg runs up to ~95% CPU and I have no idea why... perhaps the right solution is just to disable features of composite until it works, or find a way to disable composite on the desktop when OpenGL is launched... :???:


Thanks.

---

### Post by Ninjagecko on 2005-12-26
On second thought, this probably isn't a problem with the composite manager. I turned off the shadows/translucency option and X still crashed.

---

### Post by Ninjagecko on 2005-12-26
It also happens randomly while I'm doing things; the screensaver or power saving doesn't have to kick in.

---

### Post by 23meg on 2005-12-26
Please post your xorg.conf file, and if possible, your whole Xorg.0.log as well.

---

### Post by Ninjagecko on 2005-12-26
Uploaded:
* xorg.conf
* Xorg logs

I also note that after I turned the composite manager, I only crashed out of X windows once, and haven't crashed since then. And my laptop battery dock icon has appeared again... :???: I haven't tried letting the computer go to sleep yet though...

Thanks again for any insight.

---

### Post by 23meg on 2005-12-26
I suggest you try the following, one by one:

- Set your color depth to 24
- Remove the "RenderAccel" line
- Comment out the DRI section entirely
- Try the "NvAGP" option in the "Device" section with parameters from "0" to "3"

If they all fail, post your problem with a bug report file (created with the bug reporter script that the driver package installs), your Xorg.0.log and your xorg.conf files to the Linux forum at [www.nvnews.net](www.nvnews.net) .

---

### Post by Ninjagecko on 2005-12-27
[QUOTE=23meg]I suggest you try the following, one by one:

- Set your color depth to 24
- Remove the "RenderAccel" line
- Comment out the DRI section entirely
- Try the "NvAGP" option in the "Device" section with parameters from "0" to "3"

If they all fail, post your problem with a bug report file (created with the bug reporter script that the driver package installs), your Xorg.0.log and your xorg.conf files to the Linux forum at [www.nvnews.net](www.nvnews.net) .[/QUOTE]

I set my color depth to 24, but that had no effect; I kept this new setting.

I removed render acceleration, which had an interesting effect: no longer did the X server send me back to the login screen randomly, but after I left the computer unattended it instead reached a state where it was still stable, but everything was a few hundred times slower; for example the screen unblackened line-by-line, and it took me around 15-20min to use top (Xorg was taking only 80% of the CPU; it had taken more before but that had never made my computer slow to a total crawl), and also to comment the RenderAccel line back in.

I commented out the DRI section; I kept this new setting.

Adding the "NvAGP" option had very strange consequences. When I set it to 0 (don't use), I got a black screen when I rebooted X. When I set it to 1,2 or 3, I got the warning message "The X server failed to start properly. Would you like to see debugging information? [Yes/No]" and the command prompt.

---

