---
title: "Ubuntu 12.10 and NVIDIA 9500 GT"
date: 2012-11-03
forum: Multimedia Software
---

### Post by jomtones on 2012-11-03
Ubuntu noob here - 12.10 Installed fine but was running Nouveau, so I tried the proprietary drivers.  This results in no launcher when you log in.  

Tried various things like installing the latest beta from console, but I've had no luck so far.  Right now my installation is messed up - I removed the NVIDIA drivers with 'purge' but I get no launcher on login, all I can do is run terminal and then firefox from there. :confused:

Any ideas on a way forward?  Unfortunately I have no cash to buy another graphics card so I'm stuck with NVIDIA for now.  Now I know why Linus told them F-YOU!

If I could get the launcher back that would be a good start!

---

### Post by jomt on 2012-11-03
Hi this is jomtones again joining this thread as my previous a/c is having trouble with a spam infraction, due to posting personal links in an 'introducing' post.

Any help you can give with this graphics problem would be much appreciated.  :-|

---

### Post by Ghost_Mazal on 2012-11-03
I have the same issue with a 9800GT.
No launcher and no icons and screen resolution messed up with all versions of the Nvidia driver.

Haven't found a solution yet. What I can tell you is how to revert to Nouveau driver.
You have to get to "software sources" and from there select the third party drivers.
The only way to do that without launcher is right-click on the desktop and select desktop
background. Then at the top-left of the screen that opens up click on "all settings".
This will bring you to the main settings page of ubuntu.
At the bottom click on "software sources"
That will open the software sources settings screen. Now go and click on the "Additional drivers" tab. This will bring you to the screen that lists the Nvidia drivers.
Select and apply the Nouveau driver. This will revert you back to Nouveau. Apply.
Press ctrl-alt-del and select log-out. After logout you will see the icon at top right that you can click to reboot.
Alternatively reboot from the terminal.

Now you will have your correct launcher and desktop back after reboot at least and running on Nouveau again. This is the only way I could figure out to get my desktop fixed.
But haven't found a fix for the Nvidia drivers not working.

---

### Post by Ghost_Mazal on 2012-11-03
I have just tried the solution in this thread , post nr 3 :

[http://ubuntuforums.org/showthread.php?t=2073060](http://ubuntuforums.org/showthread.php?t=2073060)

It worked for me.

---

