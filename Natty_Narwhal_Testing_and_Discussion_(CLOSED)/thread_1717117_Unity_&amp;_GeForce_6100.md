---
title: "Unity &amp; GeForce 6100"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by uRock on 2011-03-29
With the past two releases of Ubuntu I have not been able to enjoy compiz and all of its glory. 

I have an nVidia chipset and the recommended driver installed and every time I set Visual Effects to Normal or Extra they work until the next restart when it reverts back to None. Does this mean Unity will not run on my machine?

Results of lspci```
uRock@uRock:~$ lspci
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
```

I ask this because I love Ubuntu and want to see it at its prime, but I don't want to upgrade just to find that I am stuck with the classic desktop.

Thank you for any and all thoughts on this.

---

### Post by lucazade on 2011-03-29
> **uRock said:**
> With the past two releases of Ubuntu I have not been able to enjoy compiz and all of its glory. 

I have an nVidia chipset and the recommended driver installed and every time I set Visual Effects to Normal or Extra they work until the next restart when it reverts back to None. Does this mean Unity will not run on my machine?

Results of lspci```
uRock@uRock:~$ lspci
00:05.0 VGA compatible controller: nVidia Corporation C51G [GeForce 6100] (rev a2)
```

I ask this because I love Ubuntu and want to see it at its prime, but I don't want to upgrade just to find that I am stuck with the classic desktop.

Thank you for any and all thoughts on this.

You should be able to use Unity in Natty.
The problem you have with previous release seems related to gconf registry that doesn't save properly a key.

launch "gconf-editor" and look in
desktop -> gnome -> session -> required_components

"windowmanager" key should have as value "metacity" or "compiz"

try to enable compiz from Visual Effect tabs and you'll see this key in gconf switching from metacity to compiz.. if it doesn't switch means gconf is broken in some way and revert to metacity at reboot.

---

### Post by uRock on 2011-03-30
It says compiz even before making changes to Visual Effects(marked as None).

I guess it'll be a game of wait and see.

---

### Post by mc4man on 2011-03-30
Not sure how well that chipset would work with nvidia-current in natty, guess you wouldn't know till you tried. (would think better suited to a legacy driver
Previous to natty never did bother with the Appearances >  visual effects options, just left blank, installed ccsm and enabled/disabled from there. (though I always have had AGP or PCI-E cards.

Anyway, depending on hardware and use nouveau with the mesa 3d drivers is vastly improved in natty, was almost ok on a large HD lcd and not bad at all on a laptop, though am now using nvidia because I can and it's better.

(there's also the current issue of mem use with nvidia, though there will be a resolution one way or the other in near future

---

### Post by cariboo on 2011-03-30
The 6100-6150 chipsets have always been strange as far as I'm concerned, I've had 3 motherboards with them, and all of them needed either safe-mode or nomodeset enabled before I could boot to a desktop with the Live CD this is going back to 7.04. I haven't tried since Lucid, because I bought add-in cards specifically a 8400GS, a 9400GT and a GT210 so that I didn't have to deal with the weirdness any more.

You shouldn't have to, but if you are having problems, install nvidia-current, then run nvidia-xconfig to see if that helps.

I did a test install this afternoon on a system with a GT6600, Additional drivers gave me the choice of either nvidia-current or the experimental 3D open source driver, I chose the experimental drivers, and Unity started right up with having to do a reboot after the driver were installed.

---

### Post by uRock on 2011-04-05
I am kicking myself for not replying sooner. I created a est install of Natty, installed the experimental driver and Unity has worked pleasingly well.

I shall receive lashings for ever doubting the devs.:twisted:

---

