---
title: "Wireless sometimes doesn't cooperate"
date: 2010-07-31
forum: Networking &amp; Wireless
---

### Post by kaldor on 2010-07-31
I've been using (solely) Linux for a few years on this laptop without problem. One night my internet disconnected on Sabayon and I assumed it was the router. 

-Then I noticed my MacBook and desktops were working fine. The wireless icon in the notification area said "Wireless is disabled".

-Then I tried out a live Lucid CD I had around. Detected wireless instantly. I backed up everything and did a clean install of Lucid. A few days later, wireless would not come on.

-Now I am on Mint 9. Wireless is always disabled by default, and in order to turn it on I have to move the slider to the Off position and then turn it back on. Lately, wireless isn't coming on sometimes and cannot be enabled. Same error; "wireless is disabled" in the GNOME panel. A reboot is the only way I could fix it.


I have a supported wireless card. It's been automatically detected by most every distro I throw at it, even some Solaris and BSD distros. I have taken the case off the back and looked at the wireless card, but nothing is loose or out of place. I'm at a loss at what to do right now.

---

### Post by digitaleagle on 2010-07-31
I am in the same boat.  My wireless has been working fine for a long time, but just the past couple of nights it quit working.  It is disabled and the option to enable wireless is grayed out.  I found a post that mentioned messing with /var/lib/NetworkManager/NetworkManager.state, but that didn't work for me.

---

### Post by digitaleagle on 2010-07-31
I found a post that made me wonder if it was the hardware switch that disables the wireless.

I just now got it working by:
- switching the switch to off
- rebooting
- switching the switch back on
Then, it started working again.

I will have to keep playing with it to see what happens.  That seems like too easy of a fix.

---

### Post by kaldor on 2010-08-01
Could this be a kernel problem? I believe Sabayon uses the same kernel version as Ubuntu.

---

