---
title: "Wireless can't connect in Ubuntu 10.10"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by jedimattk on 2011-02-20
I installed Ubuntu on my laptop at a friend's house. After installing, I connected perfectly to their wireless network and lived quite happily for a few days. However, when I arrived home and tried to connect to my own network, my computer insisted that it couldn't connect. Although I'm sure I'm entering the right pass key, it keeps asking for the passkey ad nauseum. What am I doing wrong, guys?

---

### Post by chessnerd on 2011-02-20
You can try **sudo apt-get install linux-backports-modules-wireless-maverick-generic** to see if that fixes it. This will install newer drivers that, while unsupported in your current release, may help fix your current situation.

I've found that wireless is one of the things that improves with each new version of Ubuntu. My laptop's card had next to no support in 9.04 ([which prompted me to try backports]("http://ubuntuforums.org/showthread.php?t=1370157&p=8599246")), but works great with 10.04. I expect the results will be similar with you. You could even try out the Natty Alpha on a LiveCD to see if that works.

If that isn't the issue, then my thoughts turn to wireless-N. If your computer has a wireless g/n card, it is possible that Linux only supports the wireless-G functionality, which is fine in most cases. However, if your house only has wireless-N, then Ubuntu could be failing because of this. If that is the case, then you'd need to enable wireless-G on your wireless router (which should be an available option).

EDIT: Also, you might need to enable the backports repository under System > Administration > Software Sources > Updates to be able to download these drivers.

---

### Post by PaulReaver on 2011-02-20
also make sure its in the correct case.... ubuntu is awfully pedantic about upper and lower case letters.....

I actually did this once :-$

---

### Post by jedimattk on 2011-02-20
Nope, I have wireless-G at both places, and I've double-checked the case of the passkey. It doesn't seem like a driver issue, since it was working perfectly before, no issues whatsoever. In any case, I can't apt-get the new drivers (for obvious reasons.) :S

---

### Post by chessnerd on 2011-02-20
It is quite possible that it isn't a driver issue, and that reminded me of [a problem I had last year that then lead to the wireless not working]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1405948") where the solution was to restart the router. I banged my head against the wall in the same situation you were in until it dawned on me to just unplug and replug the wireless router. After that, presto, I had Internet access. Have you tried that?

And yes, in order to apt-get, you will need an ethernet connection... :)

---

