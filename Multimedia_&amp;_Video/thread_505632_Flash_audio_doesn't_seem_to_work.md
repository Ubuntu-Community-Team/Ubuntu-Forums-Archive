---
title: "Flash audio doesn't seem to work"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by outlandish on 2007-07-20
Well, I've recently switched to ubuntu, and I've found everything to my liking except for one thing-- audio simply doesn't work in flash files-- be they youtube videos, ads, or games. The visual element of the flash appears fine, and functions as it would normally; there just isn't any sound. Any help on this issue would be appreciated.

---

### Post by stchman on 2007-07-20
> **outlandish said:**
> Well, I've recently switched to ubuntu, and I've found everything to my liking except for one thing-- audio simply doesn't work in flash files-- be they youtube videos, ads, or games. The visual element of the flash appears fine, and functions as it would normally; there just isn't any sound. Any help on this issue would be appreciated.

I assume you are talking about Flash using Firefox?  If so I watch youtube videos all the time and the audio always works.

---

### Post by Gremlinzzz on 2007-07-21
Note: if sound doesn't work in Flash Player (for example on YouTube):
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
Change:
FIREFOX_DSP=""
To:
FIREFOX_DSP="aoss"
Restart Mozilla Firefox. Now sound should work in Flash Player.
this is from ubuntu guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

---

### Post by jslmg on 2008-01-17
> **Gremlinzzz said:**
> Note: if sound doesn't work in Flash Player (for example on YouTube):
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
Change:
FIREFOX_DSP=""
To:
FIREFOX_DSP="aoss"
Restart Mozilla Firefox. Now sound should work in Flash Player.
this is from ubuntu guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Did this, and it had no effect. Is there a similar, but different, fix for Gutsy?

---

### Post by jslmg on 2008-01-17
> **jslmg said:**
> Did this, and it had no effect. Is there a similar, but different, fix for Gutsy?

Flash audio problem in Gutsy now solved. If you have no audio with Flash in gutsy, download this plugin:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bugs page.

---

### Post by niceguy123 on 2008-01-19
> **jslmg said:**
> Flash audio problem in Gutsy now solved. If you have no audio with Flash in gutsy, download this plugin:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bugs page.

I tried this and it seems the same.

---

### Post by niceguy123 on 2008-01-19
> **Gremlinzzz said:**
> Note: if sound doesn't work in Flash Player (for example on YouTube):
sudo apt-get install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
Change:
FIREFOX_DSP=""
To:
FIREFOX_DSP="aoss"
Restart Mozilla Firefox. Now sound should work in Flash Player.
this is from ubuntu guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Tried this too, doesn't seem any better. I have sound just very low.

---

### Post by jslmg on 2008-01-20
> **niceguy123 said:**
> I tried this and it seems the same.

You might also try ```
sudo apt-get install libflashsupport
``` and see if that one works for you...

---

### Post by Azyx on 2008-01-21
> **jslmg said:**
> Flash audio problem in Gutsy now solved. If you have no audio with Flash in gutsy, download this plugin:

[http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb](http://www.paulbetts.org/projects/libflashsupport_1.0~2219-2_i386.deb)

Found at Launchpad bugs page.

THANX! It worked fine on Gutsy =) After trying a lot of another things.

---

### Post by rare HERO on 2008-01-21
> **jslmg said:**
> You might also try ```
sudo apt-get install libflashsupport
``` and see if that one works for you...

```
$ sudo apt-get install libflashsupport
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libflashsupport

```

---

### Post by BobLand on 2008-01-21
jslmg,
Just tried this and fixed my problem!

Many thanks,
bobland

---

