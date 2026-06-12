---
title: "USB760 verizon &amp; Jaunty (9.04)"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by tech_esq on 2010-03-30
I've had a 6 month saga of trying to get my Acer Aspire 5738Z to work with my Verizon USB760 mobile broadband device. I'm currently dual booting Windows 7 and Ubuntu 9.04 (Jaunty Jackalope). The background is that if I boot directly into Ubuntu (my primary OS), the OS will see the device, but only as a disk (it has a 2GB flash drive built into it). Using some commands from other threads covering this topic I was able to see that the OS might have been slightly aware of the modem, but not enough to make it usable in any convenient way.

Fast forward to my discovery a couple of weeks ago. I was working on my USB760 in Windows ('cuz that's where it works), and had to boot into Ubuntu to retrieve an e-mail. When I got into Ubuntu I discovered that the mobile broadband was working!! It just found it and I had a nice little antenna in my system tray. Through a little experimenting I've found the following "truths"

1.  It still doesn't work if I boot directly into Ubuntu.
2.  If I have the USB760 working in Windows, then shut all the way down, it will not work in Ubuntu.
3.  I must use the Verizon app, connect the WWAN and then "restart" and select Ubuntu for the USB760 to work.

As long as I play by those rules, I've had no problems with it for several weeks now.

Of course, this is not how I'd like to run things, but as work arounds go, it isn't too bad given the pay off. Having said all that, does anyone know an easy way to make the USB760 work in Ubuntu without doing this two step???

---

