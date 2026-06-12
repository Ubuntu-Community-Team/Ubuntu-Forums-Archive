---
title: "Karmit with Atheros AR5001X+ WLAN Chip cannot recognize all WLANs"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by bbruecker on 2009-10-29
Hey,

Strange behavoir after Updating to Karmic/9.10, 64Bit: The network manager isn't able to connect to my WLAN with Karmic. The network-manager is displaying some WLANs but not my own. The network is not hidden. Jaunty on the same computer displays more WLANs and is able to connect to my WLAN.

I thought Karmic had improved hardware support? In that case the situation is not an improvement.

Chipbset is as described in the title.

Any suggestions how to fix that problem?

Thx, Benjamin

---

### Post by t0mppa on 2009-10-29
One simple thing to check would be whether you're searching all the wireless channels available at your location (1-11 in US, 1-13 in Europe, 1-14 in Japan, no unified standards for rest of the world). You can run **iwlist channel** on terminal to find out which channels your system is scanning. If it only checks 1-11 for instance, then naturally any networks outside them are not getting recognized.

---

### Post by bbruecker on 2009-10-30
Thank you t0mppa!-This advice saved me for sucking in driver issues (that was my idea). My router was set to channel 13 and this channel had not been scanned.

BTW: Do you know a way how to change the settings in a way that the driver scans European channels too?

Thx, Benjamin

---

### Post by t0mppa on 2009-10-30
Yeah, it's something people don't usually think of and naturally trying to fix it driverwise is not going to work.

As for how to change the setting, that is a very good question. The old way was to create (or append, if it already exists) */etc/modprobe.d/options* file with the line [b]options cfg80211 ieee80211_regdom=EU
[/b] in it (one user that I helped earlier also had to add a **options mac80211 ieee80211_regdom=64** line).

On the hand, the 9.10 release notes state that this should not be done anymore and that the **iw reg set <your_two_letter_country_code>** be used instead. Only the issue is that at least on my Karmic, iw has not yet replaced iwconfig and thus it isn't even installed on the system.

So, I guess it's your choice which way you choose to go. The former worked well, at least on Jaunty, but it isn't in accordance with standards, since then you'd be roaming as a citizen of EU and EU isn't a country. The latter is the new way to go, but apparently it didn't make it all the way to Karmic default package, like it was supposed to and thus majority of Ubuntu users will likely be referring to iwconfig instead of iw for yet another 6 months at least, thus turning the leading edge into bleeding edge, if you get the nuance.

---

