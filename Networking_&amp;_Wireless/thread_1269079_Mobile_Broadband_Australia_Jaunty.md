---
title: "Mobile Broadband Australia Jaunty"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by brianmck on 2009-09-17
Just to share my experiences in Aus. First tried a Telstra 3G usb card (based on ZTE? chipset I think). Hopeless - not detected and requires reconfiguration work to get it into modem mode, then won't work with windows. So returned it for a refund. Research shows the Optus and Vodafone modems based on Huawei chip work OK. Purchased the Vodafone one (K53520) and it is detected straight away and loads the option module but wouldn't connect. Further research shows that the Network Manager template for Vodafone is OK for the contract Vodafone network but not the prepaid. Have to change the APN to vfprepaymbb. Now it works great!

Brian

---

### Post by brianmck on 2009-11-04
Karmic update.

Vodafone connection now broken! Changed to the Telstra prepaid turbo modem (Sierra 301). This is detected by NM and works at incredible speed - however DNS needs to be set manually.

Note I moved to a regional centre and the Vodafone service was useless - GRPS only. But note they have a GUI which is great (available from Betavine)

Brian

---

### Post by amosshapira on 2010-01-19
Hi,

Are you referring to the Telstra "Turbo USB Modem Plus" sold at [this page]("http://www.telstra.com.au/bigpond_internet/get-started.html") for $149?

I'm looking to buy one for my workplace and need to make sure it works with my team's Ubuntu laptops (currently all running 9.10).

Thanks.

---

### Post by pdc on 2010-01-19
I suspect this device is a ZTE MF636 modem;

some have got it working with wvdial; the latest 9.10 Ubuntu had problems with the first release; I sense now upgrading to the latest kernel has allowed more modems to work;

if you search on "ubuntu configure MF636" you will find some posts; I believe it worked with earlier versions of Ubuntu too

---

