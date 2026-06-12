---
title: "Ettercap Send L3 Error"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by dansofe0r on 2013-02-08
Hello everyone. Hope you're all doing well. I'm staying indoors while the blizzard's wrath falls upon my home. I thought, why not try out ettercap? 

It is very nifty and fun to use. It is one of the first programs that I have used for arp poisoning that aren't copied from a textbook. 

Here is how I arrive at the problem that I am having. I start the program in graphic mode from the terminal. Scan for hosts. List hosts. Choose my laptop in my local network that I want to use as the target 1 computer. Then use the router as the target 2. Then run the arp poison utility. All looks good on the target laptop's wireshark monitor. It shows my pc's mac address instead of the router's. 

Then I 'start sniffing' and it goes well for a whole few seconds before the error comes up: 

```
SEND L3 ERROR: 1582 byte packet (0800:06) destined to 192.168.1.111 was not forwarded (libnet_write_raw_ipv4(): -1 bytes written (Message too long)
)
```

I would like to know how to fix this. Thank you very much!

---

### Post by autostart-ini on 2013-12-25
Not sure if you've fixed the problem by now but I think this might by the answer, and I quote:


                                                "This is not a libnet issue, it is a Linux issue. It  is due to the different offloads that ethtool enables on the interface  by default. I have added to the latest code in master code that will  disable this on Linux. To fix these errors, you can type the following  command:

  ethtool -K eth0 tso off gso off gro off lro off

  Substitue eth0 with the actual interface."

hope this helps anyone.



source: [https://github.com/Ettercap/ettercap/issues/71](https://github.com/Ettercap/ettercap/issues/71)

---

