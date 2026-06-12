---
title: "Xorg won't turn off."
date: 2010-03-01
forum: Multimedia Software
---

### Post by Defiant1 on 2010-03-01
[FONT=Arial Black][I][B]Hello.
I'm trying to install Nvidia drivers 190.53 on my karmic with a Nvidia 9500GT. I've downloaded the file from the Nvidia website. I've done this before on previous installations and everything went fine, however, with karmic turning off the xserver is a bit of a trick.

/etc/init.d/gdm stop doesn't work
sudo service gdm stop doesn't work
sudo killall gdm doesn't work.

After I run sh ./NVIDIA-linux-x86-190.53-pkg1.run a notice pops up and tells me I'm running x and I need to exit out. I thought I did.

I'm still poking around looking for an answer I've looked at the instructions on the Nvidia website, but I don't remember it being that complicated before and am a little nervous about removing files I don't know what they do.

Thanks in advance for any help.
[/B][/I][/FONT]

---

### Post by no2498 on 2010-03-02
i do know ubuntu 910 does not use xorg any more
you need to make the file or find what it is using now days
hope this helps

---

### Post by wojox on 2010-03-02
You logged out and switched to a tty console right? Ctrl+Alt+F1

---

### Post by mcduck on 2010-03-03
> **no2498 said:**
> i do know ubuntu 910 does not use xorg any more
you need to make the file or find what it is using now days
hope this helps

Sure it does use Xorg. :D

I suppose what you were thinking about is that Ubuntu doesn't use the xorg.conf configuration file any more (which it also uses if you just create it, otherwise it tries to autodetect the correct settings).

What comes to the original problem in this thread, wojox is probably correct, you need to get out of X before you can stop it. All the commands tries are correct and should work just fine as long as you run them from a TTY instead of a terminal emulator inside your graphical desktop.

Also, unless there's a specific reason to manually install the drivers from nVidia, you should just use the restricted drivers manager (in System/Administration menu) to automatically download & install the nVidia drivers from Ubuntu's repositoris.

---

### Post by handy on 2010-03-03
Sorry Defiant1, as soon as my eyes saw your bold text you lost me.

Just a tip, don't shout (use lots of capital letters) or yell (use lots of bold) if you want to attract responses in any forum.

---

