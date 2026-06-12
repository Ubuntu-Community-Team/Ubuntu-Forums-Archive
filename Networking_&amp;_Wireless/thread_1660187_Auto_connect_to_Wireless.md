---
title: "Auto connect to Wireless"
date: 2011-01-05
forum: Networking &amp; Wireless
---

### Post by mac4rfree on 2011-01-05
Hi Guys,

Today Morning i installed Ubuntu 10.10. Now whenever i am rebooting, i am not able to connect to my Wifi as it did in my Win7... 

It keeps asking me for my password.. after that,i am able to connect to it.. It is bit annoying.. Can somebody help me in automating it.

Cheers!!!
Magesh

---

### Post by fabricator4 on 2011-01-05
> **mac4rfree said:**
> Hi Guys,

Today Morning i installed Ubuntu 10.10. Now whenever i am rebooting, i am not able to connect to my Wifi as it did in my Win7... 


Right click on the wireless icon on the top panel and you'll get a drop down.
Click on "Edit Connections"
Select the Wireless tab
Select your wireless router (ie "Auto my=SSID")
Click on the Edit button
Up the top of the Window that opens you'll see a checkbox for "Connect Automatically". Make sure this is checked.

The system should now connect to your local wireless network each time.

The wireless password will now be protected by a "keyring" password system that you may now have to set up if you haven't done so already.  If you type your password each time you log on, this keyring gets unlocked at the same time.  If you have the system set to automatically log you on at boot then the keyring will not get unlocked and you will be prompted for the keyring password as soon as it tries to connect to the wireless network.

This is a security feature, not a bug.

Regards,
Chris.

---

