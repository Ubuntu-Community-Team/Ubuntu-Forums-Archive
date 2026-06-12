---
title: "Cheap dual dvb-t tuner"
date: 2008-09-09
forum: Mythbuntu
---

### Post by Hellfire29 on 2008-09-09
What's the cheapest dual dvb-t tuner available which is supported well by Mythtv? Whatever card you suggest, please be sure that it will run as I will be killed if I get a third non-functioning tuner. (I've now run out of Windows boxes to put them in.)

---

### Post by fibble on 2008-09-09
Hi,

I have done a lot of reading about this, and almost purchased the Nova-t-500 before deciding to go down the DVB-S route.

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

From the above article:

> 2008-06-16 - Today, using an up-to-date Ubuntu 8.04 x64, a recent V4L-DVB tree, the MythTV tuning and EIT settings and the provided remote receiver, this card is absolutely rock solid with no USB disconnects, no tuner lost or any other trouble. The few MythTV tweaks are an slight annoyance, but they are worth it. This card is a great DVB-T solution!

That URL seems to outline that the card is now supported, and pretty much stable with newer kernels and V4L.

I personally have a Nova-T single tuner card, and it has worked flawlessly for about 4 months now. Two of these could probably do the job for you too.

Take note of the warning on the above URL. There is an unsupported model, but its easily identfied as it has two aeirel inputs. So ask before buying!

Andy

---

### Post by SiHa on 2008-09-09
> **fibble said:**
> Hi,

I have done a lot of reading about this, and almost purchased the Nova-t-500 before deciding to go down the DVB-S route.

[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

From the above article:



That URL seems to outline that the card is now supported, and pretty much stable with newer kernels and V4L.

I personally have a Nova-T single tuner card, and it has worked flawlessly for about 4 months now. Two of these could probably do the job for you too.

Take note of the warning on the above URL. There is an unsupported model, but its easily identfied as it has two aeirel inputs. So ask before buying!

Andy

I'm running with a single tuner Nova-T, and a Nova-T 500, both work perfectly. There is only one tweak that is essential for the dual-tuner board and that is to enable the onboard LNA, see this thread: [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830)[/COLOR]

I've not bothered with the **'options usbcore autosuspend=-1'**, as I believe it's not needed with the latest kernels.

Note - this is with Ubuntu + Mythtv OOB - no new V4L or anything like that - far too complicated.

The -500's go for £30-£40 on eBay.

---

