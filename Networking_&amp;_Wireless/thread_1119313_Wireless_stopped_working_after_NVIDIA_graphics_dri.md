---
title: "Wireless stopped working after NVIDIA graphics driver install"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by chicobo329 on 2009-04-07
It's very strange, after a fresh install here I had gotten a lot of things working correctly on here for a while!

I'm using 8.10. When I came back from work and booted up the computer, Ubuntu pointed out to me a new version of the NVIDIA accelerated graphics driver (180), I was previously using 177. So I went to install that and it worked and wanted a restart.

Upon restarting the computer, the wireless stopped working :^P This is clearly very annoying, I can't possibly see how both are related to each other!

I was using the Broadcom STA wireless driver which was on the whole time, no ndiswrapper stuff involved (in fact it's still on even though wireless isn't working). What can I do?

EDIT: Sorry I forgot to make clear I'm using a Broadcom Wireless, 4300 series I believe.

If I deactivate the Broadcom driver, there's no 'Wireless Networks' section in the Network Manager. If I activate it, it shows one, even though it's completely empty. I also reverted all the way back to NVIDIA 173 and I still have no success in getting my wireless working again.

---

### Post by chicobo329 on 2009-04-08
Tried to upgrade to 9.04 to see if that would help but it failed at the very end because of a problem with b43-fwcutter. Ethernet was disabled while this happened so I couldn't report the problem at all and couldn't get any information. It was near the very end, I'm on a mostly complete 9.04 now, and it never performed the cleanup steps. Crap.

Ethernet now works but wireless still doesn't and now I have a slightly botched upgrade too :^P

---

