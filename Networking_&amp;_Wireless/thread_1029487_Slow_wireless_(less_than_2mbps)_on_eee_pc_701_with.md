---
title: "Slow wireless (less than 2mbps) on eee pc 701 with array kernel"
date: 2009-01-03
forum: Networking &amp; Wireless
---

### Post by nerver on 2009-01-03
Hey everyone,

I'm hoping someone else has experienced this and might know of a solution as I have not been able to find anything on the net so far.

I recently got an eee pc 701 and I've since installed Ubuntu 8.10 on it and swicthed to the Intrepid EeePC kernel (2.6.27-8-eeepc) following the instructions here:

[http://www.array.org/ubuntu/setup-intrepid.html](http://www.array.org/ubuntu/setup-intrepid.html)

Everything works on the eee pc, however I cannot seem to get reasonable wireless speeds on my home network. I ran some tests with iperf and the fastest I can get is 1.96 Mbps with the wireless. With the wired connection I get 96 Mbps. I have 97% signal strength and all the options on my router are setup correctly (I can get up to 22 Mbps on my work laptop wireless and 15 Mbps on my other Ubuntu laptop wireless).

Is this just the limitation of the eee pc wireless or is there something I can tweak/fix? 
Any help would be greatly appreciated as I need to get close to 10 Mbps out of the wireless to use it for its intended purposes.

Cheers :)
-Sean

---

### Post by nerver on 2009-01-06
No one else has experienced this on an eee pc? Hmmm. Well, maybe I will try some other eee pc distros and see if that makes any difference.

---

### Post by nerver on 2009-01-14
Ok, so I've narrowed down the problem and I'm hoping its a bit simpler to resolve now.

I installed a few different distros on the eee pc and the only one that had good wireless speeds was Ubuntu-eee based on the 8.04 release and it seems that Ubuntu-eee used the ath_pci driver for the atheros 242x wireless while all the other distros used the ath5k_pci driver which is slow.

So my new question is:  Does anybody know how I can change the wireless driver from the ath5k_pci to the older ath_pci in Ubuntu 8.10?

Thanks,
-Sean

---

### Post by timebomb on 2009-01-17
I've noticed the same thing on my 900, but have not had time to investigate. My first search brought me to your post. I used the same install instructions.

---

### Post by nerver on 2009-01-17
I actually found a solution a few days ago for this. Here are the steps I used to get my wireless working. Hopefully it will help with your 900.

First make sure you have installed the array kernal and repository then in a terminal:

Step 1: sudo apt-get install build-essential

Step 2: sudo apt-get install linux-headers-`uname -r`
this will install the kernel headers (copy the above line exactly) to allow build-essential to work with the eeepc kernel

Step 3: (this does not necessarily have to be done in the terminal) download and extract file: madwifi-hal-0.10.5.6-r3835-20080801.tar.gz
(i'm sorry i don't remember the link where I found it.. if you can't find it on google let me know and i can email it to you)

Step 4: cd into the directory that you extracted the above file to

Step 5: make

Step 6: sudo make install

The next step you may or may not have to do. For me everything worked fine after completing step 6 and rebooting. But if it doesn't try step 7 and reboot again.

Step 7: sudo gedit /etc/modprobe.d/blacklist
(or use whatever text editor you like) and add the following line:
blacklist ath5k_pci

Hope that helps. My wireless is now operating at about 14Mbps actual throughput which while not the fastest ever is working well for my purposes.

Cheers,
-Sean

---

