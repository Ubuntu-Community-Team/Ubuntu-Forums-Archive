---
title: "Intel Corporation PRO/Wireless 5100 AGN [Shiloh]/11.04 upgrade/HP Pavilion DV7-1034ca"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by CD2000 on 2011-05-03
Did an upgrade to Ubuntu 11.04. Since then, when I right-click the network icon, I can see : Wireless is disabled by hardware switch and the switch colour remains orange.

$ lspci -nn | grep 'Network controller'

02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



wlan0     IEEE 802.11abgn  ESSID:off/any  

          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   

          Retry  long limit:7   RTS thr:off   Fragment thr:off

          Power Management:off

$ uname -mr

2.6.38-8-generic x86_64

$ dmesg | grep iwlagn

[   25.719147] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:

[   25.719151] iwlagn: Copyright(c) 2003-2010 Intel Corporation

[   25.719238] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16

[   25.719247] iwlagn 0000:02:00.0: setting latency timer to 64

[   25.719279] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54

[   25.738477] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4

[   25.738479] iwlagn 0000:02:00.0: Device SKU: 0Xb

[   25.752383] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels

[   25.752465] iwlagn 0000:02:00.0: irq 50 for MSI/MSI-X

[   26.416520] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692

[   97.289287] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

[   98.114551] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

[ 1489.929374] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

[ 1490.436418] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

[ 1522.241742] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

[ 1523.746155] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

[ 1830.042489] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

[ 1830.570609] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

[ 1831.364749] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.

[ 1831.919999] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

When I right-click the network icon, I can see : Wireless is disabled by hardware switch and the switch colour remains orange and won't activate and turn blue.

Any help would be greatly appreciated.

Regards,
Dan

---

### Post by garvinrick4 on 2011-05-03
Try setting your router to g instead of n at the 2.4 ghz and set a 20 mhz see if that helps with the the iwlagn driver. I know it does not work with n very well at all. Looks like you got more troubles then that but sometimes we get lucky. After setting and saving if does not work then reboot once to make sure. Why SSID says off is a question. But looks like a nice card with abgn capabilitys. Give it a try.

---

### Post by CD2000 on 2011-05-03
Sorry if I wasn't very clear about my issue. The problem is that on my Notebook, the radio button won't turn on. It was working great prior to the upgrade. I need to know how to reactivate the wireless card at the hardware level.

Thank you.

Regards,
Dan

---

### Post by CD2000 on 2011-05-03
Hooray!! I did some updates and my wireless is now working, Thank You to the Powers that be...

Regards,
Dan

:guitar:

---

### Post by sprits2010 on 2011-06-16
hello,
tell me pls what update you did?

---

### Post by dyess002 on 2011-06-19
Same thing happened to me and I tried everything that I could think of but nothing, so I loged out of Buntu and logged into Win7, network worked fine, logged back into Buntu and it was working. I don't know what the chemistry was but it worked.

I even reinstalled Buntu and it didn't fix it.

---

### Post by wgilthorpe on 2011-06-21
Hey, hope this helps.  I ran into a similar problem.  The culprit in my case was rfkill try this:
 
