---
title: "Network Manager and Network Tools problems"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by skywatcher on 2010-10-20
After trying various suggestions I managed to successfully set up file and printer sharing on eth0 between two laptop computers, one running on 9.10 and the other on 10.04.

I now want to go a step further and share my wireless internet connection on the 9.10 machine with the 10.04 machine, but somewhere along the line I must have changed configuration files or something, because I now experience the following two problems.

Problem 1: I right-click on the network manager, then select Edit Connections > Wired > Add. Then I make the necessary changes and click on Apply. I am then asked for my password, which I enter. I am back at the Network Connections window, but the new connection that I have just created, is not there. This happens on both machines, but on the 9.10 machine there is an additional problem: it shows a wired connection called 'ifupdown(eth0)' which I cannot edit or delete because those two buttons are blanked out.

Problem 2: On the 9.10 machine I go to System > Administration > Network Tools and select Ethernet Interface (eth0). When I click on Configure I am asked for my password, which I enter, but then I get a message that tells me the interface does not exist! Yet, when I ping the other machine, it works (in both directions).

Please can someone tell me what the causes of these problems might be.

Thanks.

---

