---
title: "dvi -&gt;hdmi to hdtv troubles"
date: 2009-01-22
forum: Multimedia Software
---

### Post by eppo on 2009-01-22
ok, so i have a computer running ubuntu 8.10 which is currently connected using a dvi->vga connector which connects to an input on my sony 50inch 1080i tv. that works fine. what i would like to try is hooking it up using my dvi->hdmi cable. when i hook it up this way i get a black screen. 
my vga controler is:Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller
how do i figure out a way to set the correct resolution to get this working correctly? do i just play with the setting under resolution control on the desktop? do i have to play with the xorg.conf file? is there a way to test different configurations remotely? i have a hp mini running netbook remix and i can ssh into the box also. 
any help you guys could give me would be great. 
thanks
Joe

---

### Post by Bleumunkie on 2009-01-22
I have the exact setup your talking about on the computer I'm typing this on.

If you still have, or can acquire (possibly online) the owners manual to your TV you should be able to look up the resolutions and refresh rates that your TV supports, change your settings to reflect this, and your good-to-go.

if you cant.....

you should be able to set your computer up to remote in and easily change things this way

on your HDTV system

1. Go to System >> Preferences >> Remote Desktop

2. Check off "Allow other users to view your desktop"
   2a. Make sure "Allow other users to control your desktop" is checked
   2b. _**UNCHECK**_ "Ask you for confirmation"
   2c. **Optional** for security reasons since your unchecking the confirmation, you can enter a password here.

3. Select the "Advanced" tab
   3a. Check "Disable the wallpaper when connected" to improve performance

4. Click "Close"

on your other system go to Internet >> Remote Desktop Viewer
(from what I understand Netbook remix is a standard Ubuntu install with extra packages, so this should be available)

your HDTV system should be listed to easily connect to if its on the same lan, if not you will have to use the IP of the HDTV system.

Log in, and fiddle until it shows up on your TV.

FYI, sometimes the HDMI connection doesn't resync well.  I would suggest switching the inputs back and forth from HDMI to your Cable or antenna and back to force the tv to attempt to reconnect to the signal source.  This can also be a problem in the future after the computer puts the display to sleep.

if this doesn't work, hopefully someone else will have another method for you to try.

---

