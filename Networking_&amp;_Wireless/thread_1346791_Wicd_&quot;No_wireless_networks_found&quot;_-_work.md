---
title: "Wicd &quot;No wireless networks found&quot; - worked yesterday?"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by beefjerkymonster on 2009-12-05
Hey everyone, I've been using wicd very successfully for months now. I use Ubuntu Karmic 64bit.

Anyway, all of a sudden last night I open up wicd and get the message "No wireless networks found". Weird, so I restarted the computer. Same thing. After a few more tries, I plugged into an ethernet cable and ran a bunch of updates. I decided to try using the latest wicd 1.6.2 from wicd's repos. Same thing.

I can connect using network-manager. I've reinstalled it a couple times while trying to reinstall wicd... each time network-manager works, but wicd doesn't......

'iwlist wlan0 scan' gives me all the networks I should see. Why is wicd unable to see them?

I am unable to use network-manager, as I play internet based FPS games frequently, and for some reason I get strange lag with network-manager that makes the games unplayable.

Edit: You guys might want to know more about the comp.. it's an ASUS laptop, F50sv-X1. Wireless card is AR928X, using the ath9k module with module-backports installed.

SOLUTION: Well, after some reading online, I looked into the preferences on Wicd, and noticed that the "Wireless Interface" box was empty. I entered 'wlan0' (my wireless interface, yours may be different), and it works just fine.

---

