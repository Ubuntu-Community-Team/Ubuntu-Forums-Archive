---
title: "WG511 poor connection/&quot;link quality&quot;"
date: 2005-12-09
forum: Networking &amp; Wireless
---

### Post by chambery on 2005-12-09
Hi all,

I have a Netgear WG511T wireless pcmcia card that works "out of the box" using 5.10 (thanks Ubuntu!).  Unfortunately the connection quality (as listed by network manager) never gets above 60% no matter how close or unobstructed the path to my Netgear MR814 router is.

I could be content with this situation, but recently got a Netgear WG111 usb wireless adapter for another computer and using ndiswrapper (which has a very user-friendly tool in [ndisgtk]("http://spohlenz.blogspot.com/2005/08/ndisgtk-updated.html") available through Synaptic) I get 100% link strength and noticeably faster network activity.  I tried to use ndiswrapper with my WG511, but it doesn't seem to show up in the Network Configuration.

Does anyone know how to override the kernel driver with ndiswrapper, or if this will even result in an improvement over what I currently have?

Thanks,

Todd


PS  my iwconfig output:

ath0      IEEE 802.11g  ESSID:"hideehi"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:09:5B:3A:77:BA
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=36/94  Signal level=-59 dBm  Noise level=-95 dBm
          Rx invalid nwid:66681  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:6   Missed beacon:0

---

### Post by Lambert on 2005-12-09
There are variables here such as driver and radio attenna used in the device. 

You can try to use ndiswrapper on the device to see if you get a difference. Here are the steps.

Bring down the device
remove the atheros driver

sudo modprobe -r ath_pci

then load the ndiswrapper module after drivers are installed

sudo modprobe ndiswrapper

bring up the device and see if using ndiswrapper helps at all. If you want to stick with ndis then just add this line

blacklist ath_pci

to /etc/modprobe.d/blacklist

---

### Post by chambery on 2005-12-21
Thanks for the advice.  I tried the ndiswrapper driver, but had no luck getting the card to come up (I found some posts suggesting I may have a troublesome version of the hardware).

Given that it works without effort through the Ubuntu defaults, I'll just use what the distro gives me.

Thanks for the help,

Todd

---

