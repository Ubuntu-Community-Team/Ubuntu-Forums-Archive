---
title: "Help with nvidia geforce 6100"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by iispyderii on 2008-01-09
help please,

i searched and worked for 4 hours on this and no avail.
im trying to install the 32 bit version

i have a dell inspiron 531
AMD Athlon 64 X2 Dual Core 4000+
NVIDIA GeForce 6100 nForce 430
2 SATA HDD 250GB (1 for vista other for storage space and ubuntu)

the problem is that i burned the iso to the cd and i booted it from the main ubuntu menu, i just put the cd in. it loads the orange bar it goes back and forth, loads some more and then it says "cannot display this video mode" but i can hear the sound in the background

i am completely new with this Ubuntu thing (7.10)
but i am a very techy guy. but i dont know hardly any terms for ubuntu
so can someone please give out a know solution?

---

### Post by satx on 2008-01-09
Sorry, I misunderstood your problem. You can't boot, right?

---

### Post by iispyderii on 2008-01-09
correct, i cant see the install button but i can hear the startup.
oh, and my monitor is a dell  1024x768 60Hz is the max res.
i dont know what to do to get the installatioin to start.
i have dsl and a good connection, and i dont want to ask for a shipped cd. but if i must, i will.

---

### Post by manimal347 on 2008-01-10
Well,  I can say the problem sounds like something wrong with Ubuntu's setup of the Xserver (what displays X11/your GUI). You have what sounds to be a very old monitor, so maybe Ubuntu is trying to autodetect its settings, failing as the monitor has no way to communicate it's specifications, leading Ubuntu to assume a higher than permissible refresh rate or resolution combo.

Try doing the alternative text-install CD. It's TOO easy, I swear. It even has graphics of a sort, 80*25 column ANSI characters that create a menu-driven GUI. Since it presumably engages your graphics solution in a *much* more primitive level (plain IBM-compatible VGA@ 640x480? plain "VESA" driver?), it should solve that problem. Once the install is done, xwindows may indeed not work due to some autodetection issue, but we can work on that then, and in the (short, I swear...) interim, you'll have a rockin' CLI system to start exploring the guts and mechanics of *nix that lie beneath those pretty windows and snazzy configuration tools.

It won't ask you anything much more than the LIVECD setup, though there's a small chance you'll have to run it in "expert mode" because life is weird and something else might come up, though if you really made it all the way to the point where Xwindows is ready to load, the kernel and core modules should be okay for your machine. In other words, "expert mode" is a "Dooms-Day scenario of sorts.

-------------------------------------
Just re-download the Ubuntu CD, and check the box that say "alternate install."
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

It should work in CLI, though again, you *may* have some minor issues with xwindows. If they arise, try backing up your /etc/X11/xorg.conf file (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak), then execute dpkg-reconfigure xserver-xorg. Tell it your graphics driver is "nv," accept most defaults, and look up what your monitor can do (It's an old one, so be conservative in your settings lest the screen roll or your eyes bleed from flicker), Then, when you get to where it asks about your monitor, play around with the settings till you hit what your screen likes. Start with beginner (or whatever it's called), and select 15," even if you really own a 17." Work from there if unhappy..

Or, you can use always use Nano or Vi to edit /etc/X11/xorg.conf as root (sudo), manually changing your monitor settings and graphics driver as specified in the text file. This is probably harder if you're "green" to *nix computing.

---

