---
title: "shutter not adhering to delay"
date: 2009-07-07
forum: Multimedia Software
---

### Post by anystupidname on 2009-07-07
I'm running Shutter on Jaunty and it isn't adhearing to the delay specified. It takes the screenshot immediately, regardless of what delay is set. I'd like to capture a pull down menu on a web page but can't because of this. I also couldn't get the hotkeys to work. Any assistance on either issue would be much appreciated!

---

### Post by mario.kemper on 2009-07-08
> **anystupidname said:**
> I'm running Shutter on Jaunty and it isn't adhearing to the delay specified. It takes the screenshot immediately, regardless of what delay is set. I'd like to capture a pull down menu on a web page but can't because of this.

Shutter's delay funtionality works a little bit different from other screenshot tools. It works like this (selection mode in this example):
1) Set up a delay
[http://www.ubuntu-pics.de/bild/10892/shutter___preferences_VJrw3S.png]("http://www.ubuntu-pics.de/bild/10892/shutter___preferences_VJrw3S.png")
2) Start selection tool and select a screen region
------Now the delay takes place-------
3) Now i can do anything i want, e.g. opening a menu or move the mouse cursor to the perfect position
------delay finished----------------
4) capture

This behavior is discussed here:
[https://bugs.launchpad.net/shutter/+bug/341315]("https://bugs.launchpad.net/shutter/+bug/341315")

I think we will change this in the next version or so...

> **anystupidname said:**
>  I also couldn't get the hotkeys to work. Any assistance on either issue would be much appreciated!

Could you please provide further details? What window manager are you using? Compiz? Metacity?

Here is a little guide as well:
[http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/]("http://shutter-project.org/faq-help/set-shutter-as-the-default-screenshot-tool/")


Please let me know if you need any further assistance.

Cheers
Mario

---

### Post by anystupidname on 2009-07-13
Thanks for the reply. The way you described the delay should function is how I expected it to function. Unfortunately, it was not working that way for me.

However, after reading that bug report, I've discovered this may have just been a PEBCAK issue... I think the reason I didn't get it to work initially was because I was using the "advanced selection" method but instead of picking the area first I was trying to perform the action I wanted to take a screenshot of(stupid, I know).

I just tried to "reproduce" the problem unsuccessfully which is making me question my sanity :-& It appears to be working for me as designed now both in basic and advanced selection mode. I actually wouldn't recommend changing anything with the behavior...

Hotkeys appear to be functioning properly as well. I'm running jaunty with gnome. I'm thinking this was a fluke and maybe the window manager just needed to be restarted last time. I think I may have run an update just prior to having the problem and it required a reboot?!? Thanks again and sorry to waste your time.

P.S. You wrote as if you're one of the shutter developers. If you are, I justed wanted to stress this is an awesome utility and thank you!

---

