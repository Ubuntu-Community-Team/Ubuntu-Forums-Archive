---
title: "32 bit Flashplugin on Ubuntu Precise 64 bit?"
date: 2012-05-14
forum: Multimedia Software
---

### Post by jamesmika on 2012-05-14
Is it possible to use the 32 bit Flashplugin on Ubuntu Precise 64 bit?

I downloaded flashplayer11_1r102_63_linux.i386.tar.gz from adobe, unpacked and ~/flashplayer11_1r102_63_linux.i386$ cp libflashplayer.so ~/.mozilla/plugins/.

Firefox about:plugins does not recognize it. (It's the only plugin in that folder and I use no other plugins.)

Reason is, I want test if the 32 bit Flashplugin can solve any issues which I couldn't solve with [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796) or [http://ubuntuforums.org/showthread.php?p=11918815#post11918815](http://ubuntuforums.org/showthread.php?p=11918815#post11918815)

---

### Post by megamasha on 2012-05-14
I imagine probably not. But I'm not a Linux guru.
In my experience, 32-bit software won't run on 64-bit platforms. Typically, it needs to be separately compiled for 64-bit architecture. I find it even less likely if Firefox itself is 64-bit. But as I said, I'm not an expert.
I use FlashAid, but that may not fix any problems with Flash itself. You might also want to look into FlashVideoReplacer.

Sorry I can't be of more help.

MM

---

### Post by kurt18947 on 2012-05-15
> **megamasha said:**
> I imagine probably not. But I'm not a Linux guru.
In my experience, 32-bit software won't run on 64-bit platforms. Typically, it needs to be separately compiled for 64-bit architecture. I find it even less likely if Firefox itself is 64-bit. But as I said, I'm not an expert.
I use FlashAid, but that may not fix any problems with Flash itself. You might also want to look into FlashVideoReplacer.

Sorry I can't be of more help.

MM

My experience is that FlashAid will install a 64 bit beta install.  I just did it yesterday and it seems to work fine.

---

### Post by jocko on 2012-05-15
There is a plugin called 'nspluginwrapper' that can be used to run 32 bit plugins in 64 bit firefox.
To install it, just type this in a terminal:
```
sudo apt-get update
sudo apt-get install nspluginwrapper
```Note that I don't know if it looks for plugins in firefox's standard plugin directory, but I guess it's easy to find out...
And in my experience (from the time there was no 64 bit flash plugin) nspluginwrapper is pretty unstable.

---

### Post by jamesmika on 2012-05-17
> **jocko said:**
> There is a plugin called 'nspluginwrapper' that can be used to run 32 bit plugins in 64 bit firefox.
To install it, just type this in a terminal:
```
sudo apt-get update
sudo apt-get install nspluginwrapper
```Note that I don't know if it looks for plugins in firefox's standard plugin directory, but I guess it's easy to find out...
And in my experience (from the time there was no 64 bit flash plugin) nspluginwrapper is pretty unstable.
Installation worked. In case someone else wants to try it.

[COLOR=#221f1e][FONT=Sans Serif]sudo apt-get install ia32-libs[/FONT][/COLOR]
 
 [COLOR=#221f1e][FONT=Sans Serif]nspluginwrapper -v -i /home/<username>/flashplayer11_1r102_63_linux.i386/libflashplayer.so[/FONT][/COLOR]
 [COLOR=#221f1e][FONT=Sans Serif]
[/FONT][/COLOR]
 The same flash bugs persist, still unusable, but this thread is solved anyway as I could test it. Now I know it. Thanks.

---

