---
title: "Edimax EW-7722In non-functional"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by emcake on 2012-01-26
Hey there,

I've been browsing everything I can find in relation to this card and I've come up against a brick wall. Can anyone offer any further advice? Here's what I've done:

- I've got the linux version of the drivers from the Edimax website. - 2010_07_16_RT3062_Linux_STA_2.4.0.0

- I've changed the wpa_supplicant configuration settings, compiled the drivers, built them and installed them and blacklisted the old RT2 drivers.

- I've activated the new module and it activates on start up. The card sits with both lights on, the TX light blinking every 5 seconds.

Here's the standard command outputs:

lsmod:
> matt@aperture:~$ lsmod |grep -e rt2 -e rt3
rt3562sta             914916  1 


lspci:
> 03:06.0 Network controller [0280]: Ralink corp. Device [1814:3062]
	Subsystem: Edimax Computer Co. Device [1432:7722]
	Kernel driver in use: rt2860
	Kernel modules: rt3562sta, rt2800pci


Note that the driver it says is in use is rt2860, even though it's not installed. Is this part of the problem or a red herring? On the plus side is correctly identifying it as an Edimax chip, and the model number of 7722.

iwlist:
> matt@aperture:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ra0       No scan results


> matt@aperture:~$ iwlist ra0 channel
ra0       13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)


> matt@aperture:~$ iwlist ra0 rate
ra0       unknown bit-rate information.
          Current Bit Rate:1 Mb/s


dmesg:
> matt@aperture:~$ cat /var/log/dmesg |grep rt3
[   22.012250] rt3562sta: module license 'unspecified' taints kernel.


Let me know if you need any other info.

Hope you guys can help!

---

