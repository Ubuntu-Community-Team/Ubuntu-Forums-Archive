---
title: "Ubuntu 9.04 Wireless Less Sensitive than Windows"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by toppatopvt on 2009-06-12
Hello everyone,

Did some searching around on the topic and found nothing really helpful. The problem is simple and it has been mentioned so many times it is not even funny. Each time I see it mentioned it goes unanswered so I'm trying to get lucky.

My wireless card (Atheros) works under Ubuntu but it doesn't seem to be very sensitive. A 802.11n network that shows a "Very Good" connection on Windows is "Low" at best on Ubuntu with the corresponding performance degrades. So I already tried:

sudo iwconfig sens [anything]

...and it says that it's not supported on my wireless card.

Anyway, it definitely seems to be a sensitivity issue and I was wondering if i could increase the sensitivity some other way, but right now the wireless sensitivity seems to be inferior to that on Windows. That's the only thing forcing me to use Windows in my present location. Otherwise....[let's not go over that, the choice is obvious]

Thanks :popcorn:

---

### Post by jimv on 2009-06-12
The only thing I can think of is try using Ndiswrapper with the Windows driver and see if that gives you better signal strength.  That worked for me.

---

### Post by toppatopvt on 2009-06-12
Hello again,

Thanks for the reply. The windows drivers did work but not much help either. Setting the sensitivity using the windows driver also failed. So now I've uninstalled ndiswrapper and now I have no wireless altogether. I presume the original driver is somewhere and just needs to be enabled. I've already cleared the blacklist and rebooted but still nothing.

Does anyone have any instructions for enabling the old driver?

---

