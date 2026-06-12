---
title: "Cannot Burn DVD - K3B freezes"
date: 2011-12-12
forum: Multimedia Software
---

### Post by Loki*PI on 2011-12-12
I was having problems burning DVD with 10.4 and couldn't get it worked out so I did a fresh install of 11.10. Then installed K3B and burned 1 DVD successfully. The next try K3B froze at 50%, and after that it froze as soon as I click burn.

I thought maybe it was a hard ware problem so I bought a new  Samsung DVD. Tried that and K3B froze at 85%, and now freezes as soon as I click burn, same as before.

I've also tried Brasero, it never gets past calculating check sum. Same thing if I just drag files onto the DVD.

I've uninstalled and reinstall K3B several times. Also used apt-get purge and then reinstalled. No luck.

Read the "Mulitmeida & Video HowTo" and numerous threads, nothing has helped.

Anyone have any ideas?

Thanks

---

### Post by 4Orbs on 2011-12-12
Possibly your k3b tmp directory has no more room to expand because your root partition is too full.

---

### Post by Loki*PI on 2011-12-12
Thanks for suggestion. I checked. / has 28Gb. I don't see anything in /tmp that looks like it belongs to K3B.  Do you know what the file is called and it's location?

/ home has 26Gb

I've also slowed down the burn speed in case it is a buffering problem but no help.

---

### Post by 4Orbs on 2011-12-12
In the k3b configuration settings you can see what folder is specified as tmp, but that probably isn't the problem anyway. Seems odd that you were able to burn one successfully, then no more.

---

### Post by Loki*PI on 2011-12-13
thanks found it /tmp/kde-ric/  has one file in it xauth-1000-_0 size 50 bytes.  (sorry for slow response my internet connection is iffy to poor on good days.)

---

### Post by Loki*PI on 2011-12-14
I'm still trying to work this out and getting no where. Any ideas anyone?

---

### Post by 4Orbs on 2011-12-14
Since you are sometimes able to start the burn and get part-way through it, I suspect a hardware problem... but not with the burner. Maybe overheating or the power supply is dying. Are you still able to play dvd's from beginning to end?

If this is a laptop: are you trying to burn using battery only? Try plugging in the ac adapter before burning and see if it makes any difference.

---

### Post by bluexrider on 2011-12-14
> **4Orbs said:**
> Since you are sometimes able to start the burn and get part-way through it, I suspect a hardware problem... but not with the burner. Maybe overheating or the power supply is dying. Are you still able to play dvd's from beginning to end?

If this is a laptop: are you trying to burn using battery only? Try plugging in the ac adapter before burning and see if it makes any difference.
you might want to install another burning software to find if the same problem exits

---

### Post by Loki*PI on 2011-12-17
I'm still trying to resolve this:  

I find that if I use DeVeDe and convert an avi file to and iso, at the end of the conversion there is an option to burn. If I select that Brasero comes up and will successfully burn the ISO to DVD.

If I just launch Brasero it freezes at check sum, and K3B freezes as soon as I click to burn.  

Apparently the hardware is fine, but there is some problem on the software side. Brasero will burn successfully if it is called out by DeVeDe but not when launched independently. 

Anyone have any ideas. I need to burn some data DVD for storage and backup. Thanks

---

### Post by Loki*PI on 2011-12-26
After trying everything I read about or thought of, none of which helped, I added memory to the system.  I'm now able to burn using K3B, no problem. I've made 9 DVDs no issues. Anyone else has this problem, try adding memory.

---

