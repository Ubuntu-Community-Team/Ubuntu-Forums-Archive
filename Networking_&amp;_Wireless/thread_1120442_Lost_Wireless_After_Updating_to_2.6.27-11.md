---
title: "Lost Wireless After Updating to 2.6.27-11"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by Gyroscope352 on 2009-04-09
Alright. I know this has been asked about ten billion times. But I have looked at so many posts today and I am not getting anything helpful. So hopefully someone who has experienced this exact problem can help me.

I have a MacBook, meaning I have an Atheros 242x wireless card. It was working in 2.6.27-7. I updated to 2.6.27-11 (I know, for some reason this update was just given to me yesterday) and my network manager could no longer detect any wireless networks. And by looking at these forums, I am certainly not the only one this has happened to.

I've tried so many things I don't even remember what they were. Only one attempt to reinstall the drivers actually produced noticeable results, but it's still not working. When I boot in -9, I have my "Support for Atheros 802.11 wireless LAN cards" activated in the Hardware Drivers, and wireless works fine. In -11, I now have "Support for Series 5xxx of Atheros 802.11 wireless LAN cards" but wireless still does not work. These are the only options I have in each kernel.

For those of you that went through this back when -11 came out (and I know you're out there!) What exactly did you do in the end to fix it? Or, what can I do at this juncture that will give me the right drivers in -11? I'm trying to update the kernel every chance I get, because I'm having some application not responding problems right now that I can only hope are kernel problems that will get fixed. Please help!

---

### Post by t0mppa on 2009-04-09
Well, to get the discussion started, [http://ubuntuforums.org/showthread.php?t=1120259]("http://ubuntuforums.org/showthread.php?t=1120259") shows how I fixed mine yesterday. But that's with no "Support for x" drivers even showing up at the Hardware Drivers section. Might have to remove/blacklist yours (saw a lot of people doing that, didn't need to try it myself), if you follow this.

---

### Post by Gyroscope352 on 2009-04-09
> **t0mppa said:**
> Well, to get the discussion started, [http://ubuntuforums.org/showthread.php?t=1120259]("http://ubuntuforums.org/showthread.php?t=1120259") shows how I fixed mine yesterday. But that's with no "Support for x" drivers even showing up at the Hardware Drivers section. Might have to remove/blacklist yours (saw a lot of people doing that, didn't need to try it myself), if you follow this.

VICTORY. I didn't need to blacklist anything, I just did exactly as you said on that page and it works like a charm. I can't believe it took me two days to get this working when that was all I needed. The internet needs some better organization. ;-)

Thank you so much!

---

### Post by t0mppa on 2009-04-09
Heh, it took me some time to pull all the info required for that as well. Felt a bit dumb, when I finally got it working, since it was such a simple thing in the end, but I'm glad it ended up helping someone else as well, so maybe all that work wasn't in vain!

---

