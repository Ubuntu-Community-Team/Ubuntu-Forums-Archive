---
title: "Ubuntu 11.10 - &quot;Wireless is disabled by hardware switch&quot;?"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by BlueSunshine on 2012-05-20
My wireless has been working fine until about an hour or two ago. I have a dual-boot Compaq Presario A931NR, with Ubuntu 11.10 running fine on it. I've been using an Ethernet cable and it works as well as the router.
Help?!

---

### Post by raja.genupula on 2012-05-20
do you have hardware pin (switch)on your Lappy , then enable it.

else open BIOS settings and then look at there , the WIFI settings . Its set to OFF . Enable it and try again .

---

### Post by Replicounts on 2012-05-23
This worked for me (on Eee PC Seashell Series):

There's an odd key right above the ESC on this laptop's keyboard. It has an icon suggesting wireless broadcast just to the right of this special key. This key is only used for Windows so I didn't give it a thought. But finally it must have got pressed by accident today, the first time in a couple years that I've been using this computer a lot.

So I pressed the odd key, and the error message changed to say the wireless was disabled (but now, not mentioning the hardware switch). Then I could re-enable the wireless, using the standard wireless icon in the Ubuntu tool bar at the top of the page.

I had tried the simple terminal command:
sudo rfkill unblock all
before finding the switch. Of course it didn't work for me, since the switch was the problem. But possibly it was also necessary?

Of course on your laptop, that wireless on/off-switch might be somewhere else.

---

### Post by roelforg on 2012-05-23
My laptop has a weired thing with this that you might be experiencing as well:
If i switch the wireless off with the hw switch and reboot w/o reenabling, it get's caught in a "inbetween" state: HW=off and sw says it's on and gives error. Then i flick the switch and now i have this: HW=on and sw says the receiver is turned off.
rfkill outputs the states as i expect them so it's a bug in network manager.
I solved it by turning the wireless on with the hw switch (ignoring that network manager says it's off because rfkill says otherwise) and rebooting: Network manager resets to on and matches the hw state again and all is good again.

---

