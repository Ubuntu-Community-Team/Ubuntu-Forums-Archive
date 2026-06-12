---
title: "RaLink rt2800+wpa2+ kernel 2.6.38-can't connect"
date: 2011-03-04
forum: Networking &amp; Wireless
---

### Post by The Adi on 2011-03-04
Hi guys, the problem I'm trying to figure out since few weeks is that I can't login to WPA/WPA2 protected WIFI network on kernel 2.6.38. And I know for sure that this is the kernels fault because I've made some nice tests - I've had mint installed, I've made update to Natty and on boot I had two kernels to choose from so I could check both of them and of course on the 2.6.38 I couldn't connect. It was repeatedly asking for a password and nothing. I've also tested it on numerous Ubuntu live cd's and when I've tried Maverick life - all was nice and smooth, but after trying Natty from the firsts testing versions last year up to last nights alfa3 - I still can't connect. And the last proof of 2.6.38 kernels fault is the test of the latest Kanotix with the 2.6.38-rc6 (Ubuntu recompiled) - also with no luck :( All distros with kernels lower than 2.6.38 are connecting very smoothly and all distros with all rc's of 2.6.38 gives me no luck. So the question is What The Heck is going on?? :confused: Is this kernel really so f*#¤%d up?

---

### Post by The Adi on 2011-03-05
People of the World! Is there someone who knows what the BLEEP is going on with this kernel? And if there is some solution for that? I know that this is not the only one issue with it. I found many problems related with 2.6.38 but nowhere the fix! Or do I have to write to Linus personally? :P

---

### Post by chili555 on 2011-03-05
A great many cases here have trouble connecting to mixed WPA and WPA2 networks but have no trouble with one or the other. An even greater number of people have trouble with the rt2800 suite. If there is any other alternative, I blacklist rt2800.

There are many devices that are claimed by more than one driver, causing a conflict. The most common example is rt2800 and rt2870, although there are several others.

As far as I know, the latest stable release of Ubuntu is Maverick and its latest stable kernel in Maverick is 2.6.35-27. So the greatest majority of us have no experience with 2.6.38.

Finally, I'm not sure the Networking and Wireless forum is the best place to open a kernel discussion. You might have better luck here: 
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

### Post by The Adi on 2011-03-05
Thanks for the answer chili, you are a good man :P 
Well, actually I "can't connect to wireless network" so...it is "Networking and Wireless" issue ;) But you are right with the kernel part :) So i think I'll try my luck in the place you've pointed me to.

Thanks again and greetings from Europe :)

---

