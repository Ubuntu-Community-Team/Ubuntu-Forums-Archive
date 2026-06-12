---
title: "Desktop and laptop won't connect to wireless network at same time??"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by swoody on 2008-12-22
Running the 'Folding at Home' client is making my computers disconnect one-another from my wireless network. When I connect to the network on my desktop it will kick my laptop off the network, and vice-versa. I can eventually get both computers connected at the same time, but I have to play a game of roulette first - connecting and disconnecting the computers from the network until I have appeased the network Gods, and they let both computers stay connected. This only lasts until I have to restart one of my computers, and then I have to do it all over again.

This is not just an Ubuntu thing either, When I boot my desktop into Vista I can't connect to the network either while my laptop is running f@h. I've uninstalled folding at home on both of my computers, and this problem seemed to have gone away. The problem returns when I reinstall f@h.

How can I get rid of this annoying problem, and have f@h working at the same time? And what would f@h have changed on my computers or my network device to cause this?

My desktop is running 32bit 8.10 with an Atheros AR5800 Wireless Adapter. My laptop is running 32bit 8.10, with a Broadcom BCM4311 adapter. My wireless router is a 2Wire 1800HG. Any and all help would be GREATLY appreciated! Thanks in advance!

---

### Post by swoody on 2008-12-23
Nobody has any advice??

---

### Post by ziesemer on 2008-12-23
I almost didn't reply, either, as I don't readily see a question to answer.

I guess the first thing we need to find out is exactly what getting "kicked off" means.

I'm assuming both your desktop and your laptop are connecting over wireless?

When you get "kicked off", does it show your wireless connection as "disconnected", or are there other problems, such as traffic just no longer being received?

I assume f@h is the Folding@Home distributed computing client?  I don't see how that would be related to anything, as it just produces temporary Internet traffic.  If you reinstall it, can you reproduce the issue?

Do you have another wireless router you can try?

Can you connect one or both computers over a wired connection, and see if that helps?

---

### Post by swoody on 2008-12-24
> **ziesemer said:**
> I guess the first thing we need to find out is exactly what getting "kicked off" means.

I'm assuming both your desktop and your laptop are connecting over wireless?

When you get "kicked off", does it show your wireless connection as "disconnected", or are there other problems, such as traffic just no longer being received?

I assume f@h is the Folding@Home distributed computing client?  I don't see how that would be related to anything, as it just produces temporary Internet traffic.  If you reinstall it, can you reproduce the issue?

Do you have another wireless router you can try?

Can you connect one or both computers over a wired connection, and see if that helps?

Thanks for responding :) Now let me try to answer those questions for you:

By getting "kicked off" yes I mean being disconnected from the wireless network. Both computers are connected wirelessly. 

Yes you are correct, f@h is the 'Folding at Home' distributed computing client. I wouldn't think it would have caused this at all, except for when I uninstalled it, and the network problems cleared up :confused: And yes the problem is able to be reproduced, as I've reinstalled f@h on my laptop, and the same problems have arisen again - I have to play a game of roulette disconnecting and reconnecting my two computers to the network to be able to have them both connected wirelessly to the network at the same time. Like I had said before, this doesn't happen with f@h uninstalled.

Unfortunately I can't connect my desktop through a wired connection, but when I connect my laptop to the network through an ethernet cable, I don't experience this problem. Also, I don't have any spare routers sitting around to test.

---

### Post by cabbiinc on 2008-12-24
> **woody86 said:**
> Thanks for responding :) Now let me try to answer those questions for you:

By getting "kicked off" yes I mean being disconnected from the wireless network. Both computers are connected wirelessly. 

Yes you are correct, f@h is the 'Folding at Home' distributed computing client. I wouldn't think it would have caused this at all, except for when I uninstalled it, and the network problems cleared up :confused: And yes the problem is able to be reproduced, as I've reinstalled f@h on my laptop, and the same problems have arisen again - I have to play a game of roulette disconnecting and reconnecting my two computers to the network to be able to have them both connected wirelessly to the network at the same time. Like I had said before, this doesn't happen with f@h uninstalled.

Unfortunately I can't connect my desktop through a wired connection, but when I connect my laptop to the network through an ethernet cable, I don't experience this problem. Also, I don't have any spare routers sitting around to test.

Just a shot in the dark here but could f@h be causing both computers to try to use the same IP address?

---

### Post by ziesemer on 2008-12-24
f@h doesn't do anything with the network configuration.  Are you running f@h on both computers?  Only thing I can think of is that f@h, by nature, is quite CPU intensive, and depending upon your wireless adapters and/or drivers, there could maybe be an issue with not being able to keep the connection under load.

Can you duplicate this issue with any other kind of Internet traffic?  Try downloading a larger file on both computers at once - go grab an Ubuntu .iso or something.

Also, try to find some sort of a "stress test" program that attempts to utilize the CPU to capacity, and see if that can reproduce the issue.

Also, how are you running the f@h clients?  If running them as a service, try running them direct with debug output so you can maybe see when within the f@h process you are being disconnected.  I.E., does it happen at some point as f@h is downloading new work units or uploading completed ones?

My bet is a flaky wireless router.  I'd see if you couldn't borrow someone else's router (with permission) to troubleshoot this, possibly taking your computers to one if necessary.  If you can narrow it down to your router, you could check for firmware updates and other settings on the router.

---

