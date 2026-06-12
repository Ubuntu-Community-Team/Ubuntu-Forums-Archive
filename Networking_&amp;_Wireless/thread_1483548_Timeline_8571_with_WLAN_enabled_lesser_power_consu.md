---
title: "Timeline 8571: with WLAN enabled lesser power consumption as without"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by stefan-koch on 2010-05-14
Hello,

I have an Acer Timeline 8571 laptop with ubuntu 9.10 amd64 and Win7 installed.

On Windows the battery life comes up to 11 h, on Linux to 7-8 h (WLAN disabled, smallest display backlight)

NOTE at battery life: I have used different BIOS Versions. The laptop was shipped with V1.02 then I flashed 1.33 than I downgraded to V1.02 (becaus there the fan is quiter (v1.02) - disadvantage: CPU minimum clock at 1200 MHZ (v1.02) instead of 800 MHZ (v1.33))

Now, I have installed an backport WLAN driver, this driver can save more battery life. (If you enable WLAN, it's needs not the full power rate)
And I have recogniced that the power consumption with WLAN connection is lesser than without WLAN connection. (The battery life tests, are made without the backport WLAN driver - with disabled WLAN)

Now, there the test results:

Enable all power-settings with powertop, additional to these settings make this:

iwconfig wlan0 txpower off
iwconfig wlan0 power on

power consumption:        MIN-
txpower on, power on:        7,4-9,0 W (9,0 W seldom; WLAN connectet 5 meters away from the router)
power on, txpower off:        8,2-9,0 W

txpower off, power on, WLAN button on the laptop disabled : 8,2-8,8 W

I think, when the power consumption with WLAN is lesser than without, something went wrong.

What's to do, that the power consumption without WLAN is at 6,5 - 7 W?

Thanks.

Best regards

Stefan Koch

---

### Post by stefan-koch on 2010-05-17
I rebooted from win7 into ubuntu have opened an terminal:
sudo su
modprobe coretemp
sensors

The CPU-Temp was 41 °C,
now after 10-15 Min. in Linux the temp is at 40° C but the laptop is a lot warmer than in win7?

Is that the WLAN chip?

---

### Post by stefan-koch on 2010-05-17
-

---

### Post by stefan-koch on 2010-07-26
One or two weeks ago, I have unplug the wireless controller card. 
powertop says then 7,2 W - 7,3 W.

Is there no option to disable the chip by software?

---

### Post by stefan-koch on 2010-09-09
At first in ubuntu 10.10 alpha xyz I could switch off the wlan card:
I think that was with the "iwconfig wlan0 txpower off" command then the power consumtion was < 7,5 Watts, I think. BIOS: V 1.02

---

