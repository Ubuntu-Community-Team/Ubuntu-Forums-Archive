---
title: "Wireless printer using hp-setup"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by Unterseeboot_234 on 2012-01-12
The network works fine on Oneiric 11.10 (64-bit) for file sharing using a DNSModem router. I used the ubuntu wiki on including a wireless HP Photosmart. The printer did configure on an XP box. I did have USB cable connected to install wireless on the Windows box. Then I disconnect the cable, printer works for XP.

Using terminal, I sudo hp-setup and follow the onscreen. We do find the cable-router network, the printer, accepts encrypted key input and then setup says I can disconnect the USB.

I cannot print wireless. I can send over a print job. I have to connect the USB cable to the printer to get results. Under System Settings -> Printers [Show] the dialog tells me the printer is paused or off. The job queue always shows 'pending' with wireless. I have to connect the USB cable to clear the pending job ( I can't cancel a print job ).

---

### Post by Unterseeboot_234 on 2012-01-12
A google brings up forum discussions from 2008...

You have to connect the ip adddress with CUPS. Be sure you can ping the device on the connection you desire, eg wlan

Using the hp hplip in the terminal, which is included in Ubuntu

```
hp-makeuri <192.168.1.71>
```

Then, open a browser, set the location to
[http://http://localhost:631/](http://http://localhost:631/)

the address for the browser brings up CUPS
<xxx > is YOUR net node. do not put in the angle brackets, just the ip numbers.

In CUPS, Add a Printer. And you want the wireless printer you just created above.

My HP Photosmart C4500 had wireless built in and was listed as supported in the Ubuntu wiki.

---

