---
title: "About to lose it [Driver issues]"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by antagonistxx on 2010-08-22
Hello everyone! I will be so happy if someone can help me out with this, as I've been struggling for ages now. 

I am trying to either patch my current ath5k driver for packet injection support, or install madwifi. Before you rip on me for not looking through the forum, I will state that I have searched far and wide.

My system specs are as follows:

Acer Aspire One Netbook  (a150)
Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
Ubuntu Netbook Remix 10.04  (lucid)
Kernel : 2.6.32-24-generic


Lets start with my current ath5k driver. It works great, but doesn't support packet injection, so I downloaded compat-wireless and patched my driver with the following

[http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch](http://patches.aircrack-ng.org/fix_ath5k_no_data_in_monitor_mode.patch)
[http://patches.aircrack-ng.org/ath5k-injection-2.6.27-rc2.patch](http://patches.aircrack-ng.org/ath5k-injection-2.6.27-rc2.patch)

I compiled and installed properly, and the driver works, but still no packet injection..
I tried the absolute newest driver (which is updated daily), and another, and neither seemed to work.

As for madwifi.. well that's another story. Almost every verion of madwifi fails on the compilation, however, I did successfully get one version (trunk) to compile, and while it worked, the connections were very very slow.


Perhaps someone running the same distro or netbook may have some more information to offer?

I have all my kernel srcs, and for the most part have a good idea as to what I'm doing, so I don't see why I'm struggling so hard. Perhaps its a compatibility problem? Perhaps I've just grabbed the wrong versions? 

Any point in the right direction would be great.



(also, I'm blacklisting the version of madwifi I currently have installed, which installed properly but kills network manager (I can't seem to see any networks).)

:mad:

Thanks in advance!

---

### Post by antagonistxx on 2010-08-23
Anybody? 

The compat-wireless website says even the newest versions should be working with packet injection.. Yet the release (released yesterday) that I've compiled doesnt, even when patched with the above two patches.

:frown:

---

