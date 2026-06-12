---
title: "Tearing in videos even after removing compiz"
date: 2011-03-31
forum: Multimedia Software
---

### Post by Feelkarma on 2011-03-31
Hi all,
I have this weird problem – used to have it before upgrading to Ubuntu 10.10 : tears when watching movies and in all players (onboard Nvidia card).

At the time, II realized that this was due to Compiz, uninstalled it and forgot about it after upgrading to Ubuntu 10.10 as the problem disappeared.

I recently decided to give Cairo Dock a go and along with it the tears came back (and Compiz).

Now the weird thing: I made sure that I removed every trace of Cairo Dock and Compiz, but for some reason I suspect that something is still there as I am still getting the tears in videos, in all players (VLC and Gnome). I tried deactivating visual effects in Preferences > Appearance, no change. I also tried reinstalling Ubuntu-desktop. Again, no luck.

A solution that worked temporarily was to install mutter and do a 'mutter --replace' every time I start Ubuntu. 
However, this does not work anymore : after entering the ‘mutter --replace’ command the terminal freezes.

If I leave it, after a while, I get the following message:

> Window manager warning: Log level 16: STACK_OP_ADD: window 0x4400012 already in stack
Window manager warning: Log level 16: STACK_OP_ADD: window 0x4400012 already in stack

If I try to force close it, the top part of the windows (the part where the minimize/close buttons are) disappear and they freeze (i.e. I can move my mouse but can’t switch from one window to another).

I suspect there is something wrong with some window manager but can’t figure out what. If I enter the command ‘mutter’ in the terminal, I get the following message:

> Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

Can anyone help? I suspect I should provide more info but I’m still fairly new to this, so apologies if I missed anything out.

Because of this, my wife is forcing me to boot under Windows XP, so as you understand, this is seriously affecting my personal life ;)

Thanks

Feelkarma

Config:
Dual boot Windows XP / Ubuntu
M/B: Asus M3N H HDMI with Phenom CPU
2gb Kingston PC8500 Memory
Pioneer DVD writer
Samsung 500 gb HD

---

### Post by Feelkarma on 2011-04-02
No one? I'm getting a bit desperate here, only option being a clean reinstall but considering the pain of getting the hardware to cooperate with Ubuntu, I'd rather not.

I have also tried this (reinstalled compiz for that matter) but no luck [http://ubuntuforums.org/showthread.php?t=1305320](http://ubuntuforums.org/showthread.php?t=1305320)

I am sure that there is some window manager stuck somewhere but I can't find out how to remove/disable it.

Please help.

Thanks

Feelkarma

---

### Post by Feelkarma on 2011-04-02
Just to continue my own little monologue, somehow, inputing nvidia-settings -l seems to solve the tearing issue. There are still weird things happening with the graphics and windows manager but at least, movies look pretty decent.
If someone has any interest in or clue on this, please feel free to comment...

---

### Post by BicyclerBoy on 2011-04-02
The nvidia-setting -l option maybe resetting/reloading the vsync to the correct refresh rate ??

The compiz settings need to be set to sync to the right monitor & refresh rate..AFAIK compiz & nvidia driver gets the incorrect refresh rate for vsync..

The nvidia-settings vsync sets vsync for XVideo only.
Nvidia VDPAU video (you are not using) is vsync internally always.
VLC can use VA-API if compiled etc..else it uses XvMC/X11 or XVideo.

CCSM is used to config compiz to correct display/refresh rate.

Good luck

---

### Post by nerdy_kid on 2011-04-02
yeah I had this issue too, drove me nuts.  do this:

```

sudo -i
echo "/usr/bin/nvidia-settings -l" > /etc/X11/Xsession.d/40nvidiasettings
exit

```
open up nvidia-settings, go to the opengl page and hit sync to vblank.
then reboot. X11 will run nvidia-settings all by itself now, before compiz starts at that, so you might be able to reinstall compiz.

---

### Post by Feelkarma on 2011-04-03
Thank you both!
@BicyclerBoy: I actually have uninstalled compiz but may try to reinstall and see what happens. I'll try and look more into how it all works as it's still all a bit unclear to me (i.e. graphics under Ubuntu).
@nerdy_kid: thanks, I tried but sync to vblank was already checked. Anyway, it seems to be working so thank you!
Feelkarma

---

