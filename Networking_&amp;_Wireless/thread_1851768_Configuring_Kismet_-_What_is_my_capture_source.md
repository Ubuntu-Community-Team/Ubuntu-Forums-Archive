---
title: "Configuring Kismet - What is my capture source?"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by hashes on 2011-09-28
I have a Toshiba Satellite M645. Trying to use Kismet through BackTrack 5.
Kismet states; Kismet will not be able to capture any data until a capture interface is added. Add a source now?
 
With the command: lspci, i find the following:
 
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
 
Network controller: Intel Corporation WiMAX/WiFi Link 6050 Series (rev 5f)
 
Is RTL8101E the name of my network card?
Is RTL8101E my capture source?

---

### Post by Dangertux on 2011-09-28
Well this isn't something that is particularly supported here, and may (depending on where this is going be against the code of conduct). That being said, the answer to your question is which one are you trying to capture data from?

I'll give you a hint, it's probably your wireless network interface :-)

---

### Post by hashes on 2011-09-29
I see your point about code of conduct. I did have Kismet installed on another laptop earlier, with Ubuntu as the OS. And I guess BackTrack also is an Ubuntu sort of OS. I did take a look at the kismet.conf file on that other computer. I wasn't the one that installed it. I got help doing that part. This time I thought it would be appropriate to try myself.
 
What I did find out is that the kismet conf file had:
source=ath5k, wlan0, addmee
 
So from what I have learned so far, Kismet has changed this file a bit. Instead of source it now states ncsource (nc=newcore?)
 
I have added ncsource=wlan0:r8101=intel
 
Is this correct?
**wlan0**, because ifconfig shows a wlan0
**r8101**, because the ethernet card says RTL8101E/RTL8102E and I have read that the TL in RTL is removed when entering it in the config file. I don't know the reason for this.
**intel**, because I see it in examples and when Realtek is described, even though I keep thinking that "realtek" should substitute intel.
 
It seems Kismet is working. At least it's not coming up with any errors. I am not home at the moment so I don't have my wireless network to try it on.
Am I at least on the right track? ;)

---

