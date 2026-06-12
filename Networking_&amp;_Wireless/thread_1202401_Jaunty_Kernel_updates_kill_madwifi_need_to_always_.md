---
title: "Jaunty Kernel updates kill madwifi need to always remake/install"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by dBuster on 2009-07-02
Okay lets see if I can pick the brains of those here.  I have been using Jaunty 64bit since Alpha 3 and at that time to get my Compaq CQ60-215dx to go wireless I needed to use the madwifi drivers for the Atheros Communications Inc. AR242x wireless card.  

The drivers are great!  However, each time you receive a kernel update I am continuously having to remake and reinstall the drivers, madwifi that is.  I have heard and seen posts that the Jaunty release has support for the Atheros chipsets in the release.  I think though since I have been using the madwifi drivers those release version ones are not loaded.  I am not about to do a clean install to get the new drivers going and I would love to be able to not have to worry about getting a kernel update.

1.  Does anyone have a clue as to how I can safely and completely remove the madwifi and get the atheros drivers in Jaunty to come alive and take over?  

2.  Does anyone know what the exact drivers are that come with Jaunty?

3.  If they are madwifi drivers in the final release how do I get mine to not require the remake/install each kernel update?

I do have a usb wifi adapter I can use to connect once I remove madwifi so I can download what ever I need after removing those drivers, just in case I need to *gulp* go back to what I just removed...

Any assistance, ideas, solutions would be amazing!  Thanks in advance!

I may be breaking the forum rules but I am double posting this.  Once in Hardware & Laptops and the other in Networking & Wireless to see if I can get an answer as this is not the first time I am trying to resolve this.  Please if it is breaking the rules, administrators of the forums, remove the one that will least likely get me an answer...  Thank you.

---

### Post by superprash2003 on 2009-07-02
these happen sometimes with ndiswrapper as well.. wifi goes sometimes when new kernels are installed

---

### Post by dBuster on 2009-07-02
So then are you saying that ndiswrapper is the other way for the Atheros chipset?  I had to use ndiswrapper my last laptop with a different chipset but still had to use it and never did I have to go through make/install over again after a kernel update...

---

