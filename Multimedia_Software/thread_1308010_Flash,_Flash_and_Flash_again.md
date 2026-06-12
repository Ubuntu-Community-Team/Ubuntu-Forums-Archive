---
title: "Flash, Flash and Flash again"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Swanmate on 2009-10-31
Hi,

I have used Ubuntu since 8.04 and I recently upgraded to 9.10. Besides being satisfied with the OS overall, I always had issues (frame skips, stuttering, crashes...) with flash content in browsers, especially with youtube videos.

After lots of gooling, tweaking, using this script and that hint, I finally had youtube videos working with 9.04. Fullscreen mode was still not possible (Flock (=Firefox) crashed when hitting the Fullscreen button), but windowed mode was able to display smooth playing videos. So I just used Compiz Dekstop Zoom to make the video fullscreen, and this workaround was acceptable for me.

Now, after the upgrade to 9.10, and after hearing from many people that this upgrade resolved all their flash problems, even in windowed mode I get heavy image tearing, stuttering and frame skips all over again, with fullscreen mode still crashing the browser.

I have tried many things to get this problem solved, none of them worked so far. Can't recall them all, but I think I tried all the flash versions available, with different installation methods (32bit, 64bit, as a .deb, via synaptic or Software Center etc), different versions of nVidia Drivers, tweaking the nVidia Options, turning Desktop effects on and off... and much more without any effect or even worsening the situation.

PC:
Ubuntu 9.10 amd64
2 x 2.9Ghz AMD
4 GB RAM
nVidia GeForce 9800GT 1GB

I really don't know what I could do to get this damn thing working correctly, any hint appreciated :(

---

### Post by Bucky Ball on 2009-10-31
System->Administration->Synaptic Package Manager; search for and install:

```
ubuntu-restricted-extras
```Add the Medibuntu repository to your sources list:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository")

---

### Post by Swanmate on 2009-10-31
Looked it up, was already installed.

---

### Post by miegiel on 2009-10-31
Try this : [_Adobe Flash install information for AMD64 (September 2009 update)_]("http://ubuntuforums.org/showthread.php?t=1259102")

---

### Post by Swanmate on 2009-11-01
OK, that did something, but unfortunately the performance got even worse :(. (In Firefox. Using the 64bit-Plugin in 32bit-Flock wouldn't make that much sense, I guess).

I'm beginning to think that I'm looking in the wrong place, because most of the settings I change or tweaks I'm doing don't seem to have an effect after all. For example, the vsync. "Sync to vblank" is activated both in compiz and in the nVidia xserver settings, but flash seems to totally ignore it and keeps tearing the image.

---

### Post by miegiel on 2009-11-01
> **Swanmate said:**
> OK, that did something, but unfortunately the performance got even worse :(. (In Firefox. Using the 64bit-Plugin in 32bit-Flock wouldn't make that much sense, I guess).

I'm beginning to think that I'm looking in the wrong place, because most of the settings I change or tweaks I'm doing don't seem to have an effect after all. For example, the vsync. "Sync to vblank" is activated both in compiz and in the nVidia xserver settings, but flash seems to totally ignore it and keeps tearing the image.

Sorry, I understood from your 1st post you're running 64bit ubuntu.

---

### Post by Swanmate on 2009-11-01
> **miegiel said:**
> Sorry, I understood from your 1st post you're running 64bit ubuntu.
I do :D.

It's just Flock not being "real" 64-bit, thus the x64-Flash Plugin works in x64 Firefox, but not in not-really-x64-Flock.

---

### Post by masux594 on 2009-11-01
Hmm.. Go to your local page "about:plugins" and tell us what flash plugin have u currently installed..

Sysc, A

---

### Post by Swanmate on 2009-11-01
**Shockwave Flash**

 File name:  libflashplayer.so
 Shockwave Flash 10.0 r32

---

### Post by masux594 on 2009-11-01
ok.. .. try to uninstall the plugin that u have installed now, and then see if there's some plugin in the flash section of the about:plugins ..so, first of all let's uninstall ..```
sudo apt-get remove flashplugin-nonfree
```

So, tell me, what appear now?

Sysc, A

---

### Post by Swanmate on 2009-11-01
"Package flashplugin-nonfree is not installed, so not removed"

---

### Post by masux594 on 2009-11-01
Perfect.. so, uninstall the "official" flash package that u have installed before..
```
sudo apt-get remove adobe-flashplugin
```

now in about:plugins?

Sysc, A

---

### Post by Swanmate on 2009-11-01
"E: Couldn't find package adobe-flashplugin"

Edit: After removing everything that could have anything to do with flash and reinstalling it with the Firefox wizard =>

```
**locate libflashplayer.so**
/home/luno/.local/share/Trash/files/libflashplayer.so.trashinfo
/home/luno/.local/share/Trash/info/libflashplayer.so.trashinfo.trashinfo
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```

---

### Post by Bucky Ball on 2009-11-01
You also did this?

[quote=Bucky Ball]Add the Medibuntu repository to your sources list:

[https://help.ubuntu.com/community/Me...e%20Repository]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repository")[/quote]

If you haven't, do. It installs flash and a heap of other things that will probably fix your problem.

---

### Post by masux594 on 2009-11-02
Oki, now i understand.. y have the "flashplugin-installer" pakage currently installed.. so, remove that and install the flash plugin that i use for flash..
```
sudo apt-get remove flashplugin-installer && sudo apt-get install flashplugin-nonfree
```

This might solve your problem..

Sysc, A

---

### Post by Swanmate on 2009-11-02
I already tried all available variants of flash. Nothing changed between the versions or the performance got even worse.

@Bucky: A heap of other things? I don't know if aimless whack-a-mole package installation will help that much... any specific packages :>?

---

### Post by masux594 on 2009-11-02
Hmm.. have u tried my "solution" without success?

Sysc, A

---

### Post by Bucky Ball on 2009-11-02
> **Swanmate said:**
> I already tried all available variants of flash. Nothing changed between the versions or the performance got even worse.

@Bucky: A heap of other things? I don't know if aimless whack-a-mole package installation will help that much... any specific packages :>?

Flash for one. It will install when you update the repo.

---

### Post by Swanmate on 2009-11-02
> 
Hmm.. have u tried my "solution" without success?

Yes. As I said, i tried every available flash-Package. The free ones (Gnash & swfdec) didn't work at all; adobe-flashplugin (The .deb from the adobe page), flashplugin-installer and falshplugin-nonfree worked, but had a bad performance (additionally, adobe-flashplayer crashes the browser when hardware acceleration is turned on in flash. Could have something to do with forcing the architecture when in installing).

> 
Flash for one. It will install when you update the repo. 	

Does the Medibuntu-Repository have any additional versions of flash than the ones i mentioned above?

---

### Post by Swanmate on 2009-11-02
Just made a fresh install of ubuntu 9.10, just to make sure it's not because of the update. It's not. Still the same crappy flash performance. Maybe I should try Ubuntu in 32bit and see if flash works correctly then...

---

### Post by Swanmate on 2009-11-02
"Solved" by reinstalling 9.04

---

### Post by masux594 on 2009-11-03
D'oh.. I'm too late.. But if u want, there's another user with your problema and he solve it with [this]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ#Flash") link.. I'm sorry..

Sysc, A

---

