---
title: "after a year, wireless quits"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by GMachine_24 on 2012-06-23
Hi. I am here and I am pretty fed up. I installed 11.04 pretty much when it came out last year (2011) on a Lenovo notebook and for more than a year everything worked.

Then, I imagine after some so-called upgrade, my wireless quit working. Mind you, this was after a year of working without a problem.

This is the wireless network card:

```

04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

Previously, I believe I used

```

b43-fwcutter
firmware-b43-installer

```

and everything was great. Now, nothing works and I have wasted so much time -try at least 5 hours over many days - trying to get this thing to work again it's ridiculous.

BTW, the notebook works fine with a cable connection.

I have tried:

broadcom-sta-common & broadcom-sta-source

b43-fwcutter with the firmware-b43-lpphy-installer

I have made sure that b43xx cards are not blacklisted in any of the files in /etc/modprobe.d - I checked this whatever drivers I had installed.

I can plug an external USB wireless Cisco connector/card and the computer will recognize it. But I only tried that after everything else failed.

I'm guessing one of the updates I installed killed the wireless capability. Which is very frustrating. The entire "blacklist" thing is annoying beyond reason.

Meanwhile, if anyone has ANY ideas, please let me know. I have been using Linux and Ubuntu for almost a decade and never, ever has anything like this happened. I'm ready to turn the laptop into a Frisbee and heave it into the lake outside my home.

---

### Post by GMachine_24 on 2012-06-23
So, I feel like a dope. But I thought I should come back and say I solved the problem. Yeah, just like that.

For whatever reason, I went to System>Administration>Additional Drivers

The windows that opened said the Broadcom STA Wireless Driver was not activated. I could not remember whether I'd tried this or not - I thought I had - but I decided to try it again.

And, of course, it worked. And it works.

I had installed some of these packets via Synaptic but it seems, maybe, I had not installed the three packages that now show they're installed (that can be seen after running

```

sudo synaptic

```

click on "Search"

search for "bcm"

I'm attaching a screenshot so you can see the details of the packages now installed.

I am SO glad this is fixed.

---

