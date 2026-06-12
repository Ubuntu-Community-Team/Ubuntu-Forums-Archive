---
title: "Please Help! Acer One - lspci not showing wireless, stopped working suddenly, broken?"
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2009-08-12
Hello guys.

I have an Acer Aspire One A150 (2 months), and i'm afraid because it was working flawlessly with Ubuntu 9.04 UNR (just the brightness feedback on screen wasn't working properly) and suddenly the wireless stopped working... i was connecting to my personal router and it (tha network manager) asked me the WPA password... which is strange because the password was saved and i didn't changed it... so i tried to re-enter it (i'v noticed that the password field showed a strange number that i never entered (somthin like 78sk9c1lo307...) and it tried to connect and asked me again... i re-entered again and -<ta-dam>- the wireless interface simply stopped working, as if it was switched off physically... not even lspci showed the thing... so i restarted, and the same thing... so i booted the latest puppy linux from USB, and it showed the interface on lspci (168c:001c), so i knew that the thing was "alive" then i rebooted on Ubuntu (which showed the interface again (lspci)) and tried to do some things that i thought should help(some i found searching on google):

thing that i did:

>using wicd instead of default network managgia
>iwlist wlan0 scan returns nothings
>tried sickboy and 2.31 kernels
>uninstalled backport modules
>there's no module ath_* so i did not blacklisted anythin' same for acer_wmi
>i'm using the ath5k module, it's the only wifi module installed on my system
>tried removing a lot of modules and loading ath5k a LOT of times

>I did not tried madwifi... should i?

After all the thing still unusable... the hardware is detected but the system don't show any wireless network, i'm at the work right now, and there are a LOT of wireless networks around, including 4 which has >90% of signal, about 20 that has >40% and a LOT others which has weak signal.

I'm dling Moblin to test, because it seems to work out-of-tha-box.

Now i have some questions:

Is it possible to be a hardware fault?
What do you think is worth trying?
Can you help me please :)?

Thank you very much for your time and sorry my bad english.

---

### Post by Repgahroll on 2009-08-12
OMG! After a reboot to take the battery off, the thing began to work again :)...

But now i need to know if such thing is gonna happen ocasionally... and if it's a hardware or software fault.

Thank you.

---

