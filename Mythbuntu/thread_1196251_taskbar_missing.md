---
title: "taskbar missing"
date: 2009-06-24
forum: Mythbuntu
---

### Post by zapstrap on 2009-06-24
I'm just curious, I had to start again from scratch earlier, as I had caused myself too much grief playing with the settings in mythbuntu (9.04).

Before re-installing, I had the equivalent of a taskbar at the top of the screen when the mythtv frontend was shut down.  With my fresh installation, I don't.  Where'd it go? Is there a specific package that needs to be installed to give that piece?  Should it just be there, and somehow I broke it?

---

### Post by Mister.Vash on 2009-06-25
They are usually called panels, which is why you might have had a little trouble find information on it.

Do you still have a panel at the bottom or side or anyplace on the desk other than the missing top panel?  If you do have one panel anyplace on your screen, you an right click in an empty area on the panel.  One of the menu items will be 'New Panel'.

If that new panel doesn't come up in the right spot, you can drag it up to the top.
It's probably not going to have all the things you had on it before, but you can get many of those back by Right clicking on the panel and choosing 'add to panel'

If that doesn't work, or if you don't have a another panel, reply and post the details about what it is doing or what item wasn't working

---

### Post by zapstrap on 2009-06-25
I have no panel anywhere on the screen.  I take it by your response I'm supposed to?  I just thought there should be one, but wasn't sure.  I can right click anywhere on the screen and get something that looks like the menu from the absent panel.  Is there a log somewhere I should look at?  I didn't see anything in /var/log/messages.

---

### Post by zapstrap on 2009-06-25
I tried running xfce4-panel from a terminal window, and the panel comes up as before.  I went into the xfce4 settings manager and added xfce4-panel to the Application Autostart list.  Works.

---

### Post by bcg30506 on 2010-08-04
I had the top panel in my old 9.04 system.  I recently did a fresh install of 10.04 and now all panels are gone.  Even the Panels icon in the control center is missing.  It appears maybe xfce4-panel may not have been installed in 10.04?  Is there a reason or can I just install it?

---

### Post by LowSky on 2010-08-04
are you sure it not there? With some video card if you set the wrong resolution it will be there but above the screen natural border. A way to test is move the mouse cursor to the top of the screen if you can still see it then your missing the panel, if you dont it means the screens resolution is set wrong or your ussing HDMI and Overscan is being applied.

If its the second option go all the way to the top left with the cursor and click, it should open the menu. then just change the resolution

if that isn't the case see this
[http://www.anujpathania.blogspot.com/2008/06/xubuntu-panels-disappear.html](http://www.anujpathania.blogspot.com/2008/06/xubuntu-panels-disappear.html)

---

### Post by bcg30506 on 2010-08-04
I was sure it wasn't there and verified my resolution is perfect for my screen.  I was wrong about the package not being installed though.  I did an Alt-F2 on the desktop and ran the xfce-panel command and voila! - the top panel reappeared.  Thanks.

---

### Post by zapstrap on 2010-08-04
Did the solution I posed back on 2009.06.25 not work?  I ended up on the xfce forums to find a solution.  The big move was to open a terminal window, and type this:

xfce4-panel

Your panel should load up, provided you have everything installed correctly.  Assuming that works, log out and your settings will be saved (should be a checkbox for this), so the next time you log in, the panel will just load.  I thought it should be in an init file or a config file somewhere, but apparently not.

If you right-click (left? can't remember) anywhere on the screen, you should get a menu that allows you to pick your way through to Accessories and launch a window.  If that doesn't work, you should be able to create a launcher, as LowSky's linked page indicates.

---

### Post by bcg30506 on 2010-08-04
Running xfce4-panel did work for me.  For some reason I thought it was not installed but it was.  You can just press Alt-F2 on the Desktop and it pops up a "Run command" dialog.  For now, I'm not worrying about having it autostart as the machine rarely reboots being our 24/7 DVR machine.

Thanks for the help.

---

