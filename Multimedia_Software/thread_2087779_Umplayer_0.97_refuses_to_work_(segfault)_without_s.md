---
title: "Umplayer 0.97 refuses to work (segfault) without sudo from console"
date: 2012-11-24
forum: Multimedia Software
---

### Post by Ekeluo on 2012-11-24
Umplayer refuses to start (no ui response) when i click on the icon. When run from a console, it consistently segfaults after about 5 seconds. However it works ok when i run it with elevation (sudo umplayer). Remembers previous settings, plays files just fine. Just doesn't start without sudo. Any help will be appreciated. Running 12.10, upgraded from 12.04

---

### Post by monkeybrain2012 on 2012-11-24
Switch to smplayer which is under active development and umplayer is mostly a fork of it. Umplayer as a project seems to be dead and the developer has not returned any email more than a year ago. I am surprised that it still works (seems once in a while some users contribute a patch to fix Youtube and that's it, it has been stuck at version 0.97 since 2010 or 2011)

But you may have other problems due to your upgrade. If you start umplayer in the terminal (without sudo) what are the error messages?

---

### Post by andrew.46 on 2012-11-24
Nice new version of SMPlayer out btw, you can get this by running the following in a terminal window:

```

sudo add-apt-repository ppa:rvm/smplayer && \
sudo apt-get update && \
sudo apt-get -y install smplayer smtube smplayer-themes

```

Good to see SMPlayer well and truly on the move again...

---

### Post by Ekeluo on 2012-11-25
Sorry for my late reply, internet's a bit scarce for me right now. I've installed SMPlayer and it works, though for some reason it wont let me use the skins. Oh well...
Anyway, the response from umplayer on the terminal is:

```
ekeluo@klez-Compaq-Presario-A900-Notebook-PC:~$ umplayer
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 9: reading configurations from ~/.fonts.conf is deprecated.
This is UMPlayer v. 0.98.1 running on Linux
Segmentation fault (core dumped)

```

Other problems include programs (mainly KDE core such as gwenview, kmix, plasma) crashing when they are closed (via proper procedure), and on every logout/shutdown. Irks, but I live with it.

P.S. One new this evening: updated some gtk3.0 stuff, oxygen-gtk is now awry, painting every application a flat black.

---

### Post by monkeybrain2012 on 2012-11-25
Yeah umplayer is based on Smplayer with some minor tweaks (the most prominent new feature is Youtube player which has since been incorporated back to Smplayer) The "~/.fonts.conf is deprecated"error is apparently a bug in Smplayer which I also experienced may be a week ago, but it has been fixed in rvm's ppa so it works now. Unless someone patches Umplayer doubt that it will ever work again (If you install Umplayer through the webupd8 ppa the maintainer may do it and release a patched update) No idea why Umplayer segfault though.

Don't know about skin, it seems to be a new feature I only get in the most recent update, may have some bugs. You can post a thread on the Smplayer forum.[http://smplayer.sourceforge.net/forum/](http://smplayer.sourceforge.net/forum/)

Can't help with kde stuffs crashing, I don't use kde.

---

### Post by Ekeluo on 2012-11-26
Actually, I just copied the skins from the umplayer themes folder (/usr/share/umplayer/themes) into the equivalent for smplayer and the skins work just fine!
Thanks anyway, uninstalled umplayer now.

---

### Post by monkeybrain2012 on 2012-11-26
An update.

I tried the Smplayer skin and it works perfectly. Open  Smplayer and go to Options > Preferences > Interface  and from the box GUI choose Skinable GUI.

It seems that rvm (the developer for Smplayer) has taken up the job of maintaining and upgrading Umplayer as well (at least for Ubuntu users) I just noticed that Umplayer 0.98 is in the rvm ppa (the Smplayer ppa)

---

