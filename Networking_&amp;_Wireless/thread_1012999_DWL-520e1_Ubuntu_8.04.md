---
title: "DWL-520e1 Ubuntu 8.04"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by maverickzyx on 2008-12-16
Hello, I am a new user to Ubuntu.  I played with Ubuntu 8.10 but some bugs and lack of some modules got me annoyed so I am now on Ubuntu 8.04.
I have a D-Link DWL-520 e1, which has an Intersil Prism 2.5 chipset, and am trying to set up a wireless network, the router works and is all set up already.  I have read all I could about firmware and hostap and ndiswrapper.  And it's a lot of stuff to wrap my head around.  From what I understand, I need to modify the firmware on the NIC.
I have it down to two options.

The first it seems is the Jun Sun method using prism2_srec from hostap.  [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)
The second is editing the interfaces file in /etc/network.  [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)

They appear to be two different and separate methods, which one is more likely to work with Ubuntu 8.04?  Thank you.

---

### Post by maverickzyx on 2008-12-16
Using a wired connection and a laptop with internet sharing turned on I was able to make it work.

Using the wired internet I was able to download the available hostap and hostap-utils through the Synaptic Package Manager.
Having the primary and secondary firmware I was able to use:

prism2_srec -gs wlan0 /etc/firmware/pm010102.hex
prism2_srec -gp wlan0 /etc/firmware/pm010102.hex
prism2_srec -rp wlan0 /etc/firmware/rf010804.hex

to make the NIC work.

---

### Post by malangaman on 2009-07-03
Finally Success!
I have the DWL-520e1 wireless card up and running on Ubuntu 8.04 Hardy Heron.

 Links that were useful in solving the puzzle were:

1. [http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)
2. [http://www.dlink.com/products/?pid=DWL-520&tab=1](http://www.dlink.com/products/?pid=DWL-520&tab=1)
3. [https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1](https://help.ubuntu.com/community/WifiDocs/Device/DWL-520vE1)
4. [http://ubuntuforums.org/showthread.php?t=643467&highlight=dwl+520+rev](http://ubuntuforums.org/showthread.php?t=643467&highlight=dwl+520+rev)

and the useful post by maverickzyx above.

I had to use the command line to place the firmware in the locations suggested by hwertz although no mention is made of how to get  Latest-prism.tar.bz2  and when to use sudo and gedit. 
(link number 4. which is the one I ended up following although the other links provide source of firmware and understanding.)

I found link number 3. out of date and unnecessarily complex for 8.04 but it increased the understanding of the problem and was nonetheless helpful.

Anyway, the links above have all the guidance needed to get the card working in 8.04.

I want to thank all those that have selflessly contributed to the resolution of this problem.
:lolflag:

---

### Post by malangaman on 2009-11-07
Well the DWL-520e1 mercifully expired suddenly a couple of days ago. The drudgery of the installation for DWL-520e1 was awful. Hours of trouble and frustration, although victory was sweet when finally achieved. But all your loved ones think you are nuts to spend so much time trying to make the darn thing work. Don't you value your time?

This time I googled every pci wireless card at the COMP-USA store before hand and found that there has been great success with D-Link WDA-1320, so I bought it for $29.

Truly, it was bliss to see Ubuntu Hardy 8.04.3 recognize it immediately. What a difference when it works right out of the box!

Kubuntu 9.10 Karmic on a separate partition also recognized it instantly and put it to work effortlessly.

Win XP in the third partition, recognized it as well, after the installation of the Drivers from the CD.

Thank you D-Link WDA-1320

---

