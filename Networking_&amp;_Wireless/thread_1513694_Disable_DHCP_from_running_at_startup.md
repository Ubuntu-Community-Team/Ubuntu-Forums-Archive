---
title: "Disable DHCP from running at startup"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by kroq-gar78 on 2010-06-19
Hello, this is my first post on the Ubuntu forums.

I am trying to set up a network bridge between my LAN and Wi-Fi connections to allow my Xbox 360 to use xbox live (internet) without the purchase of an $80 adapter (specifically for xbox). I tried this on Windows Vista on my same laptop and it works well (used wubi).

Now my question: how do I disable DHCP from starting up (or running during startup). I want to do this because I am using a tutorial ([http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge#It_doesn.27t_work_with_my_Wireless_card]("http://www.linuxfoundation.org/collaborate/workgroups/networking/bridge#It_doesn.27t_work_with_my_Wireless_card")) and it says to disable the DHCP script. I have searched but have not found an answer. I have used the package "bum" and searched in the /etc/rc*.d directories but I am not sure how to disable it (based on this Ubuntu forum thread [http://ubuntuforums.org/showthread.php?t=848219]("http://ubuntuforums.org/showthread.php?t=848219")). Those didn't work.

Can someone help me disable the DHCP startup so I may continue with the tutorial?

Thanks in advance,
kroq-gar78

---

### Post by Iowan on 2010-06-21
You could check the */etc/rcX.d* directories, but I dunno if Network Manager might hold a trump card...

---

### Post by kroq-gar78 on 2010-06-22
thanks for trying to help, but I couldn't find a dhcp file in any of the rc.d directories (i assume by "rcX.d" you meant "rc*.d"; I regarded them as the same thing.

I found a solution to my problem though here ([http://myubuntu.com/how-do-i-bridge-my-ethernet-and-wireless-on-my-laptop-in-ubuntu/]("http://myubuntu.com/how-do-i-bridge-my-ethernet-and-wireless-on-my-laptop-in-ubuntu/")). It now works fine. Thank you anyway.

Sincerely,
kroq-gar78

---

### Post by Iowan on 2010-06-22
:oops: Yes, I meant rc0.d, rc1.d... rc6.d (sorry). 
If your problem is fixed, you can mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

