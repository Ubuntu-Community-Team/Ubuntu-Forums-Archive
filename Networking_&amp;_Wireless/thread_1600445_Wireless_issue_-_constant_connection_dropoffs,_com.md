---
title: "Wireless issue - constant connection dropoffs, comp freezes"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by deciding39 on 2010-10-19
All right guys, forgive me if this situation has already been addressed on here somewhere. I've been a good n00b and have not posted in the two years or so I've been on these forums because my questions have usually already been answered. This time though, google/forum searches have failed me so your help is much appreciated!

I've been using a Netgear WG311v3 wireless card to connect to the internet successfully since 8.10, thanks to ndiswrapper. However, since 10.04 I've had some serious issues with this card (at least...I think it's the card). I updated to Meerkat hoping that the problem might fix itself, but it's still there. Here's the situation:

The problem most often occurs when I'm running Transmission, but also Firefox. It also happens when streaming videos to my xbox via uShare...basically, any time I'm using the internet. 

Suddenly, my download in Transmission will drop to 0.0 KiB/s or in Firefox, pages will stop loading. If I close and try to reopen Firefox, it tells me the process is already running. If I try to restart, it says firefox-bin is still running. I click reboot anyway, and the computer hangs indefinitely at the purple Ubuntu shutdown screen. 

The terminal also freezes if I try to run any commands that are wireless related, for example iwconfig or ifconfig. I have to close the terminal to kill the process.

I've also had more serious crashes when running Transmission where absolutely everything freezes and a hard reset is my only way out.

Forgive my n00bishness and let me know what other information I can provide you with. And if this has already been answered, please kindly point me in the direction of said answer :)

Thanks!

---

### Post by Wtower on 2010-11-03
Hi,

I have similar issues. It might be slightly complicated. So far I have found the following causes.

a. I changed my connection from dhcp to a static address and this might have solved some of my router disconnection issues. Besides, since that pc is a home desktop, no need for dynamic ips. Relevant thread: [http://ubuntuforums.org/showthread.php?t=1004692]("http://ubuntuforums.org/showthread.php?t=1004692")

b. Second I have found that a slightly reduced performance of the wireless connection (because of obstacles etc) greatly affects the situation.

c. Another cause is described here: [http://forum.utorrent.com/viewtopic.php?id=47523]("http://forum.utorrent.com/viewtopic.php?id=47523")
With such number of connections a great deal of bandwidth is spent cycling over all connections. Reducing the number of maximum connections makes things far better as far as connection drops is concerned.

d. Now the freeze issue. That also I have. After having read hundreds of relevant threads and articles I come to the conclusion that it can be anything and needs a lot of looking into. For my pc I *might* have narrowed it down to the graphics card.

Hope it helps.

Regards

---

### Post by dscott422 on 2011-06-05
This thread is a little old, but I am sad to see no solution because I have the same problem.  Using firefox and doing either intensive downloading or uploading, my wireless connection freezes.  The transfer rate drops to zero.  I have to manually disconnect the connection and then reconnect using the Network Manager.  Then is starts working again.  My computer dual boots between Ubuntu 11.04 and Windows 7.  The computer does not have this problem using Windows 7.  Only in Ubuntu.  Any suggestions would be greatly appreciated as I am trying to continue to migrate away from Windows and do increasing number of tasks using Ubuntu.

---

