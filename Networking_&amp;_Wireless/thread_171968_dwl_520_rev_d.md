---
title: "dwl 520 rev d"
date: 2006-05-07
forum: Networking &amp; Wireless
---

### Post by quadz0 on 2006-05-07
I have the D-Link DWL revision D wireless card. I have tried ndiswrapper, netowrk manager severla times and they never work. I have reinstalled 3 times in the past 2 days. I'm really frustrated as how to get this piece of **** to work. Does anyone have any suggestions?

---

### Post by DarkStarDeity on 2006-05-07
I had similar frustrations getting my G520+ card working, as described [here]("http://www.ubuntuforums.org/showthread.php?t=170594"). My experience leads me to believe that the Network Manager GUI utility does not work correctly with these cards, and you need to use the command line utilities. 

My suggestions -
1) If you are able to, (re)install the breezy distro. This solved my initial connection problems out of the box, then I just needed to use the command line utils to set up WEP. You didn't meantion which distro you have installed, so forgive me if this is the one you are already using.
2) If this is not possible, set up ndiswrapper again, then try using the commands ifdown and ifup to reset the connection rather than the GUI. The man pages for these commands are pretty clear. If the commands don't work, try rebooting (even now, I sometimes have times when rebooting is the only way to re-establish a connection, a problem I also had with the card when it was in a Windoze box). Caveat - I haven't actually gone down this path myself so can't guarentee it will work, but I'm extrapolating from my own experiences.

Hope that helps. If there is one thing this has taught me, it's that I won't be buying hardware from D-Link or any other vendor that does not either supply linux drivers, or at the very least disclose the interfaces so that others may write them. Greedy bastards may have "protected" their IP, but they've lost themselves a customer. For life.

---

### Post by quadz0 on 2006-05-07
Yea im running breezy, i even tried using the original drivers from the cd through ndiswrapper, but it comes out and "Invalid Driver!" I think im going to try a different card or get a wired connection. I still want to get this to work, but i want internent more, so...

---

