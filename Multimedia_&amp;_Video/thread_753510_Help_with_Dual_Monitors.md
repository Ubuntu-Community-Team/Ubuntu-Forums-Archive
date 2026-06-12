---
title: "Help with Dual Monitors"
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by cereal killer on 2008-04-12
Hi all. 

I've been trying to get this to work for weeks, and no luck. I've tried all the tutorials and guides I could find, but they seem to screw up my video settings completely.

Basically I want to have 2 monitors like in Windows, where I can drag windows from one monitor to another. I want to watch videos I have on my PC on my TV.

I installed Envy and messed around with that, but the best I could do is get one big stretched out window, and that doesn't cut it.

I'm running a 8600GT on Ubuntu 7.10. I'm fairly new to Ubuntu and Linux all together. Could anyone please walk me through this process? I really know little about editing the xorg.conf file.

---

### Post by ad_267 on 2008-04-12
This is what worked well for me with an nvidia 6600GT:

Plug in just one monitor
Run "sudo dpkg-reconfigure -phigh xserver-xorg" to reconfigure X to default settings
Restart X with ctrl-alt-backspace
Enable the nvidia restricted drivers
Restart X
Run "sudo nvidia-settings" and under x server display configuration enable the second monitor using twin-view and choose your settings
Restart X and everything should work :)

---

### Post by cereal killer on 2008-04-12
> **ad_267 said:**
> This is what worked well for me with an nvidia 6600GT:

Plug in just one monitor
Run "sudo dpkg-reconfigure -phigh xserver-xorg" to reconfigure X to default settings
Restart X with ctrl-alt-backspace
Enable the nvidia restricted drivers
Restart X
Run "sudo nvidia-settings" and under x server display configuration enable the second monitor using twin-view and choose your settings
Restart X and everything should work :)

Nope, same thing. All it does is stretch my desktop onto my TV, instead of "extending" it like Windows does.

Maybe I did something wrong? At what point am I supposed to plug in the 2nd monitor? I did it after enabling the restricted drivers and before restarting.

---

### Post by ad_267 on 2008-04-12
Sorry I forgot to mention that, I plugged it in just before running nvidia-settings but it should work how you did it too.

I'm not sure what you mean by stretching instead of extending. My desktop background extends over both screens but gnome panels only take up the width of one screen and windows expand to take up just one screen. If you maximise a window does it fill both screens?

---

### Post by flyingaway on 2008-04-12
Thanks, nice post.  I get mine work following it, but I got another issue.  How can I choose which one to be the "primary" monitor?  I intended to my laptop monitor to be the primary one, but nvidia-settings always makes the external monitor to be the primary one. ( By "primary", I mean it contains ubuntu panels, main menus, etc). 

I tried to change the locations of the two monitors but got no luck. Once I restart X, the external monitor is always the primary one!  Any suggestions on this?  Thanks a lot.



> **ad_267 said:**
> This is what worked well for me with an nvidia 6600GT:

Plug in just one monitor
Run "sudo dpkg-reconfigure -phigh xserver-xorg" to reconfigure X to default settings
Restart X with ctrl-alt-backspace
Enable the nvidia restricted drivers
Restart X
Run "sudo nvidia-settings" and under x server display configuration enable the second monitor using twin-view and choose your settings
Restart X and everything should work :)

---

### Post by cereal killer on 2008-04-12
> **ad_267 said:**
> Sorry I forgot to mention that, I plugged it in just before running nvidia-settings but it should work how you did it too.

I'm not sure what you mean by stretching instead of extending. My desktop background extends over both screens but gnome panels only take up the width of one screen and windows expand to take up just one screen. **If you maximise a window does it fill both screens?**

That's exactly what happens and what i want to avoid. In Windows when I drag a window to the other monitor, and max it, it just fills up that one monitor. Here it stretchs and fills both screens.

Here, as soon as I apply the settings, the Icons that I have at the top right corner, now appear at the top right corner of the 2nd monitor.

---

### Post by flyingaway on 2008-04-13
I see the same thing after configuring in nvidia-settings, but after restarting X, I get the "extended" behavior. although my primary monitor is on the wrong one. :(

---

### Post by Kiri on 2008-04-13
> **cereal killer said:**
> That's exactly what happens and what i want to avoid. In Windows when I drag a window to the other monitor, and max it, it just fills up that one monitor. Here it stretchs and fills both screens.

Here, as soon as I apply the settings, the Icons that I have at the top right corner, now appear at the top right corner of the 2nd monitor.


You need to save the settings to your xorg.conf file (there is an option to do this in nvidia-settings). 
First you should make a backup of your xorg.conf of course. 
You can do so like this:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

then setup how you want by typing
sudo nvidia-settings
and making the changes. Then press save to x config file (or whatever it says on that button), 
and you must restart X (ctrl-alt-bkspace)
Pressing apply didnt work well for me...

---

### Post by Kiri on 2008-04-13
> **flyingaway said:**
> I see the same thing after configuring in nvidia-settings, but after restarting X, I get the "extended" behavior. although my primary monitor is on the wrong one. :(

I'm trying to solve this too... 
Whichever display is on the left for me always wants to be primary. But I want the one on the RIGHT to be primary. Let me know if you get it working

---

### Post by ad_267 on 2008-04-13
Thanks Kiri I forgot to mention the part about saving the changes to the xorg.conf file, I was just going from memory.

I have the same problem with my monitors as I have one monitor that can use a digital video input which I want as my main monitor and another that only uses vga but nvidia seems to insist that the monitor plugged into the vga port is the default so I have to plug the better monitor into the vga port and use a vga to dvi adapter for the other monitor. I think this is a problem with the nvidia driver.

You should just be able to move gnome panels onto the monitor that isn't the primary one though. Just click on them and hold down the mouse and drag.

---

### Post by Kiri on 2008-04-13
The panel is actually ok. But I'm using AWN which I cant seem to move the position of, and the icons are a hassle too..

Its kind of frustrating, since it seems like it should be really basic.

---

### Post by cereal killer on 2008-04-13
Success! Works perfectly after saving xorg.conf file. Thanks!

But one more tiny thing. :)  Same as what happened in Windows, the screen set automatically is a little too big, so when I maximized a video window, the edges are eaten up and can't be seen. In the Nvidia control panel in Windows there was an option to fit the screen. I can't see it here. Again, not a huge problem, but if possible and not much trouble, I'd like to fix it.

Oh and another question. The xorg.conf file that I back up, does it stay backed up until I make another backup and it's overwritten?

Thanks again!

---

### Post by Kiri on 2008-04-13
if you made the backup manually (by using the cp copy command) then it is essentially just another copy of the file. So yes it will stay there unless you overwrite it. 
If you want to back it up again, you can overwrite that one, or just make a new one with a different name.

Not sure about your screen size problem... If your resolution is set correctly and your monitor is calibrated, then there should be no problem with it

---

### Post by karrank% on 2008-04-13
don't know if this will help, but the resolution may need to be tweaked on the monitor in question to have it fit just right.

---

