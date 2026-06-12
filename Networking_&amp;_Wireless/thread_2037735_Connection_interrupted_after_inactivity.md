---
title: "Connection interrupted after inactivity"
date: 2012-08-05
forum: Networking &amp; Wireless
---

### Post by Galdov on 2012-08-05
Hi, im sorry but i didnt find it in the forum, if this is already posted give me the link :D

I have a netbook with Ubuntu 10.04 (Atom N450, 1GB, GMA3150)

In *Power Management * options i have selected to do nothing when my laptop lid is closed, by default is Suspend but i let the computer downloading with* qbittorrent* all night, the thing is the next day when i lift up the lid, I put the password, and the wireless conection is off, so my 2GB torrent that was at 2% yesterday now is 5% :(

I didnt find an option like when i had Windows, to no turn off the network adapter to save energy, i think that maybe could be something like that but didnt see the option in *Power Management* or *Network Connections*

I searched in internet, tought was a common issue but didnt find anything specific :(

Any kind of help will be appreciated, and sorry for my bad english :)

---

### Post by OM55 on 2012-08-05
Hello Galdov,

Is it possible that you made the changes only in the "Plugged in" options while left the laptop not plugged in? If so the laptop may have gone into hibernation after a while, which would explain the additional download (from 2% to 5%) but nothing else.

First, for a long unattended operation - keep the laptop plugged into power.
(If you leave the computer unplugged, you will need to the changes below also in the "On Battery Power" tab - but it is not recommended, as you might completely drain your battery and reduce its life span dramatically)

Then, open Power Management:
System -> Preferences -> Power Management

In the "On AC Power" tab, select:
*Put computer to sleep* - Never
*When laptop lid is closed* - Blank screen
*Put display to sleep when inactive for* - Never

That all you need.
If you do not have on display any of the options above, respond here and I'll add the information on how to add it.

---

### Post by Galdov on 2012-08-05
the only thing that was different in my config was

Put display to sleep when inactive for - 30min

instead of never, tought that this option just was to put black screen, but the other option does that "When laptop lid is closed - Blank screen"

so maybe that was the problem, thx :)

---

