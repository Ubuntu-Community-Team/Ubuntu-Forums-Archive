---
title: "Wireless gone after kernel crash (was using madwifi drivers)"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by gelatinous_cube on 2009-05-03
Hi, I'm completely new to all this, I have really limited knowledge of how Ubuntu works and whatever. All I know for sure is I hate Vista to guts and even the fact that I have to use it now in order to be able to access internet and write in the forums is becoming increasingly irritating. I will NOT get back to it.

Anyway, I am using a Toshiba laptop with **Atheros AR5007EG** Wireless adapter, which did not automatically work when I first installed Ubuntu 8.4 in recognizing wireless networks. I finally found the solution in installing the **madwifi** drivers and everything was working smoothly.

Recently I upgraded Ubuntu to 9.4 and everything was still going well, until this morning Kernel failed with something like this message: bad gzip numbers bla bla Kernel panic whatever, so I picked another version from the boot list which worked fine. But the wireless no longer does.

I read on the internet that I should reinstall **2.6.28-11-generic**, but I cannot do that without a working internet connection. What should I do?

---

### Post by gelatinous_cube on 2009-05-03
Thanks for the replies. I am really enjoying writing my university essay on ubuntu without an internet connection and no clue how to restore it.

---

### Post by pi3832 on 2009-05-03
@

---

### Post by pi3832 on 2009-05-03
@

---

### Post by gelatinous_cube on 2009-05-04
True, but then again, politeness got me nowhere. This thread was washed away in no time.

Anyway, thanks! I reinstalled the kernel and then, when wireless was still unavailable, I found this solution that worked for me perfectly: :
[URL="http://ubuntuforums.org/showpost.php?p=7202059&postcount=3"]
http://ubuntuforums.org/showpost.php?p=7202059&postcount=3[/URL]

You need to download the attached file and also have a working internet connection in order for this to work. Just plug in the wire (assuming that you have a wired connection available) and follow the two simple steps described.

---

