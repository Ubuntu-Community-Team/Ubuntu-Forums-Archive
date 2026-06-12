---
title: "SOLVED T-Mobile dongle with Ubuntu 10.04"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by Whitston on 2010-07-11
I found this solution from a post by **little(underscore)penguin**, and have been asked to put it out in the hope that others may find it more easily.

I used the network manager to install the settings for the pay as you go T-Mobile USB Stick 120 (mobile broadband dongle).  The settings produced by the network manager were as follows Number - *99#    User - User    Password - mms    APN  general.t-mobile.uk

With these settings it was not possible to get a connection.  ZTE (the chip manufacturer) kept asking for a password and nothing worked.

I then found this advice from **little penguin**.   Change User to user and mms to pass.

Having made and applied these changes in the network manager (by selecting the mobile broadband tab and T-Mobile and EDIT), the connection worked first time.

Hope this helps, but if you have technical questions, please do not contact me as I am a beginner.  I am sure that **little(underscore)penguin** will be able to help.

Jim

---

