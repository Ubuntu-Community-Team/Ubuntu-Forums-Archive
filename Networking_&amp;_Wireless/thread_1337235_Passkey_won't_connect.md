---
title: "Passkey won't connect"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by Shawn2009 on 2009-11-25
Hello all,
 
Somewhat new to Ubuntu 8.xx thru to 9.10, limited use. (Meaning very little experience with terminal other than finger copying suggested commands/syntax) Have set it up on my desktop and a few laptops. The laptops just worked wirelessly with internal cards no problem. The desktop is another issue. I've tried two different USB dongles. DWA-130 and an Edimax 7718un. Used ndiswrapper to install the D-Link dongle. Got it working and it could find wireless routers within range. It asks for passkey entry but will not connect. Trying to access my router with all WEP and WPA-PSK settings offers the same results. Older Toshiba Satellite Laptop on windows XP with a legacy PCMIA card, Desktop on Vista with DWA-130, Desktop Win7 DWA-130 and ipod-touch all connect with no issues, same passkey of course. Searched online for something that might be more compatible and settled on an Edimax 7718un. Couldn't get it to work until I installed the final version of Ubuntu 9.10. (Couldn't find an appropriate .inf file on the CD for ndiswrapper). Ubuntu9.10 found it and powered it up. Exact same results as with DWA-130. I'm thinking if I get to the point whereas it asks for the passkey....it should just work. Shouldn't be dongle hardware since trying two different chip makers with similar results. Could it be a PC hardware issue? Desktop is a Dell Dimension about 4 years old. 
 
Thanks in advance.

---

### Post by bkratz on 2009-11-25
> **Shawn2009 said:**
> Hello all,
 
Somewhat new to Ubuntu 8.xx thru to 9.10, limited use. (Meaning very little experience with terminal other than finger copying suggested commands/syntax) Have set it up on my desktop and a few laptops. The laptops just worked wirelessly with internal cards no problem. The desktop is another issue. I've tried two different USB dongles. DWA-130 and an Edimax 7718un. Used ndiswrapper to install the D-Link dongle. Got it working and it could find wireless routers within range. It asks for passkey entry but will not connect. Trying to access my router with all WEP and WPA-PSK settings offers the same results. Older Toshiba Satellite Laptop on windows XP with a legacy PCMIA card, Desktop on Vista with DWA-130, Desktop Win7 DWA-130 and ipod-touch all connect with no issues, same passkey of course. Searched online for something that might be more compatible and settled on an Edimax 7718un. Couldn't get it to work until I installed the final version of Ubuntu 9.10. (Couldn't find an appropriate .inf file on the CD for ndiswrapper). Ubuntu9.10 found it and powered it up. Exact same results as with DWA-130. I'm thinking if I get to the point whereas it asks for the passkey....it should just work. Shouldn't be dongle hardware since trying two different chip makers with similar results. Could it be a PC hardware issue? Desktop is a Dell Dimension about 4 years old. 
 
Thanks in advance.

I have been using the DWA-130 version A since 8.10 (9.04, 9.10) and have never gotten it to work with WEP. Only open or WPA/WPA-2).  When getting to 9.10-- encryption with ndiswrapper has a bug. See
[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

I'm waiting for resolution. Are you using ndiswrapper for both of them ( I didn't totally understand)? If you check dmesg in the terminal and see a lot of "invalid cmd 12" 's you are seeing it too.

---

### Post by Shawn2009 on 2010-01-05
Not sure if you're still monitoring this forum. I had to leave town for work shortly after my post so haven't had a chance to get back to this. Sorry for the tardy reply and certainly appreciate yours. Will reply with something a little more substantial on my return.
 
Cheers
Shawn

---

### Post by mehta on 2010-01-05
Looks like I am not the only one having this problem.  In my case, a usb adapter worked just fine with both a laptop and PC with 9.04 but on upgrade to 9.10 it has stoped working with the desktop but works with the laptop.
The networks are detected and connection attempted but thereafter the network manager keeps asking for authentication password.
I also found that I was not able to ping the router from the desktop.  This seems to indicate a compatibility issue with old hardware.  Hoping that an expert will respond.

---

