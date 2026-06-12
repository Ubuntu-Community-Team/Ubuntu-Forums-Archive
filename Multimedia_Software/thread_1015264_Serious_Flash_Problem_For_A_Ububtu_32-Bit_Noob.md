---
title: "Serious Flash Problem For A Ububtu 32-Bit Noob"
date: 2008-12-18
forum: Multimedia Software
---

### Post by Auborine on 2008-12-18
Hello, 

The problem I'm having is that I cannot get Flash 10 to work at all or any flash for that matter. Ive done a lot of surfing on these boards over the past few days and I cannot seem to come up with a solution. Let me start with what I've tried. I did go to the adobe site and download the .deb file and it runs threw the package manager and says its been installed but it really isn't working or didn't install. Every time I try to re-download and install again it just says to re-install the package. Ive also tried using the about:plugins command. I don't see any plugins at all on the page. When I go to Edit/Prefrences/Applications everything is under Use Movie Player (Default).

Any help with this matter would be greatly appreciated. Im just not used to Linux at all and would love to give this OS a shot. 

Thank You, 

-Auborine

---

### Post by gnicko on 2008-12-19
I had the same problem. Seems that there are "too many Flash players" installed by default. There's probably a better way to do it, but what I did to get Flash working (with FireFox) was to remove everything having to do with Flash (including the Ubuntu restricted packages, etc.) through the package manager, and then re-install only the Flash 10 ".deb" package from Adobe.

It works. Like I said, there's probably a better way, but I was in a hurry.

---

