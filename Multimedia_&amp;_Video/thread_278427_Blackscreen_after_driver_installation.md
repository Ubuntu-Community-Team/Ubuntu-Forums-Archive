---
title: "Blackscreen after driver installation"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by tAno on 2006-10-16
Hello! I'm compleatly new to linux and found this distro to be the best for my use... however:

After I installed the ati gfx driver
```
(ATI Proprietary Linux x86 Display Drivers for XFREE86 / X. Org Version 8.29.6)
``` 

... I ran this command in the terminal:

```
sudo aticonfig --initial
```

And that worked well I guess =), but when I restarted the computer, I couldnt get further than after the ubuntu-loading thingy, at the point the resolution was about to change... It all went black. the computer just stops working... 

what should I do? The same thing happed when I first tried the live cd...It went black if I didnt chose safe graphics mode.

I have ATi Asus X800XT PE 256MB, And I read about the: ATi + Linux = Not True... :/

I would really appriciate a fast reply, tyvm =)

---

### Post by igknighted on 2006-10-16
did you install with the drivers from the website?  Or did you use the ati drivers from the repository?  If you used the one from the site I would recommend uninstalling it and installing the driver from the repo.  I have an x800 as well and I use the xorg-driver-fglrx package from the repository via apt and it works perfectly.

---

### Post by tAno on 2006-10-16
uhm... ya, I just reinstalled ubuntu and tried once more time using this driver: ```
http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide
```

Absolutely same result, back screen. Got it like 2min ago :(

Anything else I could try? I really dont want to ditch ubuntu...then to install xp again :(

I believe the xorg file has something to do with it. because the blackscreen wont show up if I dont run the

```
sudo aticonfig --initial
```

but then, If I dont run it, I dont get the driver to work...

---

### Post by tAno on 2006-10-16
bump!?

:sad: [-o<

---

### Post by tAno on 2006-10-17
Why cant anyone help me? :(

I'll go for windows again tho.. :/

igknighted... how can I give you some rep points..or w/e.. =)

---

