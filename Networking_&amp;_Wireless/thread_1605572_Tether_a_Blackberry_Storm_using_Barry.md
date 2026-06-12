---
title: "Tether a Blackberry Storm using Barry"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by mobilewords on 2010-10-25
I challenge anyone in the universe to give me a howto on tethering a blackberry storm to a laptop with ubuntu 10.04 using barry or any alternative.

The forums and web pages are completely useless; nothing works; no one actually says here's how to do it.

A gui version would be preferred but anything that would work would be acceptable.

I am willing to wager there isn't one person who can do this; I leave it to you to prove me wrong.

Thanks.

---

### Post by djharkavy on 2010-10-31
Well...

I have it working.

First, I installed the Barry packages.

Then I used my usb cable to hook my blackberry to my laptop.

Then I opened a terminal and ran btool.  It showed that I was connected to my blackberry and gave my PIN.  I think you need to sudo btool under meerkat.

Then I sudo pppd call barry-tmobileus

I needed to tweak the /etc/ppp/peers/barry-tmobileus slightly to get it to work.

---

### Post by mobilewords on 2010-11-04
Hey, thanks for this.
is mobileus your phone service provider? or just an app within barry?
ubuntu has barry-utils, is this the only thing you installed?
I have a dial number, passsword and other info from my cell telephone supplier; where do i enter these, or do i need to enter them anywhere?
sorry for continued confusion, but as i have made no progress in the past i want to be assured i am setting up correctly before attempting again.
toratmobilewords.ca gets me directly instead of through this forum if you'd prefer.

---

### Post by auntdracula on 2011-03-07
does anyone have further instructions for this method? i've followed the above instructions and can get to the point where my phone says that modem mode has been enabled. at this point though, there's no network listed to connect to. i've tried manually making a moblie broadband network connection through system --> pref --> network connections, but this is never provided as a network to connect to either.

can anyone who has this figured out point me in the right direction??

---

