---
title: "ATI Drivers Question"
date: 2009-03-14
forum: Multimedia Software
---

### Post by Alfx on 2009-03-14
I installed the ATI drivers a while back.

Now I'm starting to think maybe I should update my drivers.(Don't even got Catalyst control center)

-How do I fully uninstall the drivers?

-What's the easiest way to install the **latest** version of the drivers?

Thanks

---

### Post by Reeman on 2009-03-14
> **Alfx said:**
> I installed the ATI drivers a while back.

Now I'm starting to think maybe I should update my drivers.(Don't even got Catalyst control center)

-How do I fully uninstall the drivers?

-What's the easiest way to install the **latest** version of the drivers?

Thanks
the ati driver is problematic with Ubuntu..if you installed the ati through Ubuntu hardware drivers, you can just open the hardware drivers control and deactivate the driver....however if you had to use the proprietary driver install directly from ATI you should have the catalst control centre!

Could be that you did the driver Ubuntu download but it did not complete the activation. Go into hardware drivers and see if the ATI is activated. The catalyst control is installed with synaptic, it will show up under accessories in the program menu. 

Right click on the progam menu and choose "edit menus" if the ati catalyst is unchecked then you have the driver installed but you do not have the control available until you check the box. Silly how ubuntu trys to hide things sometimes.

Another way to check your install is to try the command in a terminal  ...  man aticonfig  ... if you have the driver properly installed you should be able to read the documentation that way.

I would definately [COLOR="Red"]not[/COLOR] recommend trying to install a newer ati driver!   When you do a kernel update it will choke on the module that it creates if you let it do its thing. 

Essentially you will wind up with the ugly option of having to do a dpkg-reconfigure -phigh xserver-xorg ... or worse still a dpkg-reconfigure xserver-xorg ...

Ubuntu does not use a real xorg.conf file it does things totally different than other distros it links the xorg.conf to the installed configuration so modules that re-write xorg.conf like the ati installer can really hose Xwindows.

This is what happened to me ..I installed the driver from ATI and when the kernel update came through it hosed the Xserver! 

Of course the easy way out is to just then edit your /boot/grub/menu.lst to blacklist the new kernel. Or just remove them from the list or change the grub settings so it does not just boot into the first on the list..lots of ways to fix it but lots of ways to really hose things as well.

I could even get really primitive and hit esc during boot level 1 so I can see the grub menu before it boots into a hosed version of root!

For this reason I switched back to Slackware 64bit...because this little change to Ubuntu is the biggest pita in the history of Linux. At least with a sane linux install I can still just edit config files to get the proprietary software modules to work.

I have used linux for many years and have found that if there is a way to try to make it more like Microsoft then the popular distros will do just that...

I think I will stick to the real thing and put up with having to use real linux skills again.

---

