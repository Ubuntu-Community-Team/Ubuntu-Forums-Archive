---
title: "switching laptop to tv"
date: 2011-01-22
forum: Multimedia Software
---

### Post by badnaam on 2011-01-22
I am running ubuntu version 10.01 and connecting  my laptop to my 1080p tv with a hdmi cable. the resolution seems to be fine, my problem I don't know how to switch between the laptop and the tv display, i.e. I can see the things on my tv screen but the mouse is not there, and if I press some keys around and somehow they mouse shows up on the tv screen, I don't know how to switch it back to the laptop.

Thanks!

---

### Post by argued.logic on 2011-01-22
> **badnaam said:**
> I am running ubuntu version 10.01 and connecting  my laptop to my 1080p tv with a hdmi cable. the resolution seems to be fine, my problem I don't know how to switch between the laptop and the tv display, i.e. I can see the things on my tv screen but the mouse is not there, and if I press some keys around and somehow they mouse shows up on the tv screen, I don't know how to switch it back to the laptop.

Thanks!

Hi!

I am doing the same with my laptop so here is a quick guide but that may differ depending on your manufacture, tv etc.
connect the hdmi to both laptop and tv and THEN boot up your laptop
when you reach login then press Fn (button) + F5 (may differ on your laptop) so you only see the out-put on your tv
once loged-in if all is what it is supposed to be you may want to change the option for how your ubuntu should react to your laptop:s lid is closed. For that you need to go to  Configuration Editor and find gnome-power-manager / buttons and change lid_ac value to "nothing" without the "". One last step is open Power Management and change "When laptop lid is closed." to Do Nothing. You should be set.
If your resolution isnt what it should be then you might edit your xorg.conf file etc etc

---

