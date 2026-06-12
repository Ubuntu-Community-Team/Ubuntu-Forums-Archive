---
title: "wireless connection problem"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by chemsoul on 2006-06-15
Hello,

First of all, if it wasn't clear enough, let me state that I'm an Ubuntu noob. I installed the latest version (6.06) but I can't manage to connect to the internet. 

I get a green icon next to the clock. The connection status keeps changing idle-sending-receiving during the first 10 min, then it stays idle. When I type a website in the browser it stays looking up for [www..](www..)..  and then I get a "server not found error". When I ping an ip, all packages get lost...Can you help me?

I've written my ESSID and my WEP-key in "networking->eth1->properties", and I've also fulfilled the IP, netmask, default gateway and dns. I've activated eth1 and chosen it as my default gateway device and, finally, I've chosen it in the 2 computers icon, next to the sound one...

Thanks in advance for your help.

chemsoul

P.S. I'm not sure if it should go in network or wireless hardware support forum

---

### Post by Slicedbread on 2006-06-15
What wireless card do you have, and are you sure it is installed correctly- the network manager icon could be flashing for lo/eth0 instead of your wireless connection.

Go to the terminal and type "iwlist scan" to see if you get any scan results.

---

### Post by chemsoul on 2006-06-15
I've got an Intel 2200BG

That's what I get:

> 
iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: MM:MM:MM:MM:MM:MM (I don't think it is needed:))
                    ESSID:"3727564885"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:9
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54
                    Quality=71/100  Signal level=-57 dBm
                    Extra: Last beacon: 2079ms ago



---

