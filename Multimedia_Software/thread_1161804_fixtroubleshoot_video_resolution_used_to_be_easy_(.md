---
title: "fix/troubleshoot video resolution used to be easy (ish) - now it is not"
date: 2009-05-17
forum: Multimedia Software
---

### Post by Simon Bridge on 2009-05-17
With reference to:
[http://www.linuxquestions.org/questions/linux-hardware-18/changing-video-resolution-when-xorg-borks-it-up-726504/#post3543323](http://www.linuxquestions.org/questions/linux-hardware-18/changing-video-resolution-when-xorg-borks-it-up-726504/#post3543323)
[https://answers.launchpad.net/ubuntu/+faq/128](https://answers.launchpad.net/ubuntu/+faq/128)

... it took a long time for me to find the second one, and *I* was sure that it existed. In general, users that need it won't be so persistent.

Thankfully, advances in xorg have meant that manually editing xorg.conf is largly a thing of the past. This is a vast improvement. However, there are times when the autoconfig just does not work.

When this happens, I insist: it is *excessively* difficult to figure out what to do about it.

Googling around the question of how to change screen resolution in ubuntu, I find most users "solve" the problem by using proprietary drivers, third-party tools, changing distro, or changing to windows.

This is crazy. It should not be this hard but the overall user experience seems to be that it is intractable.

The solution is not difficult, it is just that the end user becomes too frustrated discovering it. This is a communication failure.

I observe that users do not generally attempt to adjust the screen resolution unless something goes wrong. They expect to find their solutions in the Screen Resolution dialog.

I suspect that it would be useful to include access to the displayconfig-gtk thingy as an "advanced settings" button under System > Preferences > Screen Resolution.

Comments? Something for Launchpad?

---

