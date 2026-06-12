---
title: "can't connect to printer"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by sdom001 on 2012-02-20
Hello Everyone,
Newbie here to Ubuntu from Winblows. I am trying to add my printer which is wired to my router on my home network. It sees the network and sees a windows laptop I have on the network but not the printer or my wifes mac. Any help would be greatly appreciated.

---

### Post by 2F4U on 2012-02-20
Does the router have a print server incorporated? Then you would select the lpr protocol in the add printer dialogue, provide the IP address of the router and also the print queue name (this can usually be found in the router manual). Next you have to select the name of the printer manufacturer and the printer model, and after that, the dialogue will suggest a printer driver.

---

### Post by roelforg on 2012-02-20
All right, i'm just guessing here.
Is CUPS installed? if not, install it.

IIRC i did this:
```

sudo apt-get update
sudo apt-get install cups-pdf
sudo usermod -a -G lpadmin <your_username_here>

```
Fire up FF and go to [http://127.0.0.1:631/](http://127.0.0.1:631/)
If it asks you to login, use your ubuntu login.

---

### Post by sdom001 on 2012-02-20
Unless it came with the ubuntu 11.10 install it is not installed. I will look and try it.

* ok I installed cups from your instructions and see the pdf printer but still don't see the one on my network.

---

### Post by kurt18947 on 2012-02-20
> **sdom001 said:**
> Hello Everyone,
Newbie here to Ubuntu from Winblows. I am trying to add my printer which is wired to my router on my home network. It sees the network and sees a windows laptop I have on the network but not the printer or my wifes mac. Any help would be greatly appreciated.

What printer?  Some are no-brainers (Most HP)  Others are difficult or impossible; Some Canon and Lexmark printers can provide real challenges.  Which version of Ubuntu are you using?  Setting up printers in 10.04 or 10.10 is different than 11.10.  Is the printer connected to the router via a network cable or wirelessly?  Just making sure it's not a USB cable to a USB print server in the router.  Linux and hardware can be feast or famine.  Hardware support for windows is the hardware manufacturer's responsibility.  Manufacturers seem to not feel the same responsibility toward Linux.  Some are quite good, with others it's "What's Linux?  We don't know and don't want to know".  Any support for that hardware comes from skilled members of the Linux community.

---

### Post by sdom001 on 2012-02-23
Okay got it working. I found this forum thread 
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)
and followed the instructions and it worked.

---

### Post by Lee_Bo on 2012-02-23
Glad you got it resolved and thanks for posting your solution.

---

