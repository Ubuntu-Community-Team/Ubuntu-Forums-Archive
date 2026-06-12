---
title: "Differing Iperf results"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by statmonkey on 2009-05-13
Any network interface guru's out there?

Recently I noticed a huge variance between the transfer speeds of two machines running Ibex.  Using the ipef -p tests found at [http://openmaniak.com/iperf.php]("http://openmaniak.com/iperf.php") I found that one machine was basically double the transfer speed of the other.  That is when machine 1 is acting as a server under iperf and machine 2 connects to it the transfer speed is double that of the inverse (machine 1 connects to machine 2).

I ran lshw -C network and ethtools and both show the capacity at 1 GB for both nics.  I have seen differences on other machines but never as dramatic as this.  As I understand it, iperf is only testing the connection from nic to nic so I don't understand what the issue would be or what I can do to correct the disparity. It is especially frustrating because the Server is twice as fast at transferring as the client is.  The opposite of what one would want.  The interface is an RTL-8169 Gigabit Ethernet in both machines and they are connected through a TPL Gigabit Hub.  

Is there anything I can do (short of switching the cards)? One other thing that might have some impact.  The client machine has an unused nic in the box. although I can't image since it is disabled what effect that might have.

Thanks in advance

---

