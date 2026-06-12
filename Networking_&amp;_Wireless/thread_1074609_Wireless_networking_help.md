---
title: "Wireless networking help"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by ffmurray on 2009-02-19
I just did a clean install of ubuntu on my acer 5315 laptop.  I think i installed the driver, I followed the instructions posted here [http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/) and everything seemed to go fine.  I'm trying to connect to my home wireless network but it wont show up or when I try to manually connect it will not connect.  It works fine with the Ethernet plugged in.   I dont really know much about Linux, as this is my first try with it and any help would be greatly appreciated.

---

### Post by Ketara on 2009-02-19
Can you see other wireless networks or is it just your home network that you can't get to?

I'm going to assume you can't see any, in which case can you please post the output of:

lspci

Just so we're sure what your card is. If it is an ar242x, more troubleshooting:

Do you have the ath5k driver enabled and the HAL access layer driver disabled in hardware drivers? (system->administration->hardware drivers)

Do you have anything strange blacklisted? Open a terminal and type in:

gksudo gedit /etc/modprobe.d/blacklist

(note: Be very careful whenever you use gedit with root priveleges, as accidents can cause serious system damage)

Once you're there, look for any lines that say "blacklist ath5k" or "blacklist ath9k" and comment them by adding a # to the line so it reads "# blacklist ath5k" instead.

Also, if you do not have the following lines at the bottom, add them:

blacklist ath_hal
blacklist ath_pci

If none of that changes anything, there are other things we can do, but lets try that first.

---

### Post by ffmurray on 2009-02-19
adding the two new blacklists fixed the problem.
Thanks

---