```
rfkill list
```The output should look something like this:

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
10: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```If any of them is blocked, try:

```
rfkill unblock all
```This helped me on my machine.  After a round of updates my wireless quit working and the switch became inoperable.  It took a while on Google before I learned this little nugget.  After issuing the above command, the switch began working properly again.

---

### Post by chili555 on 2011-06-21
> **wgilthorpe said:**
> If any of them is blocked, try:

```
rfkill unblock all
```This helped me on my machine.  After a round of updates my wireless quit working and the switch became inoperable.  It took a while on Google before I learned this little nugget.  After issuing the above command, the switch began working properly again.You could make it persistent by editing /etc/rc.local to add it above exit 0.

---

### Post by mike_crossgreen on 2011-07-15
[FONT=Fixedsys]Wow yeah same! How random - booted into Win 7 then back to Ubuntu and all seems fixed?!?
Mine went down after i acciednetally pulled the cable out the back when the battery wasn't in, and it just wouldn't turn back on the hardware switch light after that.. but into 7 then back into Ubuntu and sorted?!

Great :)[/FONT]

---

### Post by smaring on 2011-10-27
I am running 11.10 on an HP Pavilion dv7.  Prior to the upgrade, I would experience the connection problems moments after the wifi was enabled, but I could fix it by bouncing the network services.  Now, that does not work.

I should also mention, as many with this problem have in common, that I only seem to have this problem when I connect to my Linksys WRT54GX with Firmware version 1.02.15.  At the moment, I am using the wifi capabilities of my cell phone, and it works fine.

Reloading the module with rmmod iwlagn and modprobe iwlagn does not work.

I've also tried playing with the "n" capabilities ...

rmmod iwlagn
modprobe iwlagn 11n_disable=0

I get the same momentary connection, followed by no response.  If I try to disable "n" like the following, I get the same thing.

rmmod iwlagn
modprobe iwlagn 11n_disable=1

although, that may not be disabling it correctly, because I still see the "n" in the rate algorithm in the logs after doing that:

ieee80211 phy4: Selected rate control algorithm 'iwl-agn-rs'

I also tried putting a file with "options iwlagn 11n_disable=1" into /etc/modules.d and that had no affect either.


# uname -an
Linux lappy 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


# dmesg | grep iwl
[259972.543129] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[259972.543131] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[259972.543238] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[259972.543282] iwlagn 0000:02:00.0: setting latency timer to 64
[259972.543353] iwlagn 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[259972.569319] iwlagn 0000:02:00.0: device EEPROM VER=0x11f, CALIB=0x4
[259972.569326] iwlagn 0000:02:00.0: Device SKU: 0Xb
[259972.569369] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[259972.569638] iwlagn 0000:02:00.0: irq 49 for MSI/MSI-X
[259972.633429] iwlagn 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692
[259980.416030] iwlagn 0000:02:00.0: Queue 2 stuck for 10000 ms.
[259980.416040] iwlagn 0000:02:00.0: On demand firmware reload


The "rfkill" solution does not seem to apply to me either.

# rfkill list
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
6: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no


[https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748](https://bugs.launchpad.net/ubuntu/maverick/+source/linux-firmware/+bug/630748)  seems to have some good notes


I would be willing to go out and spend some money on a new AP if I was 100% convinced that my problems would be solved.

---

### Post by varunendra on 2011-10-27
> **smaring said:**
> 
If I try to disable "n" like the following, I get the same thing.

rmmod iwlagn
modprobe iwlagn 11n_disable=1

although, that may not be disabling it correctly, because I still see the "n" in the rate algorithm in the logs after doing that
After rmmod, use lsmod to see if the module has actually been removed. If it still shows there, you may have to use -f option with rmmod (rmmod -f iwlagn).

---

### Post by smaring on 2011-10-29
after setting the disable option in /etc/modprobe.d I also did

# update-initramfs -u

and rebooted ... still no luck

---

### Post by smaring on 2011-10-29
and an iwconfig shows:

wlan0 IEEE 802.11abg

instead of

wlan0 IEEE 802.11abgn

so it is getting removed, only without a positive result

---

### Post by garvinrick4 on 2011-10-29
This will show you where you config file is to remove to get N speeds again
```
Locate iwlagn
```

/etc/modprob.d/iwlagn.conf
is usual path for that fix

---

### Post by garvinrick4 on 2011-10-29
What kernel you running:
```
uname -a
```

---

### Post by smaring on 2011-10-29
sounds like I have to downgrade my kernel to get this card to work:  [http://ubuntuforums.org/showpost.php?p=11371497&postcount=56](http://ubuntuforums.org/showpost.php?p=11371497&postcount=56)

---

### Post by smaring on 2011-10-30
# uname -a
Linux lappy 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


I downgraded my kernel to 2.6.32.x and tried it again.  It did not work with or without "N".

I then replaced "Network Manager" with "wicd", leaving the "N" capabilities in the card, AND IT WORKED!

I then booted back into the default kernel, tried "wicd" there, and it worked there too!

Obviously there is a difference in how NetworkManager and wicd treat this card.

BTW ... I noticed a HUGE difference in performance between the 2.6.32 and 3.0.0 kernels.  The 2.6.32 ran WAY faster!!!!

---

