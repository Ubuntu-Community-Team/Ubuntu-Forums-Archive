---
title: "So whats up with plymouth in maverick why is there still problems"
date: 2010-06-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-21
For instance this bug right here:
[https://bugs.launchpad.net/bugs/563878](https://bugs.launchpad.net/bugs/563878)

When i used fglrx with final lucid and maverick there was a time that i had the big splash screen, but later it just stop showing 
the logo at all and that how it was until the xorg breakage and now with xorg everything is fine i can see sleek logo but i'm pretty 
sure that once the official fglrx would be released again i would again be without any logo at all just a purple screen at boot. 

So does anyone is still working of improving plymouth?or anything eles that can fix this problem?

---

### Post by wojox on 2010-06-21
You can change that bug yourself very easily. I went so far as to remove. You can change the vga=795.

---

### Post by ToxicBurn on 2010-06-21
**plymouth should be removed from the distro untill it works **
 
**Sloppy if you ask me it needs alot of work**

---

### Post by MacUntu on 2010-06-21
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-grub2-boot-framebuffer](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-grub2-boot-framebuffer)

Using a framebuffer, the splash screen looks just like with KMS-enabled drivers.

---

### Post by mc4man on 2010-06-21
> Using a framebuffer, the splash screen looks just like with KMS-enabled drivers. 
did something similar in lucid with nvidia - more just to see (looks just like with nouveau

Basically getting the appropriate fb rez for my hardware with sudo hwinfo --framebuffer, then adding to grub blue lines (native rez is best, mine is 1280x800-24 on this laptop
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Blue"]nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap"[/COLOR]
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR="Blue"]GRUB_GFXMODE=1280×800[/COLOR]

Then adding also to /etc/initramfs-tools/modules
> # Examples:
#
# raid1
# sd_mod
[COLOR="Blue"]uvesafb mode_option=1280x800-24 mtrr=3 scroll=ywrap
[/COLOR]

and setting with 3 commands
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo update-grub2
sudo update-initramfs -u

Theree's a post on wordpress somewhere detailing this, should be easy to search out if interested.., though for maverick I'll just wait & see what they work out

---

### Post by dino99 on 2010-06-21
latest days/weeks have pushed up some new packages: kernel, grub2

so oldish workaround might not be the good answer for coming days

[http://patchwork.ozlabs.org/patch/53582/](http://patchwork.ozlabs.org/patch/53582/)

---

### Post by philinux on 2010-06-21
> **dino99 said:**
> latest days/weeks have pushed up some new packages: kernel, grub2

so oldish workaround might not be the good answer for coming days

[http://patchwork.ozlabs.org/patch/53582/](http://patchwork.ozlabs.org/patch/53582/)

Which is one example of why I always run a vanilla testing release with no workarounds.

---

### Post by autocrosser on 2010-06-21
I'm running a updated Lucid install & reverted the patches in it this weekend--waiting to see the new stuff.

---

### Post by tad1073 on 2010-06-21
A simple one-liner in /etc/default/grub worked for me
Where my screen resolution is 1680x1050

```
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=YOUR SCREEN RESOLUTION
```

---

### Post by aviramof on 2010-06-21
I tried to fix this problem once before with a guide i found and with startupmanager and it didn't worked well and i was forced to reinstall ubuntu so i don't that messing with resolution is a good idea for everyone.

---

### Post by ranch hand on 2010-06-21
You can safely mess with the resolution.  You can always go in and fix it.

What is not a good idea is Start Up Manager.  It is really not up to speed with grub2 yet and I would not recommend its use except for very basic things.  As those are easy things to do it is best just not to have it installed at all, particularly on a development cycle OS.

---

### Post by aviramof on 2010-06-21
Thanks for the tip i hope that something similer but better would be released soon because he sure make things easier when you want to change the default os and etc.

---

### Post by ranch hand on 2010-06-21
> **aviramof said:**
> Thanks for the tip i hope that something similer but better would be released soon because he sure make things easier when you want to change the default os and etc.
This is all fairly easy to do by;
```

gksudo gedit /etc/default/grub

```
and editing it your self.  True, it is not a gui.  It is also true that it will not mess with your system to the point you need to do a new install.

I am sure the guy behind SUM is working on it as he can.  I believe it is a one man "team".  Probably needs a bit of time.

---

### Post by aviramof on 2010-06-22
Now look it's not that i don't know how to do it with commands such as 
gksudo gedit and etc i do but nothing can beat good gui it's like working 
with windows 2008 core or working with dos it's nice and i can do it but it's 
not the same thing it takes a lot more from you to do it using command line then 
via gui.

---

### Post by philinux on 2010-06-22
> **aviramof said:**
> Now look it's not that i don't know how to do it with commands such as 
gksudo gedit and etc i do but nothing can beat good gui it's like working 
with windows 2008 core or working with dos it's nice and i can do it but it's 
not the same thing it takes a lot more from you to do it using command line then 
via gui.

OT I guess but here's my 2 cents.
This area needs some love I guess.
The problem is that gnome-system-tools should include a grub/grub2 gui and it doesn't. It was supposed to take over from grubconf according to this page.
[http://grubconf.sourceforge.net/](http://grubconf.sourceforge.net/)
[http://projects.gnome.org/gst/](http://projects.gnome.org/gst/)

And as ranch said SUM is a one man band. [https://launchpad.net/startup-manager/](https://launchpad.net/startup-manager/)

If you go to his home page the version is one behind that in our repos.
Shame really as SUM for grub was great. I guess with grub2 he hasn't had the time to catch up.

---

### Post by aviramof on 2010-06-22
Well so far SUM is working fairly well but still it would be great if a new an updated version 
or other similer software would be released at least with till the release of final Maverick if not sooner.

---

