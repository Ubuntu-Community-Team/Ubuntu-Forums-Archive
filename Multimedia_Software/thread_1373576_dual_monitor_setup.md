---
title: "dual monitor setup"
date: 2010-01-05
forum: Multimedia Software
---

### Post by ryadav on 2010-01-05
I am on kubuntu 9.10 x86_64

I just got my new video card: nvidia 9500 GT to setup dual monitors. 
 
the video card has 2 dvi output to support dual monitors
monitor 1 is connect to dvi
monitor 2 is connect to dvi using a vga adaptor
 
i can't seem to get dual monitor to work? 

from system settings -> monitor, i see 2 vid outputs one is DVI0, the other is VGA2. what's odd is i can set up different screen resolution for each monitor, but I only see one desktop, both monitors show the same desktop.
 
how do i get each monitor to show it's own desktop?

---

### Post by fatbotgw on 2010-01-05
Make sure you don't have the "mirror desktop" option checked...

---

### Post by ryadav on 2010-01-06
where is the mirror desktop option? when i go to the multi-monitor panel in systems settings, it says

"This module is only for configuring systems with a single desktop spread across multiple monitors. You do not appear to have this configuration."

i can disable/enable one monitor, so kde is aware of the different monitor connected.

---

### Post by HappyFeet on 2010-01-06
You need to do: (I'm assuming you have the nvidia drivers installed)
```
sudo nvidia-settings
```
Make the necessary changes, apply, and save. It may throw up an error such as "failed to parse...." If it does, do the following.

```
sudo rm /etc/X11/xorg.conf
```
then restart nvidia-settings with:
```
sudo nvidia-settings
```
then make all the changes you need, apply, then save configuration, and it will see you don't have a xorg.conf file. A new window will open. Hit the button labeled **show output**, and copy the file. Leave nvidia-settings open, and open a new terminal. Do:
```
sudo touch /etc/X11/xorg.conf && sudo kate /etc/X11/xorg.conf
```
then paste what you copied from nvidia-settings. Save and reboot.

---

### Post by ryadav on 2010-01-08
I had to download the nvidia driver and build it to get dual monitor support.

to setup dual monitor with 2 separate desktop I have to enable Xinerama through the nvidia settings, otherwise the 2nd desktop was a black screen and I could not getting anything on there.

i booted up in recovered mode, because kde was hanging with the old driver? it was working fine but then on the next boot up i would freeze at the login screen

I would suggest other with a nvidia vid card to make sure they download the nvidia driver they need before they logout after install kubuntu 9.10  

this way you can build they driver, otherwise you're going to have do a reinstall because KDE will freeze on you

---

