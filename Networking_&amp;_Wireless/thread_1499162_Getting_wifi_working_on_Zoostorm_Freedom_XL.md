---
title: "Getting wifi working on Zoostorm Freedom XL"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by faulknerm on 2010-06-01
Evening all,

I've recently invested in a new netbook, a Zoostorm Freedom XL and decided to install the Ubunto Netbook Remix alongside the Windows 7 starter edition which comes preinstalled.

Everything went amazingly smoothly, and I now have a 99% working system - the only issue is the wireless networking.

The wifi adapter doesn't seem to be being recognised by the Ubuntu install at all, to the extent that even using the wifi hotkey the wifi indicator does not come on and I cannot access wireless networks.

I've done a bit of reading, and it seems that ndiswrapper may be the solution I'm looking for, however I'm not entirely sure how to go about implementing this.


The network card, in Windows, is simply recognised as "802.11n Wireless Lan Card" and the device manager properties suggest it's manufactured by Ralink and using driver version 3.0.8.0.

Any help anybody can offer would be massively appreciated, :)

Thanks in advance!!

---

### Post by txt3rob on 2010-06-17
It's a ralink RT3090
check [http://www.ralink.com](http://www.ralink.com) for drivers or apt-get

---

### Post by andersja on 2010-07-09
See also: [https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/~markus-tisoft/+archive/rt3090")

---

### Post by Velvetspacetime on 2010-07-23
Hey there. I see you got the Zoostorm netbook? So did I - I installed ubuntu and have the same errors. No net with ethernet - wireless card not even installed. How on earth did you fix it I can't find a solution anywhere!?

My Ethernet is connected to my hub and modem - it's telling me I've got a good IP etc, it even shows upload and download packets - but I can't connect to the internet via a browser or apt-get downloads.

I haven't even STARTED on the wifi yet... any help?

---

### Post by taylorb6 on 2011-09-21
I have had a similar problem and found this to work for me - I am using ubuntu 11.04 but had same problem in 10.10 - 

I listed the modules loaded using:

$ lsmod | grep rt*

and found the following:

rt2800lib
rt2800pci
rt2x00lib
rt2x00pci
rt2860sta

I then used this command to confirm my card version:

$ lspci | grep Ra*

Mine is a Ralink rt3090.

The original post on another web found that blacklisting the following modules and rebooting fixed the problem. The command used was:

echo "
blacklist rt2800lib
blacklist rt2800pci
blacklist rt2x00usb
" | sudo tee -a /etc/modprobe.d/blacklist.conf

My listing of modules didn't show the rt2x00usb but I left it in the command anyway and after running the command I rebooted the pc and the wireless connected and is now working. 
Hope this helps.

---

