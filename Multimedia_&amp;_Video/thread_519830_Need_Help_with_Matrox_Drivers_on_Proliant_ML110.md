---
title: "Need Help with Matrox Drivers on Proliant ML110"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by bm5034 on 2007-08-07
Greetings,

I am looking for help installing the proper video driver for an HP ProLiant ML115 server, running 6.06 LTS.  From my hardware configuration (output of the lspci command), I see that the server has an integrated Matrox chipset (reported as VGA compatible controller: Matrox Graphics), although I'm not sure specifically which model.

My first symptom is that after initially installing the ubuntu desktop, the screen resolution is very large (640x480), and most windows are too big for the screen.  My monitor is a Dell 19" flat panel, E193FP.  At first, I tried all combinations of settings with the X server configuration program, using both vga and vesa drivers.  When I reboot the server, the resolution always reverts back to 640x480.

I downloaded and installed the Matrox drivers from the web.  When I attempt to configure the system with that driver, X server fails with a message saying selected video modes are not supported.

So, I'm trying to first determine the correct driver that I should be using, and secondly, how to properly configure the display resolution.  Since this machine will be running as a web server, I don't need the highest and most colorful settings; just a higher resolution that is easier to work with.

I'll be happy to pass along any diagnostic information or messages that can assist in resolving my problem.

UPDATE:  I managed to get the video resolution working properly at 1024x768 with the vesa driver, when logged in as root.  After changing the security setting to allow administrator login to the desktop, I successfully changed the setting with the "Screen Resolution" applet.  The resolution settings are retained across reboots of the system.  However, when I log in as a user other than root, the resolution continues to revert to 640x480.  Almost appears to be a security or permissions-related issue.  

Thanks in advance,
Bob

---

### Post by Lersted on 2007-10-07
Hi Bob

Have you solved your problem cause i´ve got the exact same problem and i havent got it fixed yet.

---

### Post by oge on 2008-04-13
Hi Bob

I am assumimg that you are trying to set up the desktop version, as you are talking about probs with windows. I am trying to install 7.1 desktop on my ML115 as a dual boot & have the same issue.

Server edition 7.10 is a breeze to set up on the Proliant & while it may lack the GUI (although you can install x-window) & mean a bit of a learning curve with command line, the ease with which you can set up a LAMP server would make it ideal for your web server. I dont have any experience with Server 6.06 but it may be worth a try if you need the ext support.

Its not really a solution to your 6.06 probs but would get your web server up & running.

owen

---

