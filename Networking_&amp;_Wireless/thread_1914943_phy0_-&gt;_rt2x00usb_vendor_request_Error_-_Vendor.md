---
title: "phy0 -&gt; rt2x00usb_vendor_request: Error - Vendor Request"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by speigel205 on 2012-01-25
Hello

I have been for one month a go with a problem that puled my hear for hours and couldn't find a solution to it, I made tons of Googling for that issue and with no luck at all, the seem problem return again and again randomly. The problem didn't seem to be related to the USB driver itself but a kernel bug maybe in the udev according to what i have read online in some related topics about that issue.

I am running both Ubuntu 11.04 & 11.10, a USB adapter with chipset rt3070. I succeded to compile and install both driver rt2800usb from one side and the rt5370sta from an other side. To run one of them I just blacklist the other one and then modprobe xxx ... yesterday I was able to browse the net with the rt2800usb normally, but suddenly after reboot when I plug the usb adapter I get this message saying :

```
[ 281.688657] phy0-> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x0580 with error -71

[175:215603] usb 2-1.1 : string descriptor 0 read error : -75
... device descriptor read/64, error -110
```

The message is getting repeating in dmesg for many times, I didn't succeed to make the usb adapter work until now, always show me this error message, I tried switching to rt5370sta but no luck, tried to update the firmware and whatever I do I don't succeed at all, searched the net I have seen people setting hung_task_timeout_secs to 0, I did that reboot but nothing happing seem message always appear, I don't see anymore wlan0 or ra0 when tipping ifconfig, this command break many times as well and the system console refuse to respond when I plug the usb wireless so I was forced to open a new terminal tab ... really frustrating problem.

So if someone knows kindly tell me what should I do to solve it.

Regards

---

### Post by speigel205 on 2012-01-25
up :)

---

