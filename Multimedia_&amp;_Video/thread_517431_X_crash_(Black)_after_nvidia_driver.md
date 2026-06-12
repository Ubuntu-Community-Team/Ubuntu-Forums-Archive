---
title: "X crash (Black) after nvidia driver"
date: 2007-08-04
forum: Multimedia &amp; Video
---

### Post by hbayar_morph on 2007-08-04
Few hours ago I installed Ubuntu 7.04(64bit).

After this I added extra repositories from [here]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

Then I updated.

And then I enabled "Restricted Driver" (nVidia 7600GT). System says "Restart X" And I did.

While restarts I saw "Ubuntu" splash screen, then screen goes blank, but I can hear the system "log on" sound. So I thought it's nvidia driver crash.

Lucky I, ctrl+alt+f1 works, then I typed

sudo dpkg-reconfigure -phigh xserver-xorg.

And then I logged on. I've tried to install nvidia driver with "Envy", "Automatix2" there all crashing...

I almost giving up :( Everything was OK before (2monts ago), but now same PC, same DVD.

Any idea?

---

### Post by NT4usB on 2007-08-04
I just installed a 7600 GS using envy and it worked great.
Since it is a fresh install, I assume that envy is the latest. If not, uninstall it and download the latest.
When you ran it, did you first choose the option to uninstall the existing drivers. Then select install?
Can you Ctrl+Alt+F1, log in and edit your xorg to vesa or nv and startx?

---

### Post by hbayar_morph on 2007-08-07
Tnx for reply :)

Yes, i did uninstall, also I had fresh install with "envy" they're all same :(
when screen goes black I can hit Ctrl+Alt+F1 and screen comes back in text mode(of course text mode, lol).

Now I'm gonna try again, New install, and I'll start with "envy". If it is not gonna work again I will leave it untill next nvidia update.:twisted:](*,)[-o<

---

### Post by hbayar_morph on 2007-08-07
Btw, I also tried in PCLinux OS. X crashed when I install nvidia driver, exactly same.

But in ubuntu 6.06 (Dapper Drake) was OK. I installed nvidias latest driver without problem. :?

---

### Post by hbayar_morph on 2007-08-08
I think I found where is the problem. After fresh Ubuntu install+fresh nvidia driver (usually) X crashed again. I changed the Dual Link DVI cable to Single Link DVI, now it's ok, I can see my desktop, but I want to use Dual Link DVI, cuz my screen 2048 x 1536, single link doesn't support 2048 x 1536. :( Anyone know how to fix it?

---

### Post by tseliot on 2007-08-09
Try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

