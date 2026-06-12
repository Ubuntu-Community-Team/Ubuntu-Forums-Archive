---
title: "Frequently being disconnected from my wireless network.."
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-11-19
Running 9.10 (update, no problems/errors while upgrading..)

If i leave the room, and wait till my screensaver starts up.. (10 mins later) I come back, and I get a prompt asking me for my networks password.. though, I already have it set up *correctly* on my connections..

It still asks for my password.. as if it had forgotten or was using the wrong password.

Also, moblock could be playing a role?
I doubt, since it's still connected.. it only goes out everytime I'm not watching it.
(it's not going into hibernate nor suspend)

Thanks in advance for helping me out.

---

### Post by jessiebrownjr on 2009-11-19
This may or may not be helpful but... I installed a new atheros card and used a custom set of drivers on my new atheros card... after this, i started getting random DCs too.. apparently there isn't an algorythm in there for eliminating noise, so it DC's because of that sometimes...

Possible that you are running weird drivers as well?

Also, if you are too close to the AP, that can cause problems too I think

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-11-20
My guess by AP is airport? No, it's like 20-30 miles away..
I'm not sure what drivers I'm using.. It's a the on-board wifi that's in my Acer extensa 4630z

But you see, I've been on my laptop for 30 mins straight.. no DC..
If i leave and come back, and move my mouse, the screen turns on and their is a lovely prompt for my key.

Makes downloading torrents a pain.

---

### Post by drseuk on 2009-11-20
> **&#999 said:**
> Running 9.10 (update, no problems/errors while upgrading..)

If i leave the room, and wait till my screensaver starts up.. (10 mins later) I come back, and I get a prompt asking me for my networks password.. though, I already have it set up *correctly* on my connections..

It still asks for my password.. as if it had forgotten or was using the wrong password.

Also, moblock could be playing a role?
I doubt, since it's still connected.. it only goes out everytime I'm not watching it.
(it's not going into hibernate nor suspend)

Thanks in advance for helping me out.

I concur. This is definitely a bug in the (9.10) release. Re-booting tends to fix it but for obvious reasons this is less than ideal.

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-11-21
By bug in 9.10 do you mean like a bug while upgrading? Or would this issue be solved with a fresh install?
It seems when the screensaver starts it stops the internet?

---

### Post by cpetercarter on 2009-11-21
Have you tried changing the channel on your wifi router? I was experiencing big problems with my Acer Aspire One - repeatedly asking for the wifi password, taking a long time to connect, taking even longer to download a web page. Tried a variety of drivers - no improvement. Changed the wifi channel - magic! It all works!

---

### Post by &#999;&#978;&#625;&#595;&#9786;l on 2009-11-21
> **cpetercarter said:**
> Have you tried changing the channel on your wifi router? I was experiencing big problems with my Acer Aspire One - repeatedly asking for the wifi password, taking a long time to connect, taking even longer to download a web page. Tried a variety of drivers - no improvement. Changed the wifi channel - magic! It all works!

Guess I forgot to mention that.. I did have it on auto, switch to channel 11 then to 6 then to 1.. no luck.

---

### Post by RodGer GR on 2009-12-17
I have the same problem on a clean installation (not an upgraded older one) but there are also other problems when I'm inactive. The clock slows down or stops refreshing, the cursor stops blinking and generally, everything seems to slow down e.g. downloading, copying files ...

---

