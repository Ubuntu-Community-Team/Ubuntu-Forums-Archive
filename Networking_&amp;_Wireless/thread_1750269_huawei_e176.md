---
title: "huawei e176"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by littlechay on 2011-05-05
I have a Huawei E176 3g modem USB stick. This worked without problem on my Acer aspire one netbook with my old Ubuntu installation 10 . something. Yesterday I installed the latest 11 and am having trouble getting the modem recognised. It shows under lusb. I've done a modprobe with the vendor and product and installed mode-switch. If I boot with the dongle plugged in it sometimes shows up in network manager but will not connect and eventually disappears from the menu. removing and replugging it doesn't seem to help.

I looked a wvdial but with all my ignorant efforts the best I can get from that is a no carrier effort.

Is there anything specific to 11 that I have missed?

Anybody else got this device to work. I doubt that it is a specific problem with this device but something more generic that I have missed. 

I'm currently in Uruguay and connecting to Movistar

Any pointers would be appreciated. 

Chris

---

### Post by alexfish on 2011-05-05
Not sure what you mean installed usb-modswitch, modeswitch may have been installed at default

not sure what the problem could be, can start disabling usb_modeswitch
as it may be possible the device is recognised by existing rules. open up a terminal then open up gedit with following command
```
sudo gedit /etc/usb_modeswitch.conf
```change Disable switching to
```
DisableSwitching=1
```save and exit

then connect the device, see what happens, if not recognised can post results of
```
nm-tool
``````
usb-device
```post only the info regarding the device

---

### Post by littlechay on 2011-05-05
Thanks for the response. It definitely needed modeswitch, but the problem was an embarrassing oversight on my part. I had used the modem the day before without problems but must have run it out of credit (it'a a prepaid account) . I tried the modem on my mac and found it was out of credit. Charged it up and all is good. Must have just been a total coincidence, as I thought there was plenty of credit on it. 

Cheers!

---

### Post by alexfish on 2011-05-05
Hi

mm! done that one my self.

notice you mention charge up on a mac ,

does your ISP have an on line facility , most do , this saves having to use alternate OS,

if not sure ask your ISP

---

### Post by littlechay on 2011-05-05
Yea you can charge up online.. sort of... you still need a scratch card. I used the Mac because it's my boat's main computer and I also knew that the modem was a worker on it.

---

