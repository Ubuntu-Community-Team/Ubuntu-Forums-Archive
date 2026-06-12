---
title: "Updating Nvidia Drivers question"
date: 2010-03-30
forum: Multimedia Software
---

### Post by Perk on 2010-03-30
I have some games that are running extremely slow in WINE, so I figured I might try to upgrade my current video driver. I'm using a Dell Laptop with Quadro NVS 110M. Using Ubuntu Jaunty.

Currently, in the 'Hardware Drivers' window, I have the 'NVIDIA accelerated graphics driver (version 180) [Recommended]' driver enabled. I want to update to the new one: 195.36.15 [http://www.nvidia.com/object/linux_display_ia32_195.36.15.html]("http://www.nvidia.com/object/linux_display_ia32_195.36.15.html")



From what I understand, I have to first remove my current version using:
```

sudo apt-get --purge remove nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings

```

Then I have to install by doing this according to Kosimo:
```

Enter in a real terminal mode: CONTROL + ALT + F1
cd Desktop
sudo /etc/init.d/gdm stop
sudo sh ./Nxxx.run
Choose x.org automatic configuration
sudo reboot

```

Kosimo also mentioned:

"Remember to uninstall any previous version! If you are using the proprietary hardware tool in Ubuntu you should disable the current driver first and then restart your computer before you start. THIS IS MANDATORY!"

Have I done this in the steps above? Also, am I missing anything in the steps that I should add before I try them? I just want to make sure I don't screw up my system. 

Thanks!

---

### Post by mango42 on 2010-03-30
> I have some games that are running extremely slow in WINE, so I figured I might try to upgrade my current video driver.

Are you sure it's the video driver causing the problem? The only reason I ask is that I can run a very demanding flight simulator (IL2 1946 in 'Perfect' mode) flawlessly through WINE (in fact it runs more smoothly than in its native environment!) using the recommended nVidia 180 driver on my SLI (dual video card) 7900GS equipped system.

Might be worth examining your system log first? Could save a load of grief ;-)

---

### Post by Perk on 2010-03-30
Yeah, I think you're right. I'm able to run Halo pretty well with my current settings. The games I was running were intensive 2D games (commercial and indie) and after doing some poking around it seems that the DirectDraw has some problems in WINE. I've set the DirectDrawRenderer to 'opengl' and RenderTargetLockMode to 'readtex', but I did not see any performance change.

Upgrading to WINE 1.1.41 did help a bit. The main menu on some of the 2D games are a slightly faster, but the in-game menus/gameplay are still slow. Do you guys have any other hints?

---

