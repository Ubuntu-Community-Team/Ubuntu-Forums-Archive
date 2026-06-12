---
title: "need help connecting to campus network"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by moralhazard on 2010-03-02
I recently went back to Linux on my netbook because Windows 7 was too laggy (1gb of RAM, go figure). I've never been able to connect to the protected wireless network on my campus without using Windows, though, so I was hoping someone could help me finally get that figured out.

The school has a how-to for connecting to the network using various operating systems, including Linux, [here]("http://www.uccs.edu/%7Ehelpdesk/wireless.htm") (scroll down to the bottom to choose OS). After following the guide through the CA certificate it mentions, the network manager tries to connect for a while then just sort of times out and asks me to enter the information again. Using Wicd, I noticed that this timeout appears to happen when trying to obtain an IP (after authentication).

My system: Acer Aspire One AOA150 with an Intel 4965AGN wireless card (installed by me a few months back, have had no problems with the card itself not working). I've installed Kubuntu 9.10 Netbook edition and done all available updates. My campus offers an unprotected "Visitor" network that I can connect to without issue, but they limit what you can access using the unprotected network so I need to be able to connect to the WPA2 one.

I've tried getting help from on-campus IT but keep getting told that none of them know how to use Linux, which makes me wonder who exactly wrote the how-to on their website... The guides on the website are for older versions of Ubuntu, but I figured they would remain applicable on a later-version Kubuntu install. I never could get them to work on any Linux machine, though.

Any assistance would be much appreciated.

---

### Post by UrBob on 2010-03-02
I took a look at the instructions and they seemed OK in Ubuntu 9.10, slight differences in wording but that was about it.
 
I noticed another thread with a comment about a school network which worked with Windows XP but not with later versions of Windows or with Linux. Take a look at [http://ubuntuforums.org/showthread.php?t=1399246&page=2](http://ubuntuforums.org/showthread.php?t=1399246&page=2) for the particular solution.
 
(Never heard of it myself, but then I don't do devious things with networks).
 
Hope this helps a bit

---

### Post by moralhazard on 2010-03-03
> **UrBob said:**
> I took a look at the instructions and they seemed OK in Ubuntu 9.10, slight differences in wording but that was about it.
 
I noticed another thread with a comment about a school network which worked with Windows XP but not with later versions of Windows or with Linux. Take a look at [http://ubuntuforums.org/showthread.php?t=1399246&page=2](http://ubuntuforums.org/showthread.php?t=1399246&page=2) for the particular solution.
 
(Never heard of it myself, but then I don't do devious things with networks).
 
Hope this helps a bit


Thanks for the reply. I tried the fix you linked (added "send vendor-class-identifier "MSFT 5.0";" as a post script to Wicd) but it did not help. Wicd still fails to obtain an IP when trying to connect to the network.

Is there some way to force the IP outside the network manager? Since I can't get an IP it disconnects altogether, but what if I could remain connected then manually run DHCP to get an IP?

---

