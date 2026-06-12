---
title: "Broadcom driver not activating"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by my window broke on 2009-03-08
I have a problem, my friend has a Dell Inspiron E1705 with a 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

I already got fw-cutter and now it offers a b43 driver, but when I try to activate it, it only gets to 50% and then stops and doesn't activate it.

---

### Post by kevdog on 2009-03-08
Im not sure what you are meaning -- it gets 50%.  

Can you post 

iwlist scan
lshw -C network

Thanks.

---

### Post by Ayuthia on 2009-03-08
Like kevdog said, we are not for sure what you mean when it stops at 50%.  Do you have a working internet connection in Ubuntu?

If you don't you might try using the Broadcom STA version in System->Administration->Hardware Drivers.  It is a proprietary driver, but it does support your card.  

The b43 module (the fwcutter version) does provide more options (ability to switch to monitor mode) that the STA version does not.  However, the STA version does not require a download of firmware to make it work.

As kevdog also requests, please provide the results of iwlist scan and lshw -C network.  It will help us confirm if the firmware did get loaded or not.

---

