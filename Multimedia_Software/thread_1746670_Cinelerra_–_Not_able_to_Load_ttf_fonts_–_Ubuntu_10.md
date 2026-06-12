---
title: "Cinelerra – Not able to Load ttf fonts – Ubuntu 10.10"
date: 2011-05-02
forum: Multimedia Software
---

### Post by david.flights on 2011-05-02
Hello - 

I am running Ubuntu 10.10 and Cinelerra 2.15CV on a Asus eeePC 1015PE.

When I try to copy the ttf fonts over with Nautlius there the paste option is dimmed out. 

I have tried to follow the directions on the video here:

And no luck. I have also made a viedo to see the problem I'm having here:

[http://www.youtube.com/watch?v=wm770INaaXA](http://www.youtube.com/watch?v=wm770INaaXA)

Any help much apprecaited. I would love to use better fonts...

---

### Post by david.flights on 2011-05-02
SOLVED - 

Thanks to wildhostile on youtube...

sudo&#65279; nautilus

Then from the "root" I was able to copy the ttf files with no problem. 

Then

sudo ttmkfdir -o fonts.scale
sudo mkfontdir
sudo fc-cache

Open Cinelerra...and whala!

---

