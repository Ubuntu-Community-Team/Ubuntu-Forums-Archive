---
title: "Can't have a capital in an SSID!"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by braufrau on 2011-10-07
Hi,

   I've had natty installed on my ASUS netbook for a couple of months now and think its great. Visiting with my parents now and of course want to check my email ... no go! 
Google and google wpa and ubuntu etc. etc. why on earth will it connect to my home wpa network and not here?
Then I get the bright idea of changing the SSID from "Name" to "name".
Voila! It connects. And yes I had the them the same in the modem setup as my ubuntu wireless setup. Its automatic anyway. 

Problem is my dad also has a repeater thing (can't think of the right word now) that's still called Name so I have to sit down the back of the house where the signal from the modem is greatest from "name" and not up in the warm lounge connected to "Name".
I'll bug him tomorrow to see if I can get him to change it.

But has anyone heard of this before? Its certainly not a problem with windows or my fathers phone or ipad or ...

And I had a previous version of ubuntu on my old msi wind which I had lots of problems wtih but visiting here and not being able to connect to the wifi was the last straw. So its been a problem for awhile!

---

### Post by ajgreeny on 2011-10-07
I am sure there must be something more than that causing your problem, as I have an SSID totally in upper case, and can connect to that without a problem in 10.04, 10.10, 11.04 and 11.10 alpha 3.  There are also some SSIDs I use with a mix of upper and lower case letters.

Look elsewhere for the problem, I think, though I have no clue about where to look.

---

### Post by braufrau on 2011-10-08
Quite Right!

All I did was enable my computer (and myself) to differentiate between the two APs, now with different SSIDS. By chance I changed the one that I happened to be able to connect to, making it seem that the capital was important. 
But after much mucking around with SSIDs it became apparent that I just coulnd't log onto the "Name" AP no matter what its name was. 
A quick look under its bottom told me it was an "N" only AP so I guessed that was the problem.
Turns out all I had to do was get into the system and settings and activate the broadcom drivers! So here I am happily connected to "Name".
 
Thanks for your help!:popcorn:

---

