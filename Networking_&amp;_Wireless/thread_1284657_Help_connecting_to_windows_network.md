---
title: "Help connecting to windows network"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by japhyr on 2009-10-06
Hello,

In most of my work with ubuntu, I am more than willing to try different things and only ask a question when things are consistently not working.  This situation is a little different.

I am a high school teacher, and I have undertaken a project in which students have received a number of old computers donated from the community.  These are classic Windows deadbeats - BSOD, virus-ridden, slow, etc.  Students have learned to install ubuntu, and set up a simple configuration.  They love it, and they are floored that you can set up a computer with no antivirus that continues to work on the internet.

The computers will be useful for the school if students can access the internet, print, and have different user accounts for different purposes.  We have done all that.

The last step to making these computers useful in the whole school is letting them access the larger school network, where students' documents are stored.  I am wary of this step because if I mess up the network, my now-cooperative sysadmin will quickly shut down the project.  Could someone walk me through the process of connecting to the network as a client, in a way that we stand a minimal chance of affecting the overall network negatively?

I have tried the simple step of opening Nautilus, and entering "smb://shared_folder_name".  The message I receive is "Couldn't dispay shared_folder_name. Failed to retrieve share list from server.  Select another viewer."  Am I on the right track?  I saw [this windows networking post]("http://ubuntuforums.org/showthread.php?t=1169149"), but did not want to play around with the possibility of messing up the school's, or even district's network.

Any advice?

We are using Ubuntu 8.04.3.

---

### Post by ceylonerana on 2009-10-07
You can try Samba. This link gives more details about hoe to do that.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by pjstock on 2009-10-15
> **ceylonerana said:**
> You can try Samba. This link gives more details about hoe to do that.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
No offense intended but my opinion this suggested Samba How To is insanely complex. It leads a relatively inexperienced user like me blindly through a series of arcane commands that we have no idea the effect of.
if this is where Ubunut and Linux's user friendly ends or is going, heaven help the advancement of this otherwise important operating system.

---

