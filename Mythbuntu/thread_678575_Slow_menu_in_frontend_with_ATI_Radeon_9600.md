---
title: "Slow menu in frontend with ATI Radeon 9600"
date: 2008-01-26
forum: Mythbuntu
---

### Post by DouglasK on 2008-01-26
If you've installed MythBuntu 7.10, (as downloaded from [http://mythbuntu.org](http://mythbuntu.org)) you may see that the menu's on the frontend are quite slow when used with an ATI Radeon 9600 card.  I was seeing a delay of about 1 second between key press and the menu option being selected.  This is on an Athalon 2800 with 1.5Gb ram... so the system wasn't slow.  :-)

The problem is that glx direct rendering isn't enabled in mythbuntu by default with (some?) ATI Radeon cards.

To enable it, type this at a command prompt:
```
sudo aptitude install libgl1-mesa-dri
```That did the trick for me at least.  Now all menus respond quickly.

~~Douglas

---

