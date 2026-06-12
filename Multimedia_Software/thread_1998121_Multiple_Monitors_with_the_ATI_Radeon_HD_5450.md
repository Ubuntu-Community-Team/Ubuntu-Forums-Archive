---
title: "Multiple Monitors with the ATI Radeon HD 5450"
date: 2012-06-06
forum: Multimedia Software
---

### Post by Ubun2to on 2012-06-06
It took awhile, but I finally got my second monitor to work with my new ATI Radeon HD 5450. So, to help others who have the same problem, I decided to write this handy guide.
Things you will need:
1. A second monitor.
2. An ATI Radeon HD 5450.
3. A PCI slot (if your current card isn't a Radeon HD 5450 and the card is in the PCI slot, replace the current card).
4. A brain.
Ok, now lets get down to business.
1. Open terminal and type in:
```
sudo apt-get install fglrx-amdcccle
```
2. Once that has installed, you may or may not need to reboot. If you do need to, reboot. If not, continue on.
3. Open terminal and type in:
```
sudo amdcccle
```
This open up the AMD Catalyst Control Center. You will be prompted for the admin (or current account if you are admin) password.
4. Go to the Display Manager. Select the Multi-Display tab.
5. Click the box and select multiple displays. There are also options to clone the display here. You will have to reboot to apply the changes (at least, I did).
I hope this helps if you want to make a double monitor setup. I am LOVING it.
Sources:
[http://ubuntuforums.org/showthread.php?t=1835551](http://ubuntuforums.org/showthread.php?t=1835551)
Google (when in doubt, Google it)

Just remember fullscreen games will disable the second monitor, so you will have to reenable it after you exit the game (for the games I play, anyway-some may reenable it by default after you exit or just leave the second monitor on the desktop or even make use of it, but I haven't seen that happen yet).

---

