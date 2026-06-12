---
title: "TV-Out (SVideo) Pain in the butt"
date: 2008-11-07
forum: Multimedia Software
---

### Post by sinclair86 on 2008-11-07
Let me just say that this is probably the most frustrated I've ever been with linux. I have a Radeon 7200 (r100) graphics card on my ubuntu 8.04 computer. After much searching I come to the conclusion that is probably one of the worst graphic cards to have because it really isnt supported at all. Ive tried ati drivers but the restricted ones dont support it cause its too old hence why when i tried envy is why it didnt work. ATITVOUT doesnt support it which is good I guess cause that seems to be a dead project. Tried GATOS but after much reading I realized that was a dead project and Xorg had taken it over and it had become part of xrandr which doesnt work it detects my cards but not my svideo port. Ive tried ubuntu help on radeon drivers and that didnt work either which was good because it crashed X when i rebooted and said it couldnt detect my card so from the list that came up I tried ati fglrx radeon(fglrx)... etc the only 2 that worked when i hit test were the vesa one and the radoen on and to my surprise the radeon works for TV out but the display on the tv is a little shaky and the color isnt as bright. I know this has to do with xorg.conf file but i'm really just tired of trying to figure this out on my own. spent 19 hrs in the past 2 days working on this and my gf is starting to get pissed at me.

---

### Post by sinclair86 on 2008-11-07
Ok so I figured out the color thing... someone had changed the color settings on the TV. But I am still having trouble with the xorg.conf file right now the monitor and tv are the same when I try to change it it doesnt seem to stick or work.

---

