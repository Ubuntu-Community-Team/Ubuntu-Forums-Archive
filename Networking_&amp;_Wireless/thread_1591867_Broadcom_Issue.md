---
title: "Broadcom Issue"
date: 2010-10-10
forum: Networking &amp; Wireless
---

### Post by Onael on 2010-10-10
I have two machines running exactly the same OS (Ubuntu10.10 beta) and I can't get to my wireless network on one of them. My desktop is using a Linksys PCI network adapter. It found my network and connected to it without any problems.

The problem is my laptop. It won't download and install the driver for the BCM4312 network controller. The confusing thing is that it installs just fine during the LiveCD session, but not when I boot into my fresh install.

Any ideas? Thank you.


Onael



I tried a couple of things:

 1. re-installed OS: no change

 2. activating while in LiveCD session: it activated, but it didn't remain so on reboot.

When I try to activate it, I get an error message:
     "Sorry, installation of this driver failed.
      Please have a look at the log file for details:/var/log/jockey.log"

What does this mean?

---

### Post by Onael on 2010-10-10
Okay. I got it working. Here's what I did. Hope it helps. (and if I'm repeating what others have already figured out, sorry)

1. I went into System->Admin->Synaptic Package Manager and searched for 'bcm'.
2. I marked "bcmwl-kernel-source" & "bcmwl-modaliases" for reinstallation.
3. I marked "broadcom-sta-common" & "broadcom-sta-source" for installation.
4. Applied and restarted.

When startup was complete, I clicked on the network icon and noticed that I now had the option to "Connect to Hidden Wireless Network..."

5. I clicked the new option and I was in.

---

### Post by Megaptera on 2010-10-10
Glad you solved it and thanks for posting the solution which will help others.

---

### Post by nigrai on 2010-10-11
Thanx a lot, man!:P
It works like a charm!
You made my day!

---

