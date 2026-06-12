---
title: "Using 2 wlan cards"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by persev on 2009-01-31
I have a Dell Inspiron 1525 n with i3945 card. I added an Atheros AR242x pci-e to the wwan slot. It's shows up with lspci but not under iwconfig. Any one have any ideas how to use the cards at the same time? Or just get the Atheros card working in the wwan slot?

---

### Post by nixscripter on 2009-01-31
You have to use the right drivers for the second card. See if this works:

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

### Post by persev on 2009-01-31
> **nixscripter said:**
> You have to use the right drivers for the second card. See if this works:

[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

Thanks for the reply. Why would I want to use ndiswrapper when the madwifi driver is available? The madwifi driver is installed, or are saying that the madwifi driver won't work with this card?

---

### Post by nixscripter on 2009-02-01
I don't know whether madwifi would work, but that thread suggests that particular set of Atheros cards is quite tricky. In fact, the brand generally seems to be one that a lot of people have trouble getting to work, each kind with a different solution (due to different chipsets, perhaps).

It was merely a suggestion based upon Google and my understanding of the difficulty with these cards in general.

---

### Post by persev on 2009-02-02
> **nixscripter said:**
> I don't know whether madwifi would work, but that thread suggests that particular set of Atheros cards is quite tricky. In fact, the brand generally seems to be one that a lot of people have trouble getting to work, each kind with a different solution (due to different chipsets, perhaps).

It was merely a suggestion based upon Google and my understanding of the difficulty with these cards in general.

My understanding is that it is the same card that is in the eee pc and many other netbooks, which is why I got it. I knew I may have to patch the driver but saw no reason to use the windows driver with ndis over the madwifi driver. I was thinking that the problem was in using the wwan slot instead of the wlan slot on the board. I was going to set the the Intel 3945 up for kismet and use the Atheros card for injection. I'm just trying to learn a bit more about pentesting. I am using this on my home network so it's all good. The Intel card actually works much better in the wwan slot but still no luck with the Atheros card. I will isolate the Atheros card next by completely removing the Intel card

---

### Post by persev on 2009-02-03
Still no luck and madwifi won't build properly.

---

### Post by nixscripter on 2009-02-03
What do you mean "won't build properly"? Are you having troubles compiling the driver?

---

### Post by persev on 2009-02-04
> **nixscripter said:**
> What do you mean "won't build properly"? Are you having troubles compiling the driver?
Correct it wouldn't compile, don't remember the error. I was trying to build it from source.

---

### Post by persev on 2009-02-04
Solved! Followed this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
I haven't tried injection yet but at least the card is working now. Both cards actually show up in network-manager now. Now how do I mark it as solved?

---

### Post by nixscripter on 2009-02-04
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by persev on 2009-02-06
> **nixscripter said:**
> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Doesn't work, that option isn't there for me.

---

