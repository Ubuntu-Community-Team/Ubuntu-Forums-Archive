---
title: "Processor load of Xorg"
date: 2008-11-02
forum: Multimedia Software
---

### Post by pitris on 2008-11-02
Hi,
after upgrading to 8.10 Xorg process started to load my processor (P4 2.4GHz) more than I was used to. With all apps closed, static desktop - nothing is moving - it takes about 5%. In 8.04 it was 0%. When there is a little animation (like seamonkey logo while loading a website), it can be even 50%. What could go wrong? I'm using radeon driver, my card is ATI Mobility Radeon 9000 (ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)).

Also, when I press ctrl+alt+f1 to terminal and ctrl+alt+f7 back to X, an ugly weird bar of random pixels is left at the top of the screen. It was the same in 8.04, but after some seconds it disappeared. Now it stays there until I erase it with moving some window over this bar. How can I fix this?

---

### Post by kerry_s on 2008-11-02
> **pitris said:**
> Hi,
after upgrading to 8.10 Xorg process started to load my processor (P4 2.4GHz) more than I was used to. With all apps closed, static desktop - nothing is moving - it takes about 5%. In 8.04 it was 0%. When there is a little animation (like seamonkey logo while loading a website), it can be even 50%. What could go wrong? I'm using radeon driver, my card is ATI Mobility Radeon 9000 (ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)).

Also, when I press ctrl+alt+f1 to terminal and ctrl+alt+f7 back to X, an ugly weird bar of random pixels is left at the top of the screen. It was the same in 8.04, but after some seconds it disappeared. Now it stays there until I erase it with moving some window over this bar. How can I fix this?

those are the symptoms of a bad driver. try switching to vesa and see if you get those symtoms. if it runs fine with vesa you most likely just need to turn on a option or few for the radeon driver.
try the stock ati driver as well.

---

### Post by pitris on 2008-11-02
Hello,
I tried "ati" driver, but it's the same as "radeon".
For "vesa" it works fine, but it ran only in 800x600 and I wasn't able to force it to use 1400x1050 which is my default.
I also wanted to try fglrx but it seems that my card is too old and not supported.
Which options for radeon do you mean?

---

### Post by pitris on 2008-11-02
And one more thing: if mplayer is playing mp3 in terminal and you see the numbers running, it takes 100% of CPU. That's not nice...

---

### Post by kerry_s on 2008-11-02
> **pitris said:**
> Hello,
I tried "ati" driver, but it's the same as "radeon".
For "vesa" it works fine, but it ran only in 800x600 and I wasn't able to force it to use 1400x1050 which is my default.
I also wanted to try fglrx but it seems that my card is too old and not supported.
Which options for radeon do you mean?

i'm not really to familiar with radeon, i switched to nvidia years ago and haven't looked back.
try some of the options on this page:
[http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver](http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver)

check your /var/log/Xorg.0.log for clues.

---

### Post by pitris on 2008-11-03
I found out the following interesting thing:
When I stop gdm and start X manually (startx), everything is fine. I have xterm and openbox in .xinitrc only. Then I can do whatever I want and Xorg process load never increases. So it must be a problem with something connected with gdm or gnome. How can I debug this?

Visual efects are set to none and cannot be even started.

---

### Post by pitris on 2008-11-03
Fixed! I was wondering why I am not able to start visual effects. I downloaded compiz-check and it told me I had another composite manager running, the GNOME's one. I stopped it and since that time there's no CPU huge load.

---

