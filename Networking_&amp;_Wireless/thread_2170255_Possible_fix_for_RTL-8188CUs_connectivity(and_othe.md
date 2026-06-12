---
title: "Possible fix for RTL-8188CUs connectivity(and others??)"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-08-25
I'm starting a new thread rather than posting to an existing RTL-8188CUs thread because this may apply to other WiFi adapters in addition to my problem child.  The RTL-8188CUs based adapters have not worked well with open drivers since they were introduced AFAIK.  My experience has been that the adapter(Edimax EW-7811Un in my case) is recognized and will connect.  It will work properly for a few minutes then simply quit responding, ping says no host. My solution was to use the drivers from RealTek until they wouldn't compile on 13.04 onward then I used Tim Phillips' .deb package on 13.04.  Tim's solution will not work on 13.10 to date. Said to myself "let's plug the little fella in and see if there's been any progress." I plugged the adapter into a machine running 13.10 and it didn't even light up, the module did not load.  That was easy to fix but then came the familiar story.  It connected, worked for a few minutes and stopped.

A scan of 'dmesg' this time yielded a clue.  Something about a missing package, "nss-myhostname".  I fired up synaptic and sure enough, the package was available in the repository but not installed on my machine. I installed, rebooted just for luck, reloaded the module and so far so good.  I've been using the Edimax adapter in 13.10 & 12.04.3. I've been web surfacing for in excess of 30 minutes in each O.S. It survives suspend/resume.  Previously connections with this adapter haven't lasted longer than 10 minutes before simply stopping. The performance of this adapter seems not as good with the open driver as with the RealTek one.  Wavemon/iwconfig shows a connection speed of 72.5 mb/sec. compared to 135-150 mb./sec using Realtek's driver.  For my uses, I doubt I'll notice the difference.  The only problem I've noticed is the LED is on continuously rather than being off then flashing when transmitting or receiving.  I can live with that.

I wonder if this solution will work with other adapters exhibiting the same behavior. I feel the tiny/nano/micro/call-it-what-you-will adapters are a nice fairly inexpensive option for any machine but particularly for notebooks with failed or recalcitrant internal wifi adapters.  If this solution works for others as it does for me,  these little guys will be pretty close to plug 'n' play, just install one package.  It would be interesting to hear from others that have had the same problem after installing the "nss-myhostname" package.  I don't expect this will fix anything except the stops-responding-after-a-few-minutes problem but that's the only one I've had with this adapter.

---

