---
title: "What would be different with Kubuntu vs Ubuntu in terms of network handling?"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-12-14
I'm imaging Windows laptops at work using FOG - Linux based open source cloning tool.

I have two LANs going. Both are running E5500 Latitude's as the "Servers" of each LAN.

One = Kubuntu Karmic
Two = Ubuntu Jaunty

Each is running on a Dell PowerConnect 2824 24 port gigabit switch.
Entire wiring system is CAT5e.

When I fire up each LAN at the same time, it seems as if the Kubuntu LAN will fire up 2 laptops to run full bore, leaving the other 13 laptops running @ around 3-4 hours remaining, which is insanely slow. Once the 2 speed demon laptops get done, the other 13 pick up speed much faster. Overall, to do the 15 laptops, it takes about 50 minutes. When I fire up the Ubuntu LAN, they stabilize after 4-5 minutes of imaging and finish at the same time together, ranging around 35-40 minutes to image the laptops.

Two LANs. 
Two identical servers.
One Kubuntu, one Ubuntu.
Slight variations in performance and speed.

Could a desktop environment play a key role in network traffic like this? I just don't see what's different here besides the actual OS on each laptop. It doesn't make sense.

The other curve ball is, I used to run Ubuntu on my work laptop and had no issues like this, and the laptop I'm talking about where I used to run Ubuntu with no issues is the one currently running Kubuntu. I only later changed it to Kubuntu based on personal preference. Then when I got handed this job, I added a 2nd Ubuntu laptop to handle the load, which is why I have 2 laptops now.

But anyway, what's up? Any ideas?

---

### Post by Roasted on 2009-12-15
I came in today with more laptops to image and swapped out the laptops, so LAN 1 (originally Ubuntu) was now on the Kubuntu laptop and LAN 2 (originally Kubuntu) was now Ubuntu.

The issue was reversed. Now Ubuntu seems slower. I talked to the network admin and I remember there was a point in time he logged into the switch and made some config changes, but that was dating back a few months ago and I had forgotten.

So, more or less, it wasn't an OS issue - it was a switch config issue. I'll compare the results later and see what the differences were, but as of now I don't think the OS difference had anything to do with it.

---

