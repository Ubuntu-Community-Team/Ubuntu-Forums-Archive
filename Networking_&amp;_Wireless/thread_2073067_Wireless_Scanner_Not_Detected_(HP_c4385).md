---
title: "Wireless Scanner Not Detected (HP c4385)"
date: 2012-10-18
forum: Networking &amp; Wireless
---

### Post by cirelosborn on 2012-10-18
I have been working on this for a few months now and finally fixed it.  Here is the story:

I have an HP Photosmart c4385.  It is a wireless Printer/Scanner.  After performing clean installs of older and newer Ubuntu distributions I found that I could still printer wirelessly with no problem with install or functionality.  However, the scanner only worked if it was connected via USB.  I have done simple installs, cups updates, Xsane configurations, IP adds, everything that I could find or think about doing and nothing worked.  I even downloaded the system setup from HP.com support and drivers (of which the Ubuntu 12.04 version is broken) and still nothing.  

I have been doing IP configurations on printers at my office and came across an administrative printer configuration.  

If you run this code in terminal (Ctrl+Alt+T to launch terminal):
```
system-config-printer
```

It will launch a printer configuration and if you click on ADD, then click on "Network Printer", then after waiting you should see your networked printer (You should have already connected you printer to your WIFI) in my case it was HP Photosmart C4385 (IP Number).  Then under "Connection" you can select any of these to print from, but only the "HP Linux Imaging and Printing (HPLIP)" will allow you to print and scan wirelessly.  Run through setup, duplexer (if you have one), and close when your done.

You should be all set.  I hope this helps somebody.

---

