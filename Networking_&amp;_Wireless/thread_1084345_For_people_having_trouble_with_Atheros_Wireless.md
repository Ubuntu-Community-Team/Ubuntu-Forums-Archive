---
title: "For people having trouble with Atheros Wireless"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by Atrophy on 2009-03-01
Hi everyone! I just installed 8.10 for the first time. In fact, I haven't used any Linux distro before at all, so i'm brand new to this. Anyways, after I got everything installed properly, my wireless card (Atheros AR928X) was acting totally wacky. I've been seeing a lot of people having trouble with the Atheors 9x cards regarding the wireless not showing any networks, or showing networks but not connecting to anything. This is how I fixed it so now I can see all networks in the area and connect every time.

First, find a wired connection. Connect to that, and then run your package manager and install all updates and program fixes and whatnot. Then open terminal and run 'sudo apt-get install linux-backports-modules-intrepid-generic' and reboot. 

That should do it. After 4 days of trying to install madwifi and other drives with no success, this did the trick for me. Surprisingly simple.

Good luck!

---

### Post by Simyager on 2009-03-02
I have a different problem I can only connect to the internet via wifi. So could you help me please?:confused: I also did install 8.10 64bit and look [here]("http://ubuntuforums.org/showthread.php?t=1083030") for more info and [here]("http://ubuntuforums.org/showthread.php?t=1081924&page=2"). Please help me and thanks in advance.

---

### Post by Atrophy on 2009-03-02
I dont understand your issue entirely. Do you mean that you do not have access to a wired connection? If this is the case, you are in the same boat as I 3 days ago =/. I was unable to get anything to work for a long time until I found a wired connection, and followed the aforementioned procedure.

---

