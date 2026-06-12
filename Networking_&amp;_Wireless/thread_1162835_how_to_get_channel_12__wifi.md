---
title: "how to get channel 12 ?????? wifi ?????"
date: 2009-05-18
forum: Networking &amp; Wireless
---

### Post by jimmy.iceman on 2009-05-18
i bought this laptop from the US last month and when i came back to india i was not able to detect most of the wireless networks around after a while i found the reason to be that the wifi is using channel 12 or above...........

so i was wondering if there is any way for me to get the channel 12 and 13 on my laptop . i am using ubuntu 9.04

waiting for reply
peace

---

### Post by starcannon on 2009-05-18
usa wifi offers channels 1-11, not sure you can get 12+ without buying a localized wifi card; or perhaps flashing your current cards firmware.
> 
A variety of other devices use the wlan spectrum. Everything from microwave ovens to baby monitors. RF interference is a common issue for wifi networks and things like phones, etc. in shared areas. Every country has a different way of minimizing this, with the US disallowing anything over channel 11, which places like France and Spain allowing for channel 12 and 13, but not 14. My understanding is that various military installations, etc. use these restricted channels that are disallowed for civilian use. I'm not sure about the military usage, but I have first hand experience with serious RF interference due to full spectrum channel usage in Europe. 
Am guessing channels 12+ are disabled in the U.S. firmware in order to pass U.S. FCC inspections.

What model/brand/chipset?

---

### Post by jimmy.iceman on 2009-05-18
^^^^^
how do i flash my current card's firmware 
?????

---

### Post by starcannon on 2009-05-18
Heres a thread in another forum about this subject:
[http://www.velocityreviews.com/forums/t26433-intel-wifi-wont-go-to-channel-13-.html](http://www.velocityreviews.com/forums/t26433-intel-wifi-wont-go-to-channel-13-.html)

I think the easiest way is to buy a card locally, added benefit is the card will do all channels up to 13. Even better if you can get your hands on a Japan Localized card, it goes all the way to Channel 14.

GL and short of hacking your cards firmware, I'm not sure what else to tell you. Since I've never had to do this, I'm not sure how to direct you, especially without knowing the cards model/brand/chipset.

Perhaps someone else would have some advice?

---

### Post by starcannon on 2009-05-18
Looks like some cards can be enabled with a .dat file; as per this post:
[http://ubuntuforums.org/showthread.php?t=87274](http://ubuntuforums.org/showthread.php?t=87274)

You may be in luck as far as having a soft fix, not sure though, especially without knowing what wifi card your using.

---

### Post by jimmy.iceman on 2009-05-19
^^^^^
i dont think my wireless card support something like that in link mentioned above............
any other solutions guys ????

---

### Post by Aearenda on 2009-05-19
Try editing the file /etc/modprobe.d/options.conf (create it if it does not exist):
```
gksudo gedit /etc/modprobe.d/options.conf
```
Add the following line:```
options lbm_cw_cfg80211 ieee80211_regdom=XX
```Replace XX with your 2-letter country code - mine is AU for Australia.

I found this info somewhere a few weeks ago, but can't find it again now. Will edit with a link when I do.
EDIT: Try [this bug comment]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288401/comments/7")
You need to reboot or 'sudo service networking restart' (I think) to make it take effect.

EDIT2: Just found this in the 9.04 Release Notes:> Setting wireless regulatory domain via module option no longer supported

Ubuntu 9.04 enables the CRDA wireless regulatory framework for controlling which wireless channels are usable and visible in a particular location. If you previously had to use the module option similar to that below in /etc/modprobe.d/options to allow access to certain channels in your locality then you may find that wireless will not function at all:

    * options cfg80211 ieee80211_regdom=EU

You should remove this kernel module option on upgrade to Ubuntu 9.04 and use the iw reg command instead. 

I don't think 'iw' is installed by default. The module option I gave seems to work here still.

EDIT3: I just did some testing and found that the ath_pci driver I was using ignores all of these settings, whereas the ath5k driver observes both the options.conf and the 'iw set reg' command. So, your outcome will depend on what driver is in use!

If the iw command just says 'nl80211 not found' then the driver doesn't support changing regulatory domain this way.

---

