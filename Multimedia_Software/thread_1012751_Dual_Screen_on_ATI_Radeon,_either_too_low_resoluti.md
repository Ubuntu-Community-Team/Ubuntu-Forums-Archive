---
title: "Dual Screen on ATI Radeon, either too low resolution or only cloned possible"
date: 2008-12-16
forum: Multimedia Software
---

### Post by wimmelis on 2008-12-16
Dear all, 


After two days of struggling, this newby is running out of ideas, so I hope someone can help me with this problem. 
Apologies if the post is long, though I like to give the story, so I do not get proposals on things already tried. 

Configuration: 
OS: Ubuntu 8.10 64-bit
Graphics card: ATI Radeon HD 2400
Screens: LCD1: 1920x1200 and LCD2: 1680x1050.

I have tried the methods as presented on: [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Method 1:
I initially tried the ATI drivers option (since I had that working on my Ubuntu 8.04, but that got screwed up when I wanted to update the ATI drivers, and then I spend about one day trying to solve things to get to my current status, since I could not get any driver to work then).
So, the software installs nicely, but if I switch it on, then I drop back to a resolution of 1024x768. If I change my aticonfig to support big desktop, then it works from the ati catalyst centre, when I log out and log in again, then I again have a cloned display, eventhough my xorg.conf is set to the big desktop. 
What I tried:
1) add the pairwise modes, in relation to my LCD resolutions, but aticonfig mentions them to be not supported as soon as I enter them on the command line, I also tried to add them to xorg.conf immediately, no effect.
2) tried to set modes for the separate screens, does not make a change either

The ati catalyst centre, does not seem to detect my lcds correctly and I also tried to reinstall the ati drivers, though without any effect. 

I do not like to try installing the ati drivers from their website directly, as that is what started all the problems, the install did not seem to finish, but seemed to manage screwing up my system :(

Method 2:
I partly swapped to 8.10 because of the dual display support, so I tried the Mergedisplay part, again as mentioned on the above thread, though without much effect. 
When using this standard driver, I manage to get one screen to work at its normal resolution, but I do not manage to get the two displays to form one big display, they remain clones. 
I tried:
1) different configurations on the left and right, since I do not know what my primary is
2) the non rectangular, since that would be necessary since my screens are not same resolution. 


Anyone, who managed reading till here, well thanks for that, have any suggestions.


Many thanks, 

WM

---

### Post by wimmelis on 2008-12-17
Dear all, 


Well, no solution was found, so eventually I went for a complete reinstall, and guess what, the ATI drivers then worked like a charm and my dual screen worked in a matter of minutes (in comparison to the days of trying before that).

Conclusion:
1) Sometimes a complete reinstall is much faster than trying to fix something which is broken, but you just can't figure out where ...
AND 
2) Avoid updating your ATI drivers thinking their script will deal with decent removal of the old driver and then installing the new one.


Regards,

WM

---

