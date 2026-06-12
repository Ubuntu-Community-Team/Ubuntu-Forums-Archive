---
title: "wireless is disabled by hardware switch"
date: 2012-09-15
forum: Networking &amp; Wireless
---

### Post by PersGiG on 2012-09-15
hi all 
it seems this is a common problem 
i have an evesham laptop which i installed ubuntu on it 
version is latest one 

yesterday i udated my software and after that i used the laptop for about 10 hours till i restarted 
after restart it shows wireless is disabled by hardware switch 
i have onboard wlan and also a usb one 
Both wireless adapters have same issue 
i checked all settings 
i also run the kill unblock command 
i also checked for soft or hard diseable
the usb one : soft is on and hard is off 
the main one both are are on 
but all options all grey wireless led is off i checked with recovery mode and it become on 
i did not touch any harware key that may cause such a problem 

i am sure it start after latest updates 
my system is not dual boot so i can not use windows 
the light on usb wlan is on but as i said al options are grey 

how can i fix this issue other than reinstalling ubuntu 
Regards

---

### Post by josephmills on 2012-09-15
> **PersGiG said:**
> hi all 
it seems this is a common problem 
i have an evesham laptop which i installed ubuntu on it 
version is latest one 

yesterday i udated my software and after that i used the laptop for about 10 hours till i restarted 
after restart it shows wireless is disabled by hardware switch 
i have onboard wlan and also a usb one 
Both wireless adapters have same issue 
i checked all settings 
i also run the kill unblock command 
i also checked for soft or hard diseable
the usb one : [COLOR="Red"]soft is on[/COLOR] and hard is off 
the main one both are are on 
but all options all grey wireless led is off i checked with recovery mode and it become on 
i did not touch any harware key that may cause such a problem 

i am sure it start after latest updates 
my system is not dual boot so i can not use windows 
the light on usb wlan is on but as i said al options are grey 

how can i fix this issue other than reinstalling ubuntu 
Regards

try this 

open terminal (ctrl+alt+t)
then enter 
```
rfkill unblock all 
```

---

### Post by PersGiG on 2012-09-16
hi thanks for reply as i said i did what ever i could find on net 

it shows hardware lock for usb wlan
for other one both soft and hard lock are on but all options are grey

---

### Post by PersGiG on 2012-09-16
Update:
i used wicd now 
i changed wlan0 to wlan1 and it is connected now 

but still the other one shows wireless are disabled by hardware switch 
also i changed wlan1 to wlan only in case to see if i can connect with usb interface but still no luck 
so now i know problem is the other networking manager 
question is how can i fix that one or at least how can i fix usb one to work with wicd

---

### Post by MC_Claus on 2012-09-16
I had a similar problem, with my laptop and hardware switch; 
If I accidently turn off the hardware switch when the computer was in standby the rfkill command gave me the same answer.

I can normally fix it, by setting the laptop in standby (close my screen) and turn the hardware switch to "on".
Afterwards, awake the computer (open the screen), and use the rfkill to unblock.

Hope it works...

---

### Post by PersGiG on 2012-09-16
thanks for answer i will try that 
Maybe onboard wifi hardware have this problem 
but i never heard a usb wifi adapter have laptop key to make them on and off 

also if there was such an issue how the usb one is working with wicd but not network manager 

by putting on sleep you mean hybernat ,suspend or lock screen

---

### Post by MC_Claus on 2012-09-16
Yes, standby aka suspend (at least in my reality:) )

---

### Post by PersGiG on 2012-09-16
> **MC_Claus said:**
> Yes, standby aka suspend (at least in my reality:) )

Seems you know what are you talking about 
LoL
Thanks a lot 
It worked but still dont know why the problem start 
Also why usb was also off and why they were working with WiCD 

Problem Resolved 
Once again thanks

---

### Post by MC_Claus on 2012-09-16
I haven't found a solution either (haven't done much searching really), but I have narrowed it down to happening, when I change the hardware switch to disable, or enable, network while the computer is suspended or hibernated.

Great it worked, after all, it is a rather easy workaround :)

---

