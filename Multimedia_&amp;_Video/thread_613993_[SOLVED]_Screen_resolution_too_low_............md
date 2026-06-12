---
title: "[SOLVED] Screen resolution too low ..........."
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by tahitiwibble on 2007-11-15
Can someone please advise me on what to do with this situation;

dad@dad-desktop:~$ sudo dpkg-reconfigure xserver-org
[sudo] password for dad:
Package `xserver-org' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-org is not installed.
dad@dad-desktop:~$ 

During boot I get an X for the mouse pointer and the message that says "Ubuntu is running in low graphics mode" and the only two screen resolutions available are 800 x 600 @ 85Hz or 640 x 480 @86Hz

I haven't a clue what to do but it's taking me hours to navigate through a one page email due to the horrendous size of everything on the screen.

I have just taken my system hard drive out of my old dead computer and am now using the components in my signature. The old machine used a video card and now I only have onboard video capability ................. should I buy a new video card??????

---

### Post by disturbedite on 2007-11-15
typo.  should be *xserver-**x**org*.

---

### Post by tahitiwibble on 2007-11-15
Hi there Disturbed ........... that was actually a copy/paste from the Terminal window????????

---

### Post by exoren22 on 2007-11-15
> **disturbedite said:**
> typo.  should be *xserver-**x**org*.

What disturbedite is syaing is when you entered the command into the command window you typed it wrong. You didn't copy it from the command window incorrectly. 

That being said, there is usually a reason why low graphics mode kicks in, like your graphics card is not fully supported by the open drivers. Try running 
```
sudo cp /etc/X11/xorg.conf ~/corg.conf.bak
sudo dpkg-reconfigure-xserver-xorg
```
and setting it to the correct resolution. If it fails to start X after that then I suggest you come back to the forums for help on installing your correct driver.

---

### Post by tahitiwibble on 2007-11-15
Exoren22, understood for the typo, you and distubedite were dead right. However this is what I get when using  the correct command

[IMG]http://i221.photobucket.com/albums/dd79/wibble_01/Screenshot-daddad-desktop.png[/IMG]

I have no video card installed, is the onboard video on the mother board a viable proposition or should I go and buy a card?

and THANKS to both of you for the feedback

---

### Post by tahitiwibble on 2007-11-15
Well a few things have happened since my first post.

I did all kinds of research and eventually was able to designate the correct driver for my motherboards video (S3 Unichrome) .............. when I rebooted the computer the resolution defaults  to 1600 x 1200 @ 60Hz (I can't decipher anything on the screen) which is too much for my monitor that wants 1280 x 1024 @ 85Hz.

Question is ........... How can I change the screen resolution at boot up? I have booted from 7.04 cd and can adjust the resolution to whatever I desire while working from live cd. How may I change the machines resolution from the 7.04 cd so that it holds good while booting from my hard drive?

Oh if someone can get me out of really deep trouble :confused:

---

### Post by tahitiwibble on 2007-11-15
bump .................. please forgive me for doing this but I am as desperate as that

---

### Post by Qwerty_ on 2007-11-16
Ok I assume you are on the login screen where you cannot see anything.

When you are there do ctrl+alt+F1 that should bring you to a terminal screen.

From there redo reconfigure xserver-xorg and only select resolutions up to 1280X1024.

Doing this will tell the xserver to only offer you resolutions up to 1280X1024.

This should hopefully fix your problem.

---

### Post by tahitiwibble on 2007-11-16
> **Qwerty_ said:**
> Ok I assume you are on the login screen where you cannot see anything.

When you are there do ctrl+alt+F1 that should bring you to a terminal screen.

From there redo reconfigure xserver-xorg and only select resolutions up to 1280X1024.

Doing this will tell the xserver to only offer you resolutions up to 1280X1024.

This should hopefully fix your problem.

Aaaaah Qwerty, you may be saving a life here!

I can get the terminal screen like you suggested, but my keyboard quits working when I'm asked "(SUDO) password for dad :"

????

---

### Post by tahitiwibble on 2007-11-16
> **Qwerty_ said:**
> Ok I assume you are on the login screen where you cannot see anything.

When you are there do ctrl+alt+F1 that should bring you to a terminal screen.

From there redo reconfigure xserver-xorg and only select resolutions up to 1280X1024.

Doing this will tell the xserver to only offer you resolutions up to 1280X1024.

This should hopefully fix your problem.

qwerty_, this has been really helpful! Do you know which key to use to de-select 1600X1200?

---

### Post by Qwerty_ on 2007-11-16
I think its enter. if not try space or tab.

---

### Post by exoren22 on 2007-11-16
It's space.

---

### Post by tahitiwibble on 2007-11-21
I now have a completely useless computer and can no longer stop the machine from defaulting to a resolution that is not supported by my monitor .......... I really have no idea what to do .............. heeeeeeeeelp

---

### Post by tahitiwibble on 2007-11-22
I just couldn't take it any more and I ended up doing a lovely fresh install of Feisty 7.04 and everything works perfectly again ........... I will not be re-installing the update to Gutsy for quite some time to come, if ever!?

---

