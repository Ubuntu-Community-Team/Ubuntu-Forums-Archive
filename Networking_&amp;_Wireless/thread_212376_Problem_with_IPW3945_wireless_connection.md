---
title: "Problem with IPW3945 wireless connection"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by kemosabe79 on 2006-07-09
I have everything set-up correctly according to this [thread]("http://ubuntuforums.org/showthread.php?t=140085&highlight=ipw3945+driver+installation"), and I have internet connectivity, but every few seconds I drop my connection. Also, when I drop my connection (btw-I'm like 6 feet away from my router...a Netgear WGT624 v3), my laptop, a Dell Inspiron e1505, locks up. When the Wifi light comes back on, the computer is back to normal. Does anyone else have this problem? Its driving me crazy. I can surf normally for at most 5 minutes or so before I lose my connection. Any help would be great.

---

### Post by djoelsson on 2006-07-10
I have the same chipset, but with a different problem.  I can connect to my router just fine, but the connection is really slow.  It only runs at 1/10 the speed it does in windows.

I wonder if these are symptoms of a similar problem.

What processor do you have?  What Ubuntu version/kernel?

My hunch tells me it's related to the powermanagement problems with the 686 kernel (I haven't tried the 386 kernel yet).

Please let me know if you get somewhere with this.

Dan

---

### Post by kemosabe79 on 2006-07-10
Im on the Dapper 6.06 386 kernel. I have an Intel core solo T1300 chip. Im trying a clean install atm, and I'll let you know if I find a work around. 

Im going to try the latest driver for my IPW3945...the beta ones. I usually try to stick with the stable releases, but maybe (Im crossing my fingers on this one) the latest development release will solve the problem. 

I'm really at a loss right now...my wifi worked flawlessly in breezy. At least I know that this issue isnt necessarily related to my kernel version, because a kernel compilation was my next try and I'd like to avoid it if possible.

---

### Post by kemosabe79 on 2006-07-16
Well I think I've got it working for the most part now. I installed the latest development driver for my IPW3945, and I built Network-Manager from source. I still have the occasional studder, but it is a little more tolerable now. Hopefully, future updates will solve this problem completely.

I'm still up for any suggestions, so don't hesitate to let me know if there's another way to get this sucker working.

---

