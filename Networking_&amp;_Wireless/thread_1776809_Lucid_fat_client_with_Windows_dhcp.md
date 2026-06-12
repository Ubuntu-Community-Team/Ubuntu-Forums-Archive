---
title: "Lucid fat client with Windows dhcp"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by theller on 2011-06-06
I set up an isolated fat client system (6) with 2 nics and it worked. [/UbuntuLTSP/FatClients]("https://help.ubuntu.com/community/UbuntuLTSP/FatClients")

When I connected it to the school network it worked with the first client (after we turned off zenworks). [/UbuntuLTSP/LTSPWindowsDHCP]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPWindowsDHCP")

The first client and I mean only that machine will pxeboot. Any other machine that we put the Mac address in the windows DHCP will not pxeboot. It gives a tftp timeout. I ran gpxe and discovered 2 problems

[LIST=1]
[*]The other machines/clients are getting the wrong address for  the next server which I guess would be the tftp or ubuntu server. They were assigned the right ip address, static address we put in with the Mac of the machine we were trying to boot.
[*]The clients are also getting the wrong path for the prelinux0 file.
[/LIST]
How do I change these and why does one machine work? I have updated and even built a new client image. (puzzled face)

---

### Post by theller on 2011-06-07
The problem is solved by going windows only. So sad, The other network person is hardcore windows and I just can't fight anymore. It's really sad for the students. I had all of the students in our middle school using ubuntu and they liked it. I handed out many discs. Now I have to teach on windows(very sad face).

---

