---
title: "wireless connection"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by 31chevy55 on 2011-11-11
I have recently installed Ubuntu 11.10 on my IBM Think-Pad and unable to establish a wireless connection to the Internet. The computer has installed a Belkin Wireless G Notebook Card, model F5D7010, Ver 7000.
 	Using the 'Terminal' and the command 'lspci' the card is recognized.
 	Also, using the command 'sudo lshw -c network' I believe there is a driver.
 	I have downloaded the firmware and driver for the card. However, it is an '.exe' file.
 	As I am a newbie to 'Linux', I need step by step instructions as to what I am to do next.
 	If I have gone about this the wrong way,please advise.

---

### Post by praseodym on 2011-11-11
Hi and welcome.

There are two different kinds of this card with either Realtek- or Ralink-Chipset. Please show the outputs of:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by 31chevy55 on 2011-11-12
How does one get the vertical line and should I press enter after each command line?

---

### Post by praseodym on 2011-11-12
The "vertical line" is (on a german keyboard): AltGr+< but you can also copy paste the lines. And yes: Press ENTER after each line

---

### Post by 31chevy55 on 2011-11-13
I have since reinstalled the  OS and noted.
 the following:
   1. The computer and OS 'see' the network.
   2. The computer and OS recognize the notebook card.
   3. The chip set is  Realtek RTL8185.
Must hard wire to connect to the internet.

---

### Post by 31chevy55 on 2011-11-18
Problem solved!!

---

