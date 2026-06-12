---
title: "Wireless Linksys/Ubuntu 10/HP Pavillion A6710T"
date: 2010-05-08
forum: Networking &amp; Wireless
---

### Post by therjnel on 2010-05-08
See attached documents for HOWTO step results and results of "make" command for WUSB600N.tar
 
Additionally I am connecting to a wrt160n v3 router using mac filtering and not broadcasting the SSID without any additional security being used.
 
As a note, when reading the word document, I did create headings you can search for, for instance, the HOWTO requirements for a wireless post ask for the 'lspci' command to be run and I put the results following a line which says 'lspci results'.  Where nothing resulted, I noted 'nothing.' as the results.
 
Thanks,
Rob

---

### Post by chili555 on 2010-05-08
You have two conflicting drivers loading and their ugly wrestling match is not allowing proper operation of your wireless device. Let's throw one out, along with his dependencies:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will pop open and we will add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully, save and close gedit. Reboot and make a nice post telling everyone how beautifully your wireless works.

---

### Post by therjnel on 2010-05-08
I wish I could say that everything was working fine now, but I must have something misconfigured still.  I'm attaching the document again that details the responses now.  I am unsure why I cannot connect.  I can connect fine when I boot to windows so I doubt it is something on the router.  Thanks for taking the time to look at this.
 
As a note, there are some things that replied now with data differently, but mostly it seems the same replies came through.  Most notably to me the ifconfig, iwconfig, and lsmod commands had new or different information.  I believe the iwlist scan replied differently too.
 
Rob

---

### Post by chili555 on 2010-05-08
Your scan results show that the card is working correctly. What happens when you click the Network Manager icon? Does it show your network now? Can you click it and connect? Does it ask for your password or key?

---

### Post by therjnel on 2010-05-08
It shows my network and it attempts to connect, however it is not able to.  I'm not sure what may be the problem now as Windows Vista is able to connect to it.  I do not have WPA or WEP security configured, only mac address filtering.  I do have the router configured only to operate with wireless N.  I'll have to try configuring the router differently to see if any changes there provide any better success.
 
Rob

---

### Post by chili555 on 2010-05-08
> I do have the router configured only to operate with wireless N. I suggest setting it to mixed B, G and N speeds, rather than N exclusively.

---

### Post by therjnel on 2010-05-08
Actually it was setting it to mixed modes that finally did the trick.  Funny thing is that it actually does seem to be connecting and running at N speed so I'm not sure why they're behaving that finicky!  Success at last.  Thanks for all the help!

Rob

---

