---
title: "Serious wi-fi woes"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by sonicb00m on 2009-12-05
I have Ubuntu 9.10 installed and this problem is exhibited on both 32bit and 64 bit.

I have the following two wireless adapters that are green listed (which is why i bought them)

DLink DWA-140
Netgear WG111v2

Both of them display the network when plugged in but as soon as I try connecting to the network nothing happens.

I have tried WEP 64bit, WPA and no wireless security and not one of them works on either adapter.

Funnily enough, using WPA shows that it "connects" instantly but when i ping anything i Just get the "no route to network" message.

I have done clean installs and nothing is working.

Lastly, I have a DWA-160 which I tried installing with NDISGTK and that doesn't work either. 

I am sooooooooooo tired of wifi problems with Ubuntu.

For the record, I have a tvix 7000 which runs some Linux version and this runs my dwa-140 beautifully.


[ 9785.589865] wlan0: AP denied association (code=18)
[ 9785.590849] wlan0: RX AssocResp from 00:22:b0:80:f8:fe (capab=0xc31 status=18 aid=15216)
[ 9785.590853] wlan0: AP denied association (code=18)
[ 9785.590862] wlan0: RX AssocResp from 00:22:b0:80:f8:fe (capab=0xc31 status=18 aid=15216)
[ 9785.590866] wlan0: AP denied association (code=18)
[ 9785.590873] wlan0: RX AssocResp from 00:22:b0:80:f8:fe (capab=0xc31 status=18 aid=15216)
[ 9785.590876] wlan0: AP denied association (code=18)
[ 9785.591083] wlan0: RX AssocResp from 00:22:b0:80:f8:fe (capab=0xc31 status=18 aid=15216)
[ 9785.591087] wlan0: AP denied association (code=18)
[ 9785.780026] wlan0: association with AP 00:22:b0:80:f8:fe timed out

---

### Post by sonicb00m on 2009-12-07
I cannot get either of these two work on a clean install of OpenSuse 11.2 either.

Does anyone know whats going on? The adapters seem to be detected but just do not work.

I've tried taking off the security on the router but NO GO!

---

### Post by sonicb00m on 2009-12-08
Can anyone even confirm these problems? That would be a start.

---

### Post by teward on 2009-12-08
Usually stuff like this can happen if the devices you're using are incompatible with your hardware.  However, is it possible that network manager (or WICD, whichever you use) isn't functioning properly?

---

### Post by sonicb00m on 2009-12-09
I took the router out of N mode and made it b/g. What happens now is the authentication is working ok but still I am not able to ping anything. It just says "no route to host".

I insatlled wicd but the wan adapter is no longer found. So i put that gnome network manager back.

I thought that at least the wg111 usb would work since it's not N compatible but it exhibited the same behaviour. So no further forward.

It's got to be some kernel issue since the problem is on both suse 11.2 and Ubuntu 9.10

---

### Post by sonicb00m on 2009-12-22
back to the good old days, eh?

---

### Post by bkratz on 2009-12-22
> **sonicb00m said:**
> back to the good old days, eh?

You might want to check out this thread

[http://ubuntuforums.org/showthread.php?t=1333255](http://ubuntuforums.org/showthread.php?t=1333255)

---

### Post by sonicb00m on 2009-12-22
thanks for the pointer but I already discovered that thread before writing this one. Unfortunately, the black list option doesn't work.

In OpenSuse you can select which driver to test within its GUI and I can't get connected with any.

I think it's a kernel issue.....there's no distro I can find (with current-ish kernel builds at least) that are running the wifi correctly.

The problem is obvioulsy fixable because my TVIX 7000 unit (which runs some custom version of Linux) is working flawlessly with the wifi adapter (the DLINK). I bought the adapter because it said it ran without any known issues in the Ubuntu usb adapter list.

---

### Post by sonicb00m on 2010-01-19
install ubuntu backports kernel fixed it.

---

