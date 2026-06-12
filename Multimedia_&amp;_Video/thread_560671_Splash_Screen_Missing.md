---
title: "Splash Screen Missing"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by nckinfn04 on 2007-09-26
Since I've installed 7.04, the splash screen hasn't ever appeared. It's just a blank screen until the login window appears. Can I fix this at all?

menu.lst file:
> 
title		Ubuntu 7.04
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd18bcbe-b420-4352-8ffa-8fb83f3d44ae ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=fd18bcbe-b420-4352-8ffa-8fb83f3d44ae ro single
initrd		/boot/initrd.img-2.6.20-16-generic


title		Ubuntu with memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
chainloader	+1


and usplash.conf
> # Usplash configuration file
xres=1024
yres=768

Graphics Card: Intel 82845G Chipset

Thanks!
Nick

---

### Post by Skerit on 2007-09-26
[B]*oops* I thought you where talking about the SPLASH screen after you log in, not the boot-splash-screen. Lol, they're probably just upgrading the artwork or something, it'll get fixed soon.
[/B]
I'm really not making fun of anything when I say: "It's a new feature!"

They really did remove the splash screen, no idea how to get it back though.

A lot of people don't like it, though! Me included, the time spent between logging in and the splash screen appearing can tell you a whole lot about what is going on in your system. Now every time I log in I wonder "What the hell is happening?"

---

### Post by radwis on 2007-09-29
hello, I go the same problem. Installed a program called Start-up-Manager. there I forced the usplash screen resoluton to 1024x768 - however the uspalsh conf fIle showed that already - and that solved the probelm :-)

---

### Post by DJ_Peng on 2007-09-30
I actually got it fixed with the [usplash-switcher]("http://www.getdeb.net/search.php?keywords=usplash-switcher") program. Can you post a link to the Start-up Manager? I'd like to check that one out myself.

---

### Post by radwis on 2007-09-30
> **DJ_Peng said:**
> I actually got it fixed with the [usplash-switcher]("http://www.getdeb.net/search.php?keywords=usplash-switcher") program. Can you post a link to the Start-up Manager? I'd like to check that one out myself.

code:
sudo apt-get  install startupmanager
password:
:)

---

### Post by DJ_Peng on 2007-09-30
Thanks, rawdis. That's an even better program than the one I suggest. I got the issue [blogged]("http://nancib.wordpress.com/2007/09/30/fixing-the-ubuntu-gutsy-boot-splash-issue/"), giving you credit for the suggestion.

---

